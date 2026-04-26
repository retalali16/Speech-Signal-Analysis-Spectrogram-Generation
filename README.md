# 🎵 Speech Signal Analysis & Spectrogram Generation

> **Assignment 2 — Audio Signal Processing for Machine Learning**
> Course: Zewail City of Science and Technology

---

## 📌 Overview

This project performs end-to-end analysis of speech audio signals using FFT and STFT. It visualizes frequency content, estimates the fundamental frequency (F0), generates annotated spectrograms, and explores the effect of different window sizes and overlaps on time-frequency resolution.

---

## 🎯 Objectives

- Load and visualize raw audio waveforms
- Compute and plot the frequency spectrum using **Fast Fourier Transform (FFT)**
- Identify **dominant frequencies** and estimate **fundamental frequency (F0)** using `pyin`
- Apply **Short-Time Fourier Transform (STFT)** to generate spectrograms
- Annotate spectrograms with spoken word labels
- Analyze **formant patterns** and phoneme distinctions
- Explore the effect of different **window sizes and hop lengths** on time-frequency resolution

---

## 📁 Project Structure

```
Spectrogram/
│
├── Spectrogram.ipynb          # Main implementation notebook
├── pianos-by-jtwayne-7-174717.mp3   # Input audio file
└── README.md
```

---

## ⚙️ Pipeline

### 1. Audio Loading
- Audio loaded at `sr = 16000 Hz` using `librosa.load`
- Sentence: *"the piano plays beautiful melodies every day"*

### 2. Waveform Visualization
- Time-domain plot of the raw audio signal (Amplitude vs. Time)

### 3. FFT — Frequency Spectrum
- Applied `scipy.fft.fft` on the full signal
- Plotted magnitude spectrum (Frequency Hz vs. Magnitude)
- Identified **Top 5 dominant frequencies** by magnitude

### 4. Fundamental Frequency (F0) Estimation
- Used `librosa.pyin` with `fmin=50 Hz`, `fmax=500 Hz`
- Overlaid F0 contour on the waveform plot
- Reported mean, min, and max F0 values

### 5. STFT & Spectrogram
- Parameters: `n_fft=1024`, `hop_length=256`, Hann window
- Converted STFT magnitude to dB scale with `amplitude_to_db`
- Plotted spectrogram with `magma` colormap
- Annotated each word from the sentence evenly across the time axis

### 6. Window & Overlap Analysis
- Compared different `n_fft` and `hop_length` combinations
- Discussed trade-off between **time resolution** (small window) and **frequency resolution** (large window)

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| `librosa` | Audio loading, STFT, F0 estimation, display |
| `scipy.fft` | FFT computation |
| `matplotlib` | All plotting |
| `pydub` | Audio segment utilities |
| `numpy` | Numerical operations |

---

## ⚙️ Setup & Installation

```bash
pip install librosa scipy matplotlib pydub numpy
```

Run on **Google Colab** (recommended) or Jupyter Notebook. Place your audio file at the path specified in the notebook config cell.

---

## 📊 Key Results

- **Top dominant frequencies** identified from the FFT magnitude spectrum
- **F0 estimated** via probabilistic YIN (`pyin`) — overlaid on waveform
- **Annotated spectrogram** produced showing word-level time blocks
- **Formant patterns** visible in spectrogram as horizontal bands of energy
- Window size analysis: larger `n_fft` → better frequency resolution, worse time resolution; smaller `n_fft` → opposite

