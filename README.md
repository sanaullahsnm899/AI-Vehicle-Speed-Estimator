# 🚗 AI Vehicle Speed Estimator — YOLO26 + ByteTrack

A computer-vision notebook that tracks vehicles in recorded traffic footage and estimates their **speed when they cross a configurable virtual line**. It annotates detections and displays speed readings in miles per hour (mph).

**Notebook:** `speed_estimator.ipynb`

## Features
- Detects **cars, motorcycles, buses, and trucks** using pretrained YOLO26 Small (`yolo26s.pt`).
- Tracks individual vehicles with ByteTrack IDs.
- Detects when a vehicle's bounding-box center crosses a user-defined horizontal line.
- Estimates speed from tracked pixel displacement, video FPS, and a manually calibrated **feet-per-pixel** scale.
- Shows vehicle type and the estimated mph reading in an overlay.
- Records each tracked vehicle's crossing once per track ID.

## Technologies
Python, Ultralytics YOLO26, ByteTrack, OpenCV, NumPy, Google Colab.

## Getting Started
1. Open the notebook in **Google Colab** and run the dependency setup cell.
2. Upload a traffic video with moving vehicles.
3. Generate and inspect `sample_frame.jpg`.
4. **Calibrate your video:** edit `LINE_Y`, `REAL_DISTANCE_FT`, and `PIXEL_DISTANCE_AT_LINE` so they match a real reference distance at the trigger line. The example values are placeholders.
5. Run the detection and speed-processing cells to export `speed_output.mp4`. The Drive copy cell is optional.

**Dependencies:**
```bash
pip install ultralytics opencv-python numpy
```

## Output
- `sample_frame.jpg` — reference image for line placement and calibration.
- `speed_output.mp4` — annotated vehicle video with line crossing and mph readings.

## Limitations
Speed values are **approximate**, especially with perspective distortion, diagonal motion, moving cameras, or inaccurate scale calibration. Measurements use 2D image displacement, not a calibrated roadway geometry model. This project is a demonstration, **not a certified traffic-enforcement instrument**.

**Maintainer:** [@sanaullahsnm899](https://github.com/sanaullahsnm899)
