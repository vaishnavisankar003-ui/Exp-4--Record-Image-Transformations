# Exp-4--Record-Image-Transformations
# IMAGE-TRANSFORMATIONS

## Aim

To perform image transformations such as Translation, Scaling, Shearing, Reflection, Rotation, and Cropping using OpenCV and Python.

## Software Required

- Anaconda - Python 3.7
- OpenCV
- NumPy
- Matplotlib

## Algorithm

### Step 1
Import all the necessary modules.

### Step 2
Choose an image and save it as `filename.jpg` or `bird.png`.

### Step 3
Use `cv2.imread()` to read the image.

### Step 4
Use `cv2.warpPerspective(image, M, (cols, rows))` to translate the image.

### Step 5
Use `cv2.warpPerspective(image, M, (cols2, rows2))` to scale the image.

### Step 6
Apply shearing, reflection, and rotation by defining the appropriate transformation matrices.

### Step 7
Crop a specific region of the image and save the cropped image.

## Program

**Developed By:** VAIHSNAVI S

**Register Number:** 212225230289


## i) Image Translation

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 1: Load the image
image = cv2.imread('vaishu.jpeg')  # Load the image from file

# Display the original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert BGR to RGB for correct display
plt.title("Original Image")  
plt.axis('off')

# Step 2: Image Translation
tx, ty = 100, 50  # Translation factors (shift by 100 pixels horizontally and 50 vertically)
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  # Translation matrix: 
# [1, 0, tx] - Horizontal shift by tx
# [0, 1, ty] - Vertical shift by ty
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  # Display the translated image
plt.title("Translated Image")  
plt.axis('off')
```

## ii) Image Scaling

```python
# Step 3: Image Scaling
fx, fy = 5.0, 2.0  # Scaling factors (1.5x scaling for both width and height)
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
# resize: Resize the image by scaling factors fx, fy
# INTER_LINEAR: Uses bilinear interpolation for resizing

plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')
```

## iii) Image Shearing

```python
# Step 4: Image Shearing
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')
```

## iv) Image Reflection

```python
# Step 5: Image Reflection
reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
# flip: 1 means horizontal flip, 0 would be vertical flip, -1 would flip both axes

plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')
```

## v) Image Rotation

```python
# Step 6: Image Rotation
(height, width) = image.shape[:2]  # Get the image height and width
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2)  # Set the center of rotation to the image center
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  # Get the rotation matrix
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  # Apply rotation

plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')
```

## vi) Image Cropping

```python
# Step 7: Image Cropping
x, y, w, h = 100, 100, 200, 150  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
# Cropping the image from coordinates (x, y) to (x+w, y+h)
cropped_image = image[y:y+h, x:x+w]
# The crop is performed by slicing the image array in the y and x directions

plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')
```

## Output
### i) Input Iamge

<img width="280" height="407" alt="Screenshot 2026-10-31 101724" src="https://github.com/user-attachments/assets/6f17e4f7-ca8d-41d0-b2a6-5afcb2b3728e" />


### ii) Image Translation


<img width="283" height="398" alt="Screenshot 2026-10-31 101808" src="https://github.com/user-attachments/assets/bfd4e775-433d-4d35-b5c2-283311a90c3c" />


### iii) Image Scaling

<img width="522" height="385" alt="Screenshot 2026-10-31 101832" src="https://github.com/user-attachments/assets/6f4fd0ea-ae28-42d9-a3d1-63f37eddb72d" />


### iv) Image Shearing

<img width="297" height="406" alt="Screenshot 2026-10-31 101845" src="https://github.com/user-attachments/assets/6baf0e87-d1ac-4c54-9772-4e48aeb30587" />


### v) Image Reflection

<img width="256" height="407" alt="Screenshot 2026-10-31 101853" src="https://github.com/user-attachments/assets/8e58f2f7-9f5d-4925-af07-4795e21d6ce7" />


### vi) Image Rotation

<img width="287" height="397" alt="Screenshot 2026-10-31 101903" src="https://github.com/user-attachments/assets/71b7ea3b-618c-4ca1-b080-d6dbcc8021f4" />


### vii) Image Cropping

<img width="507" height="397" alt="Screenshot 2026-10-31 101917" src="https://github.com/user-attachments/assets/a6082f64-4cf5-436f-9ae2-0cb31e9bc4ea" />


## Result

Thus, different image transformations such as Translation, Scaling, Shearing, Reflection, Rotation, and Cropping were performed using OpenCV and Python programming.
