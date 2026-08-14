## PsychoPy Numerical Go/No-Go Task with EEG LSL Marker Integration

Hi Everyone. This PsychoPy experiment is designed to present numbers (1–10) in five randomised blocks and transmit real-time event markers via Lab Streaming Layer (LSL) to an EEG acquisition pipeline.


## Overview & Design

This repository contains the PsychoPy implementation of a **Numerical Go/No-Go Paradigm**. 

### Experimental Structure
* **Total Runs/Blocks:** 5 runs.
* **Trials per Run:** 10 trials (numbers 1 through 10 presented in a **randomized order** within each run).
* **Total Trials:** 50 trials total across the session.

### Task Conditions
* **Go Condition:** Even numbers (`2, 4, 6, 8, 10`) → Requires a rapid motor response (Key press: 'A').
* **No-Go Condition:** Odd numbers (`1, 3, 5, 7, 9`) → Requires withholding a response.

---

## Event Markers & Trigger Logic

Event markers are streamed dynamically via **LSL** to synchronise behavioural performance with continuous EEG recordings:

| Event | Trigger Condition | LSL Marker Sent |
| :--- | :--- | :--- |
| **Stimulus Onset** | Presentation of digits `1–10` | `Stim_<number>` (e.g., `Stim_4`) |
| **Correct Response** | Response on an **Even** number (Hit) | `Corr` |
| **Incorrect Response** | Response on an **Odd** number (False Alarm) | `InCorr` |

---

## EEG Analysis

Data collected with this paradigm can be processed using Event-Related Potentials (ERPs) and Time-Frequency Analysis to investigate:

* **No-Go N200 / P300:** Neural markers of response inhibition and cognitive conflict monitoring over fronto-central electrodes.
* **Error-Related Negativity (ERN) & Error Positivity (Pe):** Generated post-response during false alarms (`InCorr` marker) to evaluate automatic error processing.
* **Motor Preparation & LRPs:** Lateralized Readiness Potentials linked to motor execution (`Corr` marker).
* **Frontal Theta Dynamics (4–8 Hz):** Power changes during active response suppression and error detection.

---

## Requirements & Dependencies

Ensure the following packages are installed in your Python environment:

* Python 3.8+
* [PsychoPy](https://www.psychopy.org/)
* `pylsl` (Python LSL interface)

```bash
pip install psychopy pylsl
