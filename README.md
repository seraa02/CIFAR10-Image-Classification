Image Classification on CIFAR-10
Exploring CNN, ResNet-18 + SVM, and ResNet-34

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-orange.svg)](https://pytorch.org)
[![Live Demo](https://img.shields.io/badge/Website-Live-brightgreen)](https://ecencifar10project.netlify.app/)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1aQ69T-Q3BfMhu1ZyM2xCXGJo2AswAZHU)

 📌 Project Overview

This project explores image classification on the **CIFAR-10 dataset** — 60,000 color images across 10 classes (airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck). We benchmarked three progressively deeper approaches to understand the trade-offs between model complexity, accuracy, and generalization.

The core question: *how much does architecture choice actually matter for a well-known benchmark?*

Turns out — a lot. We went from **75% → 86% → 95%** accuracy just by rethinking the approach.

Results at a Glance

| Model | Test Accuracy | Key Strength |
|---|---|---|
| Baseline CNN | 75% | Simple, fast, interpretable |
| ResNet-18 + SVM | 86% | Best of both worlds — deep features + SVM classifier |
| ResNet-34 | **95%** | Deepest network, best generalization |

🧠 Approaches

1. Baseline CNN
A custom CNN with convolutional layers, max pooling, ReLU activations, and fully connected layers. Trained with SGD and cross-entropy loss. Good starting point — showed clear overfitting when layers were added naively.

2. ResNet-18 + SVM Hybrid
Used a pretrained ResNet-18 purely for **feature extraction**, then fed those features into a Support Vector Machine (SVM) with an RBF kernel for classification. Hyperparameters (C, gamma) were tuned using randomized cross-validation. This combo hit 86% on test — the hybrid approach really paid off.

3. ResNet-34
Full end-to-end deep network with skip connections to handle vanishing gradients. Tuned learning rate and momentum across multiple values. Best result: **95% accuracy** at lr=0.01, momentum=0.2.

📊 Data & Preprocessing

- **Dataset:** CIFAR-10 (50,000 train / 10,000 test, 32×32 RGB images)
- Augmentations: random rotation (±20°), horizontal flips, color jitter (brightness, contrast, saturation), random erasing (75% probability)
- Normalization based on training set mean and std
- PCA analysis showed 3 components only captured 47% variance → kept original resolution

 Tech Stack

- **Python 3.8+**
- **PyTorch** — model training and architecture
- **torchvision** — pretrained ResNet models and transforms
- **scikit-learn** — SVM, cross-validation, metrics
- **matplotlib / seaborn** — visualization
- **Google Colab** — training environment (GPU)


🌐 Website

Project writeup and visualizations are also hosted at:
**[ecencifar10project.netlify.app](https://ecencifar10project.netlify.app/)**


👥 Team

Ankita Aswathanarayana · Hayley Hawkins · Harsha Rapuru · **Saher Thekedar** · Prachi Dudhe


