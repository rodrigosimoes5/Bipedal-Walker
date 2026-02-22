# Bipedal-Walker Reinforcement Learning

This repository contains the project developed for the course **Introduction to Intelligent and Autonomous Systems**. The main goal was to apply Reinforcement Learning (RL) techniques to solve the `BipedalWalker-v3` environment and analyze how well agents adapt to a structural change in the environment (injury simulation).

**Authors:**
* Francisca Cerqueira
* Iara Ferreira
* Rodrigo Simões

---

## Project Overview

The work was split into three main milestones, focusing on environment customization, implementing and training agents with **Stable-Baselines3**, and performing a comparative analysis of results.

### 1. Environment Customization
* **Base Environment:** `BipedalWalker-v3` (Box2D/Gymnasium).
* **Implemented Modification:** Creation of the `InjuredBipedalWalker` environment.
* **Description:** A mechanical "injury" was introduced in the robot, characterized by a **70% loss of power** in the right-leg motors.
* **Goal:** Test algorithm robustness and force the agent to learn an asymmetric compensatory gait.
* **Code:** Available in `my_envs/injured_bipedal.py`.

### 2. Reinforcement Learning Agent
* **Algorithm Selection:** Four algorithms were compared: **PPO**, **A2C**, **SAC**, and **TD3**.
* **Selected Agent:** **TD3** (Twin Delayed DDPG) showed the best performance and stability in preliminary experiments.
* **Tuning:** Hyperparameter optimization (Learning Rate, Gamma, Action Noise). The best configuration for the original environment was the "Myopic" variant ($\gamma=0.98$), which achieved a consistent average score of **~278 points**.

### 3. Evaluation and Analysis
* **Robustness Test:** The agent trained in the healthy environment failed when transferred to the injured environment (performance drop from ~278 to ~27 points), highlighting limited generalization to dynamic failures.
* **Retraining in the Modified Environment:** Training directly in `InjuredBipedalWalker` allowed the agent to learn not to fall (a survival strategy), but it struggled to move forward efficiently, frequently resulting in *timeouts*.
* **Conclusion:** The agent developed a visible compensatory gait, trading speed for stability.

---

## Installation and Usage

### 1. Prerequisites
Make sure you have Python installed (recommended 3.8+).

### 2. Install dependencies
```bash
pip install -r requirements.txt
