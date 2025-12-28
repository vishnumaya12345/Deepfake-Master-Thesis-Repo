# Master Thesis ( Comparative evaluation of Deepfake detection and generation using DeepfakeBench ) – Experiments (Code + Results)

This repository contains the Colab notebooks, and exported result tables used in my master’s thesis on deepfake detection using **DeepfakeBench**.

## Thesis focus (what this repo demonstrates)
- We initially evaluated **9 detectors** available in DeepfakeBench (screening stage) and then selected **3 representative finalists** for detailed analysis:
  - **Xception** (naive)
  - **F3Net** (frequency-aware)
  - **FFD** (spatial)
- Evaluation is **frame-level** using **AUC, AP, and EER**
- In addition to standard benchmarks, we evaluate **custom multi-source identity-swap datasets** created with **Faceswap.dev** to study how increasing the number of source images (1 / 5 / 10) affects detectability.

## Datasets used
- **FaceForensics++ (C40)** (subset used for evaluation)
- **Celeb-DF** (subset used for evaluation)
- **Custom identity-swap datasets (Swap-1 / Swap-5 / Swap-10)**:
  - 50 real + 50 fake videos per set
  - 20 sampled frames per video (~2,000 frames per set)
  - Swaps generated with Faceswap.dev using 1/5/10 source images per identity

⚠️ **Datasets are NOT included** in this public repository (privacy + licensing).  
See `data/README.md` for dataset download links and folder structure.

## Key findings (high-level)
- Standard benchmark performance does not fully reflect the harder regime introduced by multi-source identity swaps.
- As the number of source images increases (1 → 5 → 10), swaps become more perceptually convincing and detection becomes harder (AUC decreases / EER increases across detectors).
- Risk is illustrated through **Fake→Real** errors and qualitative failure examples in the thesis.

## Repository structure
- `notebooks/` : Colab notebooks for screening (9 detectors) and final evaluation (3 detectors)
- `results/` : exported CSV tables/plots/logs (no videos)
- `results/tables/` : frame-level output tables used for additional error inspection and for selecting representative misclassified-frame examples
- `environment/` : requirements/setup notes
- `src/` : helper scripts (if any)
- `data/` : dataset instructions only (no data)

## How to run (summary)
1. Set up environment using `environment/requirements.txt`
2. Download datasets and follow `data/README.md` for folder structure
3. Run notebooks in `notebooks/` (notebook names indicate detector + dataset)

## Notes
- This repository is intended for research reproducibility and does not redistribute raw faces/videos.
