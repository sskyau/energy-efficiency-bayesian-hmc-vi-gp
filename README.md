# Energy Efficiency Estimation with Bayesian Machine Learning

This is the final project for CM50268 Bayesian Machine Learning (Semester 2, 2022) at the University of Bath.

## Objective

The goal of the project is to estimate the heating load of buildings given 8 architectural parameters listed below:

| Attributes # | Attribute Description |
| ------------- | ------------- |
| X1  | Relative Compactness  |
| X2  | Surface Area  |
| X3  | Wall Area  |
| X4  | Roof Area  |
| X5  | Overall Height  |
| X6  | Orientation  |
| X7  | Glazing Area |
| X8  | Glazing Area Distribution  |

The data used in this project is the ["Enercy Efficiency" dataset from UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/energy+efficiency).

## Tasks

There are 5 tasks in this project, brief description for the tasks are provided below. The final report can be found [here](https://github.com/sskyau/energy-efficiency-bayesian-hmc-vi-gp/blob/master/CM50268-Final%20Report.pdf).

#### 1. Exploratory Analysis
Descriptive statistics and distributions of the attributes are explored. A simple ordinary least-squares (OLS) linear regression model is also developed as the baseline.

#### 2. Bayesian Linear Regression (BLR)

A BLR model is set up for the problem. In the setup, it is assumed that there are 3 latent variables for the problem:

| Latent Variable | Description |
| ------------- | ------------- |
| w  | Weights of the 8 attributes  |
| α  | Precision of the distribution of w  |
| β  | Precision of the distribution of heating load (target variable) |

The methods of **Type-II ML** and **Variational Inference (VI)** for approximating the latent variables are applied and compared. Both methods arrive at solutions that are almost identical as the problem is not computationally complex. For a more complex problem, Type-II ML would require a much longer runtime, and using VI for approximation would be more practical, with sacrifice on accuracy.

#### 3. Hamiltonian Monte Carlo (HMC) Sampling on a 2D Gaussian Example

The method of HMC for approximating distributions is verified on a simple 2D Gaussian example to approximate the covariances.

#### 4. HMC Sampling for the BLR model 

HMC is applied on the BLR problem set up in Task 2 to approximate the latent variables. Theoretically, given inifite time, HMC would arrive at the exact solution. Although there was insufficient time to compute the exact solution, the final error rates achieved in the project are highly comparable to the OLS, Type-II ML and VI methods.

#### 5. Gaussian Process (GP) for the BLR model

Finally, the non-parametric method GP is explored. The method achieves the best performance among all methods experimented in the project as non-linear kernels can be incorporated to better fit the true ditribution of the data. However, the method is also more prone to the problem of overfitting.
