# 🩺 VAE 7-Day Risk Calculator (Cox Model)

## Overview
This application implements a **Cox proportional hazards model** to estimate the **7-day risk of ventilator-associated events (VAEs)** in mechanically ventilated patients.

The model is derived from:

> Kubbara A, Barnett WR, Safi F, et al. *Case-control study investigating parameters affecting ventilator-associated events in mechanically ventilated patients.* Am J Infect Control. 2019;47(4):462-464.

---

## Model Description

### Variables included
  - Arrival from home
- Site of intubation:
  - Emergency Department
  - Ward
- Comorbidities:
  - CAD
  - CHF
  - Kidney disease
  - Lung disease (COPD)
- Clinical factors:
  - BMI group
  - TPN

All inputs are binary:
- Yes = 1
- No = 0

---

## Mathematical Formulation

### Linear predictor
beta_X = sum(coefficient * indicator)

### Centering
eta = beta_X - center  
center = 0.2556

### Survival
S(7|X) = S0(7) ^ exp(eta)  
S0(7) = 0.6693146

### Risk
Risk = 1 - S(7|X)

---

## Interpretation

This model predicts:

**Risk of meeting CDC-defined VAE surveillance criteria within 7 days**

It does NOT predict:
- Clinical pneumonia
- Infection certainty
- Mortality

---

## Model Performance

- Somers’ D (Dxy): 0.302  
- C-statistic ≈ 0.65  

Interpretation:
- Moderate discrimination
- Suitable for risk stratification and QI use

---

## Use Cases

- Quality improvement
- Risk stratification
- Operational planning

---

## Limitations

- Single-center model
- Retrospective data
- No dynamic ventilator variables
- 7-day prediction only

---

## Disclaimer

For research and QI use only. Not for direct clinical decision-making without validation.
