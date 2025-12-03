# Image Segmentation Using K-Means & PCA – README

This project demonstrates how to perform **image segmentation** and **dimensionality reduction** using:

* **K-Means Clustering** (for color-based segmentation)
* **PCA (Principal Component Analysis)** (for image compression)

The notebook includes functions for reading images, reshaping pixel data, finding optimal clusters, applying segmentation, saving results, and reconstructing images using PCA.

---

## 📌 **Project Overview**

This notebook covers:

* Loading and visualizing RGB images
* Reshaping image pixels into a dataset suitable for clustering
* Using the **Elbow Method** to pick optimal number of clusters
* Applying **K-Means** to segment images by color similarity
* Reconstructing compressed images using **PCA**
* Saving segmented images to disk

---

## 🧭 **Workflow Summary**

### 1. **Import Required Libraries**

Includes Scikit-Learn, NumPy, Matplotlib, Seaborn, PCA modules, and PIL for saving image files.

---

## 🖼️ **Image Loading & Display**

Function:

```python
def load_and_show_image(image_path):
    image = mplt.image.imread(image_path)
    ...
```

This prints image shape, pixel size, and displays the original image.

---

## 🔄 **Reshape Image for Clustering**

Images must be reshaped into **(num_pixels, 3)** before clustering.

Function:

```python
def reshape_image_for_clustering(image):
    X = image.reshape(-1, 3)
```

This prepares pixel colors (RGB) as dataset rows.

---

## 📉 **Elbow Method to Find Optimal k**

Function:

```python
def find_optimal_clusters(X, max_clusters=10):
    ...
```

The function:

* Runs K-Means for k = 1 to `max_clusters`
* Stores **WCSS (Within-Cluster Sum of Squares)**
* Plots an elbow curve to help choose the best value of k

---

## 🎨 **Apply K-Means Image Segmentation**

Function:

```python
def apply_kmeans_segmentation(X, image, n_clusters=3):
    ...
```

This:

* Clusters pixels into k color groups
* Replaces each pixel with its cluster's centroid color
* Reshapes it back to the original image dimensions
* Displays the segmented image

This produces a simplified, abstract version of the image.

---

## 💾 **Save Segmented Image**

Function:

```python
def save_segmented_image(image_Seg, output_path='segmented_image.jpg'):
    ...
```

This stores the segmented/clustering output as a JPEG file.

---

## 🧠 **PCA-Based Image Compression**

Function:

```python
def apply_pca(X, image, n_components=2):
    ...
```

Steps:

* PCA reduces pixel dimensions from 3 → `n_components`
* The image is reconstructed using inverse transform
* Original and compressed images are displayed side-by-side

This demonstrates how PCA reduces noise and smoothens an image.

---

## 🖥️ **Main Execution Flow**

Example:

```python
image_path = 'diver.jpg'
image = load_and_show_image(image_path)
X = reshape_image_for_clustering(image)
find_optimal_clusters(X)
segmented_image = apply_kmeans_segmentation(X, image, n_clusters=3)
save_segmented_image(segmented_image, 'segmented_diver.jpg')
pca_reconstructed_image = apply_pca(X, image, n_components=2)
```

---

## 🎯 **Goals of the Project**

* Understand **color clustering** using K-Means
* Learn how to reshape image data for ML algorithms
* Apply the **Elbow Method** to find optimal clusters
* Explore **PCA** for image compression & reconstruction
* Create reusable modular functions for image processing

---

## ⚙️ **Technologies Used**

* Python 3
* NumPy
* Matplotlib
* Scikit-Learn (KMeans, PCA)
* PIL (for saving images)

---

## 🚀 **How to Run This Notebook**

1. Install required libraries:

   ```bash
   pip install numpy matplotlib seaborn scikit-learn pillow
   ```
2. Place your image (e.g., `diver.jpg`) in the working directory.
3. Run the notebook sequentially.
4. Adjust `n_clusters` or `n_components` for experimentation.

---

## ✨ **Author**

This project demonstrates unsupervised learning for image processing using clustering and PCA.

---

If you'd like, I can also:

* Add silhouette score evaluation
* Add comparison with hierarchical clustering
* Generate a combined notebook README portfolio
