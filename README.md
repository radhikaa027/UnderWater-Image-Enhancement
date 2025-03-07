# Underwater Image Enhancement: A Comparative Analysis

This repository contains code and experiments related to underwater image enhancement. The project presents a comparative study of classical methods (including average-based and PCA-based fusion) and deep learning approaches (GAN, DCGAN, and CycleGAN) for improving the quality of underwater images.

---

## Table of Contents

- [Overview](#overview)
- [Motivation and Background](#motivation-and-background)
- [Methods Implemented](#methods-implemented)
  - [Classical Approaches](#classical-approaches)
  - [Deep Learning Approaches](#deep-learning-approaches)
- [Dataset](#dataset)
- [Results and Discussion](#results-and-discussion)
- [Installation and Usage](#installation-and-usage)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

Underwater imaging faces unique challenges due to light absorption, scattering, and color distortion caused by the aquatic environment. This project explores several methods to enhance underwater images for applications such as marine biology, environmental monitoring, and underwater exploration.

The repository includes:
- **Classical methods:** Average-based fusion and PCA-based fusion that use color correction and global histogram equalization.
- **Deep learning methods:** Implementation of GAN, DCGAN, and CycleGAN architectures, designed to learn the mapping from degraded underwater images to enhanced ones.

---

## Motivation and Background

Underwater images are often characterized by low contrast, color distortions (usually bluish or greenish tones), and poor visibility due to the inherent properties of the water medium. Enhancing these images is critical for tasks like object detection, marine habitat mapping, and underwater surveillance.

The project builds on the insights provided in the attached paper, which compares traditional fusion-based techniques with modern deep learning frameworks. The study includes:
- Addressing light absorption and scattering issues.
- Improving structural similarity (SSIM), perceptual quality (UIQM), and other key metrics.
- Demonstrating that while classical methods are computationally efficient, advanced deep learning models (especially CycleGAN) offer more robust performance in complex underwater conditions.

---

## Methods Implemented

### Classical Approaches

1. **Color Correction and White Balancing:**  
   - Adjusting individual color channels using compensation equations.
   - Applying the Gray World algorithm for white balancing.

2. **Contrast Enhancement:**  
   - Converting images to the HSV color space and equalizing the V component.
   - Using unsharp masking to sharpen the images.

3. **Fusion Techniques:**  
   - **Average-based Fusion:** Simple pixel-wise averaging of processed images.
   - **PCA-based Fusion:** Utilizing eigenvalue decomposition to fuse images, thereby preserving important features.
   
   These methods provide a fast and efficient solution for enhancing underwater images, although they may struggle with adaptability under varying conditions.

### Deep Learning Approaches

1. **GAN (Generative Adversarial Network):**  
   - A basic GAN architecture to learn the mapping from degraded to enhanced images.
   
2. **DCGAN (Deep Convolutional GAN):**  
   - Improved performance in terms of Mean Squared Error (MSE) and Peak Signal-to-Noise Ratio (PSNR), though structural similarity (SSIM) can be lacking.

3. **CycleGAN:**  
   - Utilizes unpaired image-to-image translation with cycle-consistency loss.
   - Demonstrated the best overall performance in balancing color correction, contrast, and structural fidelity.
   - Experimented with various training epochs (100, 200, 300, and 350) to determine optimal performance settings.

---

## Dataset

The experiments in this project use the **UIEB dataset** – a collection of raw underwater images paired with reference images. The UIEB dataset is essential for both classical and deep learning experiments.

**How to obtain the dataset:**
- Visit the benchmark page at [https://li-chongyi.github.io/proj_benchmark.html](https://li-chongyi.github.io/proj_benchmark.html) for details on the dataset.
- Follow the instructions on the website to download the dataset. The UIEB dataset includes images captured under various underwater conditions and is used for both training and evaluation in this project.

---

## Results and Discussion

The project evaluates each method using several metrics:
- **MSE (Mean Squared Error)**
- **PSNR (Peak Signal-to-Noise Ratio)**
- **SSIM (Structural Similarity)**
- **UIQM (Underwater Image Quality Measure)**
- **FID (Fréchet Inception Distance) [for GAN-based methods]**

### Key Findings:
- **Classical Methods:**  
  Average fusion slightly outperformed PCA fusion in terms of SSIM and UIQM, offering visually pleasing and perceptually consistent results.
  
- **Deep Learning Methods:**  
  - Basic GAN showed suboptimal performance.
  - DCGAN improved MSE and PSNR but had low SSIM.
  - CycleGAN (especially with 300 epochs at a 0.0001 learning rate) achieved the best balance across all metrics, suggesting its superior ability to handle underwater distortions.

---

## Installation and Usage

### Prerequisites

- Python 3.7 or later
- [PyTorch](https://pytorch.org/) (for deep learning modules)
- OpenCV, NumPy, and other common Python libraries

### Installation Steps

1. **Clone the repository:**

   ```bash
   git clone https://github.com/yourusername/underwater-image-enhancement.git
   cd underwater-image-enhancement
   ```

2. **Create and activate a virtual environment:**

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install the required packages:**

   ```bash
   pip install -r requirements.txt
   ```

### Running the Code

- **Classical Methods:**  
  Navigate to the `classical_methods` directory and run the appropriate Python scripts to test color correction, histogram equalization, and fusion methods.
  
- **Deep Learning Approaches:**  
  Each subfolder (GAN, DCGAN, CycleGAN) includes a training script. For example, to train the CycleGAN model:

  ```bash
  cd deep_learning/CycleGAN
  python train_cyclegan.py --epochs 300 --learning_rate 0.0001
  ```

- **Dataset Preparation:**  
  Follow the instructions in the `dataset/download_instructions.md` file to download and organize the UIEB dataset.

---

## Contributing

Contributions, issues, and feature requests are welcome!  
Feel free to check [Issues](https://github.com/yourusername/underwater-image-enhancement/issues) or submit a pull request.

---

## License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.

---

*Happy Enhancing!*
