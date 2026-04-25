

The project is based on computer vision. Bluetooth was used for wireless communication between the PC and the microcontroller installed on the car.

The goal of the project was to park a randomly placed car in a specific parking spot. To achieve this, concepts such as computer vision, pixel mapping, and image processing were studied in order to recognize a square marked on the floor and determine each spot within the square as coordinates with respect to the corners of the square.

Concepts of object detection were also studied, including contour detection, Gaussian blur, kernel size, and grayscale processing. Additionally, perspective transformation and warp transformation were explored to obtain a bird's-eye view of the area.

During this process, ArUco markers were introduced. The computer could detect these markers and determine the pixel locations of the markers' corners, storing them in an array in a specific order for each marker ID.

This capability was utilized for the project because pixel coordinates were required as the source points in the warpPerspective transformation function in the OpenCV library. The destination points were defined as (0,0), (480,0), (0,480), and (480,480), since the square area was 4 ft × 4 ft.

A fifth ArUco marker was attached diagonally on the car so that, in the bird's-eye view, the bottom corner coordinates could be subtracted from the top corner coordinates to obtain the vector representing the direction in which the car is facing:

(x₁ − x₂, y₁ − y₂)

The top corner was assigned as the coordinate of the car, as the car would rotate about an axis passing through this point.

Since both the direction coordinates and the position coordinates of the car were now available, along with the destination coordinates, the car could be guided to the destination using a simple algorithm.

While designing the algorithm and writing the code, tolerance levels and motor RPM had to be considered, as they needed to be optimal due to the time difference between the video feed and Bluetooth transmission.
