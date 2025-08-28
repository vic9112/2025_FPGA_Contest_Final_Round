## 🏁 Final Round

---

## 🏆 Evaluation Criteria

The final score consists of three components, for a total of **100 points**:

1. **Project Completeness (40 pts)**  
   - The submitted HLS project must compile successfully and generate all evaluation metrics (mIoU, latency, and resource usage).  
   - If the flow cannot be executed to completion, this portion of the score will not be awarded.  

2. **HLS Performance Metrics (40 pts)**  
   Submissions will be evaluated based on **semantic accuracy**, **latency**, and compliance with **FPGA resource constraints**:  
   - **Semantic Accuracy**  
     - **mIoU**: Mean Intersection over Union, a measure of semantic segmentation accuracy.  
   - **Latency**  
     - Latency = Max Latency from the `csynth` report.  
     - Different from the [qualifying round](https://github.com/nycu-pcs-lab/FPGA_Challenge2025_Qualifying_Round_Challenge), RTL simulation is skipped since it takes too long.  
     - The `csynth` report is located at:  
       `myproject_prj/solution1/syn/report/myproject_csynth.rpt`  
     - Be sure to set both the cosim FLAG and validation FPGA to **0** to skip RTL simulation.  
       <div style="border:8px solid black; display:inline-block; padding:4px;">
       <img src="build_prj_tcl_FLAGS.png" alt="img" width="400"/></div>  
   - **FPGA Resource Constraints**  
     - All four resources reported by `vynth` must be ≤ 75% of the target FPGA’s capacity, identical to the [qualifying round requirements](https://github.com/nycu-pcs-lab/FPGA_Challenge2025_Qualifying_Round_Challenge).  
     - Target FPGA: **Xilinx Alveo U55C**.  

   **Final Scoring Rule:**  
   - If **FPS (1/latency) ≥ 60**:  
     **Score = mIoU**  
   - If **FPS < 60**:  
     **Score = mIoU × (FPS / 60)**  
   - This ensures real-time performance is prioritized, while rewarding higher segmentation accuracy. Submissions below 60 FPS are proportionally penalized.  

3. **Poster & Presentation (20 pts)**  
   - Each team must deliver both a **poster** and an **oral presentation** on the final day.  
   - Poster size and presentation time limits follow the [official website](https://sites.google.com/ceres.iee.nycu.edu.tw/2025-fpga/%E6%B1%BA%E8%B3%BD%E5%90%8D%E5%96%AE?authuser=0) guidelines.  
   - Judges will award points based on presentation quality and overall project completeness.  

---

## 📂 Dataset Introduction

Cityscapes is a popular benchmark dataset for semantic segmentation in autonomous driving applications.

- **Training set**: 2,975 images  
- **Validation set**: 500 images  
- The **validation set** is used for performance evaluation.  
- Each image is annotated with **20 semantic classes** (e.g., building, road, car, pedestrian, etc.)

To accommodate FPGA limitations, **testing images are resized to 64×64**. However, we provide training images at multiple resolutions (2×, 4×) and **encourage participants to leverage these high-resolution variants to enhance model performance**.
![img1](visualize_predictions.png)


---

## Accuracy Scoring System & Dataset

- The dataset and evaluation system are hosted on the [Kaggle Competition Page](https://www.kaggle.com/t/195ff157a94e42448487db92f612b4ff), same as the setup used in the [qualifying round](https://github.com/nycu-pcs-lab/FPGA_Challenge2025_Qualifying_Round_Challenge)
- You can import and run the [Jupyter notebook](https://github.com/nycu-pcs-lab/FPGA_Challenge2025_Final_Round_Challenge/blob/main/cityscape_qkeras_hls4ml_endtoend.ipynb) on Kaggle to see an end-to-end workflow example.

