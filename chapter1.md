---
layout: clean
title: About
---

# Chapter 1: Introduction: Advanced Machine Learning

> *All models fade, but principles endure!*

## Abstract

In this chapter, we first introduce the traditional empirical risk minimization (ERM) framework, using classical label prediction problems to illustrate three key components: loss functions, optimization algorithms, and generalization analysis.

We then delve into advanced learning methods, including distributionally robust optimization (DRO) and group DRO, aimed at enhancing model robustness. Next, we present an advanced learning paradigm called empirical X-risk minimization (EXM) and discuss its applications. Finally, we introduce a new learning paradigm named data prediction for learning foundation models in modern AI with a discriminative X-risk.

---

## 1. Empirical Risk Minimization

### 1.1 What is Machine Learning?

In 1959, Arthur Samuel, a pioneer in the field of machine learning (ML), defined Machine Learning as the:

> *“field of study that gives computers the ability to learn without being explicitly programmed.”*

Today, machine learning has become the foundation of AI. The essence of machine learning is to learn a model by optimizing an objective function on training data, with the goal of achieving strong generalization to unseen data.

Optimization plays a fundamental role in machine learning, as it underpins:

1. the formulation of objective functions,  
2. the development of optimization algorithms, and  
3. the analysis of generalization error in learned models.

While (3) is an important subject of ML, this book focuses on (1) and (2). Below, we will use the traditional label prediction problem to illustrate these components.

---

### 1.2 Label Prediction

In supervised learning, the primary objective is to learn a predictive model from a given set of labeled training data.

Let $$(\mathbf{x}, y)$$ be a data-label pair, where  
$$\mathbf{x} \in \mathcal{X} \subset \mathbb{R}^{d_0}$$ denotes the input features, and  
$$y \in \mathcal{Y} = \{1, \ldots, K\}$$ is the corresponding label.

The goal is to learn a predictive model parameterized by  
$$\mathbf{w} \in \mathbb{R}^d$$ (e.g., a deep neural network),  
which induces a scoring function:

$$
h(\mathbf{w}; \cdot): \mathcal{X} \to \mathbb{R}^K.
$$

A classical framework for learning such a model is the well-known **empirical risk minimization (ERM)**, which minimizes the empirical risk over the training dataset.

To this end, a pointwise loss function  
$$\ell(\mathbf{w}; \mathbf{x}, y)$$  
is defined to measure the discrepancy between the model’s prediction $h(\mathbf{w}; \mathbf{x})$ and the true label $y$.

Given a training dataset  
$$\mathcal{S} = \{(\mathbf{x}_1, y_1), \ldots, (\mathbf{x}_n, y_n)\},$$  
the ERM problem is formulated as:

$$
\min_{\mathbf{w} \in \mathcal{W}} R_{\mathcal{S}}(\mathbf{w}) := \frac{1}{n} \sum_{i=1}^n \ell(\mathbf{w}; \mathbf{x}_i, y_i).
$$

