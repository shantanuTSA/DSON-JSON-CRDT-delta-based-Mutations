# DSON: JSON CRDT using Delta-Mutations

## Overview

This repository contains my work on the paper:

**"DSON: JSON CRDT Using Delta-Mutations for Distributed Document Stores"**

It includes:

* A LaTeX research poster
* The original research paper
* Supporting material for presentation

This work was completed as part of the **NoSQL Systems (DAS 839)** course at IIIT Bangalore.

---

## Motivation

Distributed systems often require multiple replicas to update the same JSON document concurrently, leading to:

* Conflicts between updates
* High metadata overhead
* Inefficient synchronization

DSON addresses these issues using delta-based CRDTs and structured conflict resolution.

---

## Key Concepts

* **CRDTs** ensure convergence without manual conflict resolution
* **Delta-based updates** transmit only changes instead of full state
* **Dot (node, counter)** uniquely identifies each update
* **Causal context** tracks observed updates for correct merging

---

## Core Contributions

* **ORArray**: Handles arrays using stable positions instead of indices and supports concurrent operations
* **CompDotFun**: Prevents deleted elements from reappearing
* **JSON CRDT Composition**:

  ```
  Value = Map | Array | Register
  ```

---

## Complexity

* Without concurrency:
  O(D + n log n)

* With concurrency:
  O(k²D + n log n)

Where D is document size, n is number of replicas, and k is concurrent updates.

---

## Evaluation

Compared to Automerge and Yjs, DSON:

* Maintains constant metadata in most operations
* Avoids unbounded growth in common workloads
* Performs better under repeated updates and modifications

---

## Limitations

* Worst-case metadata grows under high concurrency
* Anti-entropy synchronization is not optimal
* Replica removal is complex
* Current implementation is a research prototype

---

## Future Work

* More efficient delta synchronization
* Safe replica removal mechanisms
* Performance optimization
* Deployment improvements

---

## Author

Shantanu T
IIIT Bangalore

---

## References

* Rinberg et al., *DSON: JSON CRDT Using Delta-Mutations*
* Automerge
* Yjs

---
