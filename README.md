# Reinforcement Learning Basics

This project demonstrates a basic implementation of Reinforcement Learning (RL) using the Bellman equation to find the optimal value function for a 4x4 GridWorld.

## Problem Description

We are given a 4x4 GridWorld environment.  The agent starts in the top-left corner (state 0) and aims to reach the bottom-right corner (state 15).

*   **Actions:** The agent can move up, down, left, or right.
*   **Stochasticity:** The agent's actions are stochastic; each action (up, down, left, right) has an equal probability of being executed.
*   **Rewards:** Each move incurs a reward of -1. Reaching the terminal state (state 15) yields a reward of 0.
*   **Goal:**  Find the optimal value function V(s) for each state s.

## Implementation Details

The core of the solution involves iteratively applying the Bellman equation in its stochastic form until convergence.

### Bellman Equation

The Bellman equation used in this project is:

```
V(s) = Σ P(s'|s, a) * [R(s, a, s') + γ * V(s')]
```

Where:

*   `V(s)` is the value of state `s`.
*   `P(s'|s, a)` is the probability of transitioning to state `s'` from state `s` by taking action `a`.  In our case, this is equal for all moves.
*   `R(s, a, s')` is the reward received when transitioning from state `s` to state `s'` by taking action `a`.
*   `γ` is the discount factor (set to 1 in this project).
*   The summation is over all possible next states `s'`.

### Algorithm

1.  **Initialization:** Initialize `V(s)` to 0 for all states `s`.
2.  **Iteration:** Repeat the following until convergence:
    *   For each state `s`:
        *   Calculate the new value of `V(s)` using the Bellman equation.  This involves considering all possible actions (up, down, left, right) and their corresponding transition probabilities and rewards.
    *   Calculate the maximum change in `V(s)` across all states during the current iteration.
3.  **Convergence:** Stop iterating when the maximum change in `V(s)` is less than a predefined threshold (1e-4 in this project).

## Output

Running and Final Value Function output

```
Starting...
Iteration 100, max change: 0.16564811116836609
Iteration 200, max change: 0.0223975903278415
Iteration 300, max change: 0.003028419997747278
Iteration 400, max change: 0.0004094783210462083
Done after 471 iterations

Final values:
[[-59.42367735 -57.42387125 -54.2813141  -51.71012579]
 [-57.42387125 -54.56699476 -49.71029394 -45.13926711]
 [-54.2813141  -49.71029394 -40.85391609 -29.99766609]
 [-51.71012579 -45.13926711 -29.99766609   0.        ]]
```


## Further Improvements

*   Implement policy extraction to determine the optimal policy based on the calculated value function.
*   Experiment with different discount factors (gamma).
*   Add obstacles to the GridWorld environment.
*   Visualize the value function and policy.