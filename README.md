# Seam Carving for Content-Aware Image Resizing

This project is a Python implementation of the seam carving algorithm, a technique for content-aware image resizing. Instead of uniformly scaling an image, this method intelligently finds and removes the least "interesting" paths of pixels, known as seams, to reduce the image's dimensions while preserving important features.



---

## How It Works

The algorithm operates in a series of steps to intelligently resize an image:

1.  **Energy Calculation**: An "energy map" of the image is generated. Each pixel is assigned an energy value based on its contrast with neighboring pixels, typically calculated using image gradients. High-energy pixels represent edges and details, while low-energy pixels represent smooth areas.
2.  **Cumulative Energy Map**: Using dynamic programming, a cumulative minimum energy map is computed. Each cell in this map stores the total minimum energy of a connected path (a seam) from the first row/column to that specific pixel.
3.  **Seam Identification**: The optimal seam is identified by finding the pixel with the lowest cumulative energy in the last row (for vertical seams) or column (for horizontal seams) and then backtracking to find the lowest-energy path to the top/start.
4.  **Seam Removal**: The pixels along this optimal seam are removed, effectively reducing the image's width or height by one pixel.
5.  **Iteration**: The process is repeated, recalculating the energy for the new image each time, until the desired dimensions are reached.

---

## Features

* **Energy Map Generation**: Calculates pixel energy using both simple gradients and a more robust Sobel operator.
* **Vertical & Horizontal Seam Carving**: Capable of reducing both the width and height of an image.
* **Seam Visualization**: Includes functionality to display the identified optimal seam overlaid on the image.
* **Comparative Analysis**: The script demonstrates resizing on various images and compares the seam-carved result against standard `cv2.resize`.

---

## Dependencies & Installation

This project requires Python 3 and the following libraries:

* **OpenCV**: For image processing tasks (`cv2`).
* **NumPy**: For numerical operations and array manipulation.
* **Matplotlib**: For displaying images and plots.

You can install the necessary packages using pip:

```bash
pip install opencv-python numpy matplotlib
