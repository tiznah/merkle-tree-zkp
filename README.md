# ZKP Partition Merkle Proof

A simple implementation of the Zero-Knowledge Proof example described in [Mastering Ethereum Chapter 17](https://masteringethereum.xyz/chapter_17.html#chapter-17-zero-knowledge-proofs).

This project proves you know a solution to the **Partition Problem** (splitting a set of numbers into two subsets with equal sums) without revealing the solution itself, using **Merkle Trees** for efficient commitments.

## How It Works

1.  **Prover**:
    * Takes a list of numbers `S` (e.g., `[1, 1, 5, 7]`).
    * Finds a "witness" `w` (a list of `+1` and `-1`) such that the dot product is 0.
    * Commits to the witness by creating a **Merkle Tree** where each leaf is a value in `w`.
    * Publishes the **Merkle Root** as the commitment.

2.  **Verifier**:
    * Challenges the prover by asking for the value at a random index `i` (and `i+1`).
    * Checks if the equation holds (e.g., `s[i] = w[i] + w[i+1]`).

3.  **Proof**:
    * The prover reveals *only* the requested values and provides a **Merkle Proof** (branches) to prove they belong to the committed root.
    * The verifier confirms the proof matches the root and the values satisfy the partition logic.
