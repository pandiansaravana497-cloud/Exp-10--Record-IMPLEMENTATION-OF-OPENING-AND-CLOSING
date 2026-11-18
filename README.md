# Opening and Closing Operations Using OpenCV

## Aim

To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

The program performs the following operations:

- Morphological Opening
- Morphological Closing

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Create or load an input image containing foreground objects.

### Step 3:

Display the original image.

### Step 4:

Create a structuring element (kernel) of suitable size.

### Step 5: Opening Operation

- Apply the Opening operation using the structuring element.
- Opening consists of Erosion followed by Dilation.
- Remove small foreground noises while preserving the shape of larger objects.
- Display the opened image.

### Step 6: Closing Operation

- Apply the Closing operation using the structuring element.
- Closing consists of Dilation followed by Erosion.
- Fill small holes and gaps within foreground objects.
- Display the closed image.

### Step 7:

Compare the original, opened, and closed images.

## Program
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the input image
image_path = r"C:\Users\acer\OneDrive\Pictures\Camera Roll\road.jpg"
img = cv2.imread(image_path)

# Check whether image is loaded
if img is None:
    print("Error: Image not found!")
else:
    # Convert BGR to RGB
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Step 2: Display original image
    plt.figure(figsize=(5, 5))
    plt.imshow(img_rgb)
    plt.title("Original Image")
    plt.axis("off")
    plt.show()

    # Step 3: Convert image to grayscale
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    # Step 4: Apply binary thresholding
    _, binary = cv2.threshold(
        gray, 127, 255, cv2.THRESH_BINARY
    )

    # Step 5: Create structuring element
    kernel = np.ones((5, 5), np.uint8)

    # Step 6: Opening operation (Erosion + Dilation)
    opening = cv2.morphologyEx(
        binary, cv2.MORPH_OPEN, kernel
    )

    # Step 7: Closing operation (Dilation + Erosion)
    closing = cv2.morphologyEx(
        binary, cv2.MORPH_CLOSE, kernel
    )

    # Step 8: Display all results
    titles = [
        "Original Image",
        "Binary Image",
        "Opening Operation",
        "Closing Operation"
    ]

    images = [
        img_rgb,
        binary,
        opening,
        closing
    ]

    plt.figure(figsize=(12, 8))

    for i in range(4):
        plt.subplot(2, 2, i + 1)
        if i == 0:
            plt.imshow(images[i])
        else:
            plt.imshow(images[i], cmap="gray")

        plt.title(titles[i])
        plt.axis("off")

    plt.tight_layout()
    plt.show()

```

## Developed By

**Name: PON SARAVANA PANDIAN B**

**Register No: 212225230207** 

## Output

<img width="511" height="341" alt="image" src="https://github.com/user-attachments/assets/8c2dfa54-3243-4af1-99da-60984cb04484" />

<img width="1387" height="446" alt="image" src="https://github.com/user-attachments/assets/30a69ce1-9498-465b-a6c5-9cb79cfa6eae" />

<img width="1360" height="501" alt="image" src="https://github.com/user-attachments/assets/43102245-c606-452f-a2f9-1d17dca7f6d0" />


### Original Image

- The input image is displayed.
- The image serves as the source for morphological processing.

### Opening Operation

- Original image is displayed.
- Opened image is displayed.
- Small foreground noise is removed.
- Thin protrusions and isolated pixels are eliminated.
- Object boundaries become smoother.

### Closing Operation

- Original image is displayed.
- Closed image is displayed.
- Small holes and gaps inside objects are filled.
- Broken regions are connected.
- Object boundaries become more continuous.

## Applications

### Opening

- Noise removal in binary images.
- Separation of connected objects.
- Preprocessing for object detection.

### Closing

- Filling small holes in objects.
- Connecting nearby components.
- Enhancing segmented regions.

## Advantages

### Opening

- Removes unwanted foreground noise.
- Preserves major object structures.
- Improves segmentation quality.

### Closing

- Restores object continuity.
- Eliminates small background gaps.
- Improves object representation.

## Result

Thus, the morphological operations **Opening** and **Closing** are successfully implemented using OpenCV. 
