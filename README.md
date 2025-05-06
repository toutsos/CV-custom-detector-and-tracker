# Computer Vision Custom Detector and Tracker

This repository provides a **complete pipeline** for custom object detection and tracking using a combination of manual annotation, YOLOv8-based detection, and KCF tracking. It includes tools to **train your own YOLO models**, **run inference**, and **track objects** across video frames.

---

## Features

- **Manual Annotation Tool**: Annotate frames for training or evaluation.
- **YOLOv8 Integration**: Train and fine-tune custom object detectors using Ultralytics' YOLOv8.
- **KCF Tracking**: Track detected objects using Kernelized Correlation Filters.
- **Fallback Detection**: Automatic YOLO detection when tracking fails.
- **Evaluation**: Compare manual vs. tracked annotations.
- **Visualization & Outputs**: Save annotated videos and export bounding boxes to CSV.

---

## Project Structure

| File                    | Description                                                              |
| ----------------------- | ------------------------------------------------------------------------ |
| `object_tracking.ipynb` | Pipeline for manual annotation, KCF tracking, YOLO fallback + comparison |
| `train_models.ipynb`    | Script to train YOLOv8 models with Roboflow datasets                     |
| `yolo_inference.ipynb`  | Inference on images/videos using trained YOLO models                     |

---

## 🔧 Installation

1️⃣ Clone the repository:

```bash
git clone https://github.com/toutsos/CV-custom-detector-and-tracker.git
cd CV-custom-detector-and-tracker
```

**Main dependencies:**

- `ultralytics`
- `opencv-python`
- `numpy`
- `pandas`
- `torch`

---

## Usage

### 1️⃣ Train a YOLO Model

- Open `train_models.ipynb`.
- Update the dataset path (handled via Roboflow).
- Run cells to train models on:
  - Original dataset
  - Augmented dataset
  - Augmented + hard negatives

### 2️⃣ Run Inference

- Open `yolo_inference.ipynb`.
- Set the path to your trained `.pt` model.
- Run inference on:
  - Images
  - Videos

### 3️⃣ Track Objects

- Open `object_tracking.ipynb`.
- Steps:
  - Extract frames from your video.
  - Manually annotate objects (draw bounding boxes).
  - Track objects with **KCF**.
  - If tracking fails → auto-detect with YOLO and reinitialize.
  - Compare manual vs. tracked annotations visually + export to CSV.

---

## Dataset Notes

- Dataset prepared via **Roboflow**:
  - Original: 35 train / 10 val / 5 test images.
  - Augmented: 70 train (crop, rotate, hue, noise).
  - Augmented + background: 106 train (added negative samples).

---

## Example Outputs

- Annotated videos with bounding boxes.
- CSV files of annotations:
  - Frame number
  - Object coordinates
- Comparison visuals:
  - Green = Manual
  - Red = Tracked

---
