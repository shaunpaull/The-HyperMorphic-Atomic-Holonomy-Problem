# The-HyperMorphic-Atomic-Holonomy-Problem
The HyperMorphic Atomic-Holonomy Problem


# The HyperMorphic Atomic-Holonomy Problem

> **An extremal problem on families of reversible laws whose pairwise commutators have the smallest possible nontrivial support — with a separate, conjectural bridge to quantum measurement dynamics.**

<p align="center">
  <strong>Finite group theory · Algebraic combinatorics · Holonomy · Quantum foundations</strong>
</p>

---

## Scientific status

This repository contains a **newly proposed extremal problem**, several elementary results and small-\(n\) computational observations, and a sequence of **candidate** quantum-measurement constructions motivated by the same holonomy language.

The status of each layer is different:

| Component | Status |
|---|---|
| Definition of the atomic-holonomy extremal function \(H(n)\) | Exact mathematical definition |
| Minimality of a \(3\)-cycle as nontrivial permutation commutator support | Elementary theorem |
| Star-family lower bound \(H(n)\ge n-1\) | Proved |
| Values \(H(3)=4,\ H(4)=4,\ H(5)=7,\ H(6)=9\) | Exhaustively reproducible for small \(n\); code should be committed |
| Conjecture \(H(n)=\Theta(n)\) | Open |
| Sharper target \(H(n)\le 2n+O(1)\) | Open |
| HCARL stochastic measurement dynamics | Conditional mathematical model |
| Born-rule result | Valid inside the stated stochastic/localization assumptions |
| Curvature-forced coupling theorem | Conditional on locality, gauge covariance, analyticity, and lowest-derivative assumptions |
| Covariant HyperMorphic law-field theory | Candidate effective field theory; not experimentally established |
| Objective single-outcome interpretation | Requires an additional physical ontology for the output record |
| Experimental curvature-dependent reversal deficit | Proposed and untested |

**Nothing in this repository should currently be described as an experimentally confirmed solution to the quantum measurement problem.**

---

## Contents

1. [Core mathematical problem](#core-mathematical-problem)
2. [Why a \(3\)-cycle is atomic](#why-a-3-cycle-is-atomic)
3. [The extremal graph formulation](#the-extremal-graph-formulation)
4. [Basic construction and lower bound](#basic-construction-and-lower-bound)
5. [Known small values](#known-small-values)
6. [Main conjectures](#main-conjectures)
7. [Pair-density version](#pair-density-version)
8. [Invariant-constrained variants](#invariant-constrained-variants)
9. [Reproducible exhaustive search](#reproducible-exhaustive-search)
10. [Connection to existing permutation literature](#connection-to-existing-permutation-literature)
11. [Quantum-measurement research program](#quantum-measurement-research-program)
12. [Candidate experimental signature](#candidate-experimental-signature)
13. [Repository structure](#repository-structure)
14. [Research roadmap](#research-roadmap)
15. [Contribution standard](#contribution-standard)
16. [Citation](#citation)
17. [References](#references)
18. [License](#license)

---

# Core mathematical problem

Let

\[
X_n=\{1,\ldots,n\},
\qquad
S_n=\operatorname{Sym}(X_n).
\]

Each permutation \(\sigma\in S_n\) may be interpreted as a reversible law acting on \(n\) states. Its inverse \(\sigma^{-1}\) gives exact recovery.

Throughout this repository, permutations are composed right-to-left:

\[
(\sigma\tau)(x)=\sigma(\tau(x)).
\]

For \(\sigma,\tau\in S_n\), define the group commutator

\[
[\sigma,\tau]
=
\sigma\tau\sigma^{-1}\tau^{-1}.
\]

We call the ordered law switch:

- **flat** if \([\sigma,\tau]=\mathrm{id}\);
- **curved** if \([\sigma,\tau]\neq\mathrm{id}\);
- **atomically curved** if \([\sigma,\tau]\) is a \(3\)-cycle.

Define

\[
\boxed{
H(n)
=
\max
\left\{
|\mathcal L|:
\mathcal L\subseteq S_n,\ 
[\sigma,\tau]\text{ is a \(3\)-cycle for all distinct }
\sigma,\tau\in\mathcal L
\right\}.
}
\]

The central problem is:

\[
\boxed{\text{Determine }H(n).}
\]

This includes:

1. determining the asymptotic growth of \(H(n)\);
2. proving upper and lower bounds;
3. classifying extremal families;
4. determining stability and supersaturation results;
5. understanding constrained versions inside subgroups or invariant-preserving law classes.

---

# Why a \(3\)-cycle is atomic

## Proposition 1 — Commutators are even

For every \(\sigma,\tau\in S_n\),

\[
[\sigma,\tau]\in A_n.
\]

### Proof

The sign map

\[
\operatorname{sgn}:S_n\rightarrow\{\pm1\}
\]

is a homomorphism. Therefore

\[
\begin{aligned}
\operatorname{sgn}([\sigma,\tau])
&=
\operatorname{sgn}(\sigma)
\operatorname{sgn}(\tau)
\operatorname{sgn}(\sigma^{-1})
\operatorname{sgn}(\tau^{-1})\\
&=1.
\end{aligned}
\]

Hence every commutator is even. \(\square\)

## Proposition 2 — Minimal nontrivial support

Every nonidentity commutator in \(S_n\) moves at least three points. If it moves exactly three points, it is a \(3\)-cycle.

### Proof

A nonidentity permutation cannot move exactly one point. A permutation moving exactly two points is a transposition and is therefore odd. By Proposition 1, a commutator is even, so a nonidentity commutator must move at least three points.

The nonidentity even permutations on a set of three points are precisely the two orientations of a \(3\)-cycle. \(\square\)

This motivates the terminology:

\[
\boxed{
\text{\(3\)-cycle}
=
\text{smallest-support nonzero switching holonomy}.
}
\]

---

# The extremal graph formulation

Define the **atomic-holonomy graph**

\[
\mathcal G_n=(V_n,E_n)
\]

by

\[
V_n=S_n
\]

and

\[
\{\sigma,\tau\}\in E_n
\quad\Longleftrightarrow\quad
[\sigma,\tau]\text{ is a \(3\)-cycle}.
\]

The relation is symmetric because

\[
[\tau,\sigma]=[\sigma,\tau]^{-1},
\]

and the inverse of a \(3\)-cycle is again a \(3\)-cycle.

Then

\[
\boxed{
H(n)=\omega(\mathcal G_n),
}
\]

where \(\omega(G)\) denotes the clique number of a graph.

The graph is invariant under simultaneous conjugation:

\[
(\sigma,\tau)
\mapsto
(g\sigma g^{-1},g\tau g^{-1}),
\]

because

\[
[g\sigma g^{-1},g\tau g^{-1}]
=
g[\sigma,\tau]g^{-1},
\]

and conjugation preserves cycle type.

This symmetry should be exploited in exact searches and structural proofs.

---

# Basic construction and lower bound

For \(n\ge3\), define the transposition-star family

\[
\mathcal S_n
=
\{(1\,i):2\le i\le n\}.
\]

For distinct \(i,j\),

\[
\begin{aligned}
[(1\,i),(1\,j)]
&=
(1\,i)(1\,j)(1\,i)(1\,j)\\
&=
(1\,i\,j),
\end{aligned}
\]

which is a \(3\)-cycle.

Therefore every two distinct members of \(\mathcal S_n\) are adjacent in \(\mathcal G_n\), so \(\mathcal S_n\) is a clique of size \(n-1\).

## Theorem 3 — Star lower bound

For every \(n\ge3\),

\[
\boxed{
H(n)\ge n-1.
}
\]

The construction is simple, but it may or may not be asymptotically extremal.

---

# Known small values

Exhaustive maximum-clique enumeration gives:

| \(n\) | \(|S_n|\) | \(H(n)\) |
|---:|---:|---:|
| 3 | 6 | 4 |
| 4 | 24 | 4 |
| 5 | 120 | 7 |
| 6 | 720 | 9 |

Thus:

\[
\boxed{
H(3)=4,\qquad
H(4)=4,\qquad
H(5)=7,\qquad
H(6)=9.
}
\]

These values are consistent with linear growth, but four data points do not establish an asymptotic law.

The current repository should eventually contain:

- the exact search implementation;
- software and dependency versions;
- the maximum clique certificate for each \(n\);
- an independently checkable upper-bound certificate;
- runtime and memory statistics;
- symmetry reduction details.

Without those artifacts, the values should be treated as computational observations rather than a complete reproducibility package.

---

# Main conjectures

## Atomic-Holonomy Conjecture

\[
\boxed{
H(n)=\Theta(n).
}
\]

Equivalently, there should exist constants \(c,C>0\) such that for all sufficiently large \(n\),

\[
cn\le H(n)\le Cn.
\]

The lower bound already holds with \(c\) arbitrarily close to \(1\), because

\[
H(n)\ge n-1.
\]

The difficult direction is the linear upper bound.

## Sharper upper-bound target

A stronger first target is

\[
\boxed{
H(n)\le 2n+O(1).
}
\]

This is a proposed target, not a theorem.

A superlinear construction would refute the linear-growth conjecture and reveal a high-density regime of pairwise minimally noncommuting reversible laws.

## Classification problem

Classify all \(\mathcal L\subseteq S_n\) satisfying

\[
|\mathcal L|=H(n)
\]

up to simultaneous conjugation and other genuine automorphisms of the relation.

## Stability problem

Prove that a family with

\[
|\mathcal L|\ge (1-\varepsilon)H(n)
\]

must be structurally close to one of a bounded number of extremal templates.

---

# Pair-density version

For \(m\le n!\), define

\[
U_n(m)
=
\max_{\substack{\mathcal L\subseteq S_n\\|\mathcal L|=m}}
\left|
\left\{
\{\sigma,\tau\}\subseteq\mathcal L:
[\sigma,\tau]\text{ is a \(3\)-cycle}
\right\}
\right|.
\]

Then \(U_n(m)\) is the maximum number of atomically curved unordered pairs among \(m\) reversible laws.

The clique threshold satisfies

\[
\boxed{
H(n)
=
\max
\left\{
m:
U_n(m)=\binom{m}{2}
\right\}.
}
\]

This formulation opens several Erdős-style questions.

## Supersaturation

For \(m>H(n)\), how many non-atomic pairs are unavoidable?

Equivalently, determine lower bounds for

\[
\binom{m}{2}-U_n(m).
\]

## Density regime

For \(m=m(n)\), determine the asymptotic density

\[
\frac{U_n(m)}{\binom{m}{2}}.
\]

## Random families

For a random subset \(\mathcal L\subseteq S_n\) of prescribed size, determine:

- the expected number of atomic pairs;
- concentration bounds;
- the threshold for the appearance of atomic-holonomy cliques.

---

# Invariant-constrained variants

Let \(G\le S_n\) be a subgroup encoding an invariant or admissibility constraint.

Define

\[
H_G
=
\max
\left\{
|\mathcal L|:
\mathcal L\subseteq G,\ 
[\sigma,\tau]\text{ is a \(3\)-cycle for all distinct }
\sigma,\tau\in\mathcal L
\right\}.
\]

Important cases include:

- Young subgroups preserving a partition of \(X_n\);
- alternating groups \(A_n\);
- cyclic, dihedral, affine, and wreath-product actions;
- automorphism groups of graphs, codes, or combinatorial designs;
- permutation groups preserving a metric or incidence structure.

A block-preserving version may force the \(3\)-cycle support to lie within one block, while more general imprimitive actions may permit curvature to propagate across block systems.

These variants connect the abstract extremal problem to invariant-constrained law switching.

---

# Reproducible exhaustive search

The following reference implementation constructs \(\mathcal G_n\) and computes its clique number using exhaustive maximal-clique enumeration.

It is intended only for small \(n\). The graph has \(n!\) vertices and naive construction requires

\[
O((n!)^2n)
\]

time.

## Requirements

```bash
python -m pip install "networkx>=3.0"
```

## Reference implementation

```python
from __future__ import annotations

from itertools import permutations
from typing import Sequence

import networkx as nx

Permutation = tuple[int, ...]


def identity(n: int) -> Permutation:
    return tuple(range(n))


def compose(left: Permutation, right: Permutation) -> Permutation:
    """
    Return left composed with right, so
    (left * right)(x) = left(right(x)).
    """
    if len(left) != len(right):
        raise ValueError("Permutations must have the same degree.")
    return tuple(left[right[i]] for i in range(len(left)))


def inverse(p: Permutation) -> Permutation:
    result = [0] * len(p)
    for i, image in enumerate(p):
        result[image] = i
    return tuple(result)


def commutator(sigma: Permutation, tau: Permutation) -> Permutation:
    """
    [sigma, tau] = sigma tau sigma^{-1} tau^{-1}.
    """
    return compose(
        compose(
            compose(sigma, tau),
            inverse(sigma),
        ),
        inverse(tau),
    )


def is_three_cycle(p: Permutation) -> bool:
    moved = [i for i, image in enumerate(p) if image != i]
    if len(moved) != 3:
        return False

    p_squared = compose(p, p)
    p_cubed = compose(p_squared, p)
    return p_cubed == identity(len(p))


def atomic_holonomy_graph(n: int) -> tuple[list[Permutation], nx.Graph]:
    if n < 1:
        raise ValueError("n must be positive.")

    group = list(permutations(range(n)))
    graph = nx.Graph()
    graph.add_nodes_from(range(len(group)))

    inverses = [inverse(p) for p in group]

    for i, sigma in enumerate(group):
        for j in range(i + 1, len(group)):
            tau = group[j]

            value = compose(
                compose(
                    compose(sigma, tau),
                    inverses[i],
                ),
                inverses[j],
            )

            if is_three_cycle(value):
                graph.add_edge(i, j)

    return group, graph


def maximum_atomic_family(n: int) -> list[Permutation]:
    group, graph = atomic_holonomy_graph(n)
    maximum_clique = max(nx.find_cliques(graph), key=len)
    return [group[index] for index in maximum_clique]


def verify_family(family: Sequence[Permutation]) -> None:
    for i, sigma in enumerate(family):
        for tau in family[i + 1 :]:
            if not is_three_cycle(commutator(sigma, tau)):
                raise AssertionError(
                    f"Non-atomic pair found: {sigma=}, {tau=}."
                )


def main() -> None:
    for n in range(3, 7):
        family = maximum_atomic_family(n)
        verify_family(family)
        print(f"H({n}) = {len(family)}")


if __name__ == "__main__":
    main()
```

## Expected output

```text
H(3) = 4
H(4) = 4
H(5) = 7
H(6) = 9
```

## Reproducibility warning

`networkx.find_cliques` enumerates maximal cliques. Taking the largest returned clique is exact only when the enumeration completes.

For larger \(n\), a serious exact computation should use:

- conjugacy and centralizer reductions;
- bitset graph representations;
- branch-and-bound maximum-clique solvers;
- SAT, CP-SAT, or integer-programming encodings;
- independently checkable clique and coloring certificates;
- canonical augmentation to avoid equivalent searches.

---

# Connection to existing permutation literature

Pairs of permutations with a \(3\)-cycle commutator have been studied before.

In particular, David Zmiaikou studied

\[
B(n)
=
\left\{
(\sigma,\tau)\in S_n^2:
[\sigma,\tau]\text{ is a \(3\)-cycle}
\right\}
\]

and derived counting formulas related to generation of \(S_n\) and \(A_n\).

The problem in this repository is different:

\[
\boxed{
\text{maximize the size of a family for which every pair lies in }B(n).
}
\]

In graph language, previous pair-counting work studies the edge set globally, while this project studies the maximum clique and related extremal functions.

A complete literature-priority search has **not** yet been completed. The exact function \(H(n)\) should therefore be described as a proposed problem formulation, not as a certified first occurrence in all mathematical literature.

---

# Quantum-measurement research program

The finite permutation problem is mathematically self-contained. It does not require any physical interpretation.

The repository also explores a separate conjectural bridge:

\[
\text{noncommuting reversible laws}
\longleftrightarrow
\text{curvature or holonomy in representation-law space}.
\]

The physics program is called **HyperMorphic Curvature-Activated Representation Locking** (HCARL).

## 1. Full Hilbert space

The proposed measurement model uses

\[
\mathcal H
=
\mathcal H_S
\otimes
\mathcal H_A
\otimes
\mathcal H_E
\otimes
\mathcal H_L,
\]

where the factors represent:

- the measured system;
- the apparatus;
- the environment;
- a register encoding the active representation law.

Measurement begins with ordinary unitary premeasurement:

\[
|\psi\rangle|A_0\rangle|E_0\rangle|L_0\rangle
\mapsto
\sum_i
\Pi_i|\psi\rangle
|A_i\rangle
|E_i\rangle
|L_i\rangle.
\]

## 2. Unitary law holonomy

For unitary laws \(G_a,G_b\), define

\[
\Omega_{ab}
=
G_aG_bG_a^\dagger G_b^\dagger.
\]

A normalized curvature exposure is

\[
c_{ab}
=
1-
\frac1d
\operatorname{Re}\operatorname{Tr}(\Omega_{ab}).
\]

For the permutation representation of an atomic \(3\)-cycle on \(n\) states,

\[
c_{\mathrm{atomic}}
=
\frac3n.
\]

## 3. Conditional locking dynamics

The candidate trajectory equation is

\[
\begin{aligned}
d|\Psi_t\rangle
={}&
\left[
-iH_t
-
\frac12
\sum_r
(A_r-\langle A_r\rangle_t)^2
\right]
|\Psi_t\rangle\,dt\\
&+
\sum_r
(A_r-\langle A_r\rangle_t)
|\Psi_t\rangle\,dW_r(t).
\end{aligned}
\]

This equation is norm preserving when the \(A_r\) are self-adjoint.

Its ensemble average has Lindblad form:

\[
\frac{d\rho}{dt}
=
-i[H,\rho]
-
\frac12
\sum_r
[A_r,[A_r,\rho]].
\]

## 4. Conditional Born-rule theorem

Let \(Q_i\) be branch projectors and suppose, during amplification,

\[
[H,Q_i]=0,
\qquad
[A_r,Q_i]=0.
\]

Write

\[
A_rQ_i=a_{ri}Q_i
\]

and

\[
p_i(t)=\langle\Psi_t|Q_i|\Psi_t\rangle.
\]

Then Itô calculus gives

\[
dp_i
=
2p_i
\sum_r
(a_{ri}-\bar a_r)dW_r,
\qquad
\bar a_r=\sum_jp_ja_{rj}.
\]

Thus each \(p_i(t)\) is a bounded martingale:

\[
\mathbb E[p_i(t)]=p_i(0).
\]

If persistent branch distinguishability implies almost-sure localization,

\[
p_i(\infty)\in\{0,1\},
\]

then

\[
\boxed{
\Pr(\text{outcome }i)=p_i(0).
}
\]

For a POVM \(\{E_i\}\),

\[
\boxed{
\Pr(i)=\operatorname{Tr}(\rho E_i).
}
\]

This is a conditional theorem: it derives the Born weights **inside the specified stochastic localization model**. It does not independently prove that nature implements that model.

## 5. Curvature-forced coupling

A later manuscript introduces a Hermitian bundle over a law manifold, with connection \(\mathcal A_\mu\) and curvature

\[
\mathcal F_{\mu\nu}
=
\partial_\mu\mathcal A_\nu
-
\partial_\nu\mathcal A_\mu
+
[\mathcal A_\mu,\mathcal A_\nu].
\]

Under the assumptions of:

- locality;
- gauge covariance;
- analyticity near flat connection;
- exact flat-law decoupling;
- lowest-derivative leading order;
- an available protocol bivector \(\Sigma^{\mu\nu}\);

the proposed leading Hermitian coupling has the form

\[
\boxed{
L_r
=
g_r\,i\rho_*(\mathcal F_{\mu\nu})
\Sigma_r^{\mu\nu}
+
O(\mathcal F^2).
}
\]

This result is only as strong as its assumptions. Additional local tensors, nonanalytic interactions, higher derivatives, or different field content can permit other couplings.

## 6. Microscopic field dilation

The proposed microscopic Hamiltonian is

\[
H_{\mathrm{tot}}
=
H_{\mathrm{SAL}}
+
H_B
+
\epsilon
\sum_r
\widetilde K_r\otimes B_r.
\]

The bath spectrum determines

\[
\Gamma_{rs}(\omega)
=
\epsilon^2
\int_{-\infty}^{\infty}
e^{i\omega t}
\langle B_r(t)B_s(0)\rangle\,dt.
\]

Diagonalizing the positive rate matrix produces the effective localization operators.

A quantum-filtering construction then defines the innovation process

\[
dW_\alpha
=
dY_\alpha
-
2\langle A_\alpha\rangle_tdt.
\]

In this route, the Wiener noise is not an unrelated random term: it is the unpredictable part of a conditioned field-output record.

## 7. Remaining ontology condition

A unitary system–field dilation plus conditioning does not, by itself, establish that only one branch is objectively real.

For an objective single-outcome theory, the repository proposes the additional statement:

\[
\boxed{
\text{exactly one commuting law-field output history is physically actual.}
}
\]

This is an ontological postulate and must be stated openly.

---

# Candidate experimental signature

The proposed differentiating test is a **curved-loop reversal experiment**.

Prepare

\[
|+\rangle
=
\frac{|0\rangle+|1\rangle}{\sqrt2}.
\]

Apply a noncommuting law loop

\[
\Omega
=
G_1G_2G_1^\dagger G_2^\dagger
\]

and then apply \(\Omega^\dagger\), so that the net ideal unitary is

\[
\Omega^\dagger\Omega=I.
\]

Ideal closed-system quantum mechanics predicts complete recovery.

The proposed HyperMorphic contribution predicts an additional coherence factor

\[
\frac{V_{\mathrm{HCARL}}}{V_{\mathrm{control}}}
=
e^{-D},
\]

with

\[
D
=
\frac12
\int_0^T
\sum_r
(a_{r0}-a_{r1})^2dt.
\]

For a small signed loop area \(s\), the curvature model predicts, at leading order,

\[
\boxed{
-\ln
\frac{V(s)}{V(0)}
=
\kappa s^2+O(s^3).
}
\]

The key discriminants are proposed to be:

\[
D(+s)=D(-s)+O(s^3)
\]

and

\[
D(2s)=4D(s)+O(s^3).
\]

A credible experiment must match the curved and flat controls for:

- total duration;
- gate count;
- pulse power;
- dynamical phase;
- ordinary noise filter function;
- leakage;
- calibration drift;
- control-path length.

A residual deficit is not evidence for HCARL unless conventional decoherence and coherent-control errors are quantitatively excluded.

---

# Repository structure

Current top-level files:

```text
.
├── README.md
├── The HyperMorphic Atomic-Holonomy Problem
├── HyperMorphic-Curvature-Activated-Representation-Locking
├── Curvature-Forced HyperMorphic-Measurement-Dynamics
└── Covariant-HyperMorphic-Law-Field-Theory
```

## Documents

### [`The HyperMorphic Atomic-Holonomy Problem`](./The%20HyperMorphic%20Atomic-Holonomy%20Problem)

Introduces:

- the extremal function \(H(n)\);
- atomic \(3\)-cycle commutators;
- the star-family lower bound;
- small exact values;
- the linear-growth conjecture;
- the pair-density function \(U_n(m)\).

### [`HyperMorphic-Curvature-Activated-Representation-Locking`](./HyperMorphic-Curvature-Activated-Representation-Locking)

Develops the initial nonrelativistic measurement model:

- full Hilbert-space formulation;
- stochastic locking dynamics;
- norm preservation;
- martingale Born-rule argument;
- POVM extension;
- Lindblad ensemble equation;
- reversal-visibility prediction.

### [`Curvature-Forced HyperMorphic-Measurement-Dynamics`](./Curvature-Forced%20HyperMorphic-Measurement-Dynamics)

Attempts to derive the locking operators from law-space curvature:

- Hermitian bundle and connection;
- curvature observable;
- conditional leading-coupling theorem;
- microscopic field coupling;
- bath-derived rate matrix;
- quantum filtering and innovation noise;
- pointer sectors and Born-rule localization.

### [`Covariant-HyperMorphic-Law-Field-Theory`](./Covariant-HyperMorphic-Law-Field-Theory)

Reserved for the covariant effective field theory that should specify:

- the law-space gauge field;
- its curvature;
- the law-amplitude field;
- apparatus coupling;
- field quantization;
- Wightman and influence kernels;
- the derived spectral matrix \(\Gamma_{rs}(\omega)\);
- stability, conservation, and flat-limit conditions.

At the time this README was prepared, this file is a placeholder and must be populated before the covariant theory can be considered part of the repository record.

---

# Recommended repository reorganization

A more maintainable structure would be:

```text
.
├── README.md
├── LICENSE
├── CITATION.cff
├── pyproject.toml
├── docs/
│   ├── atomic_holonomy_problem.md
│   ├── hcar_locking.md
│   ├── curvature_forced_dynamics.md
│   └── covariant_law_field_theory.md
├── src/
│   └── atomic_holonomy/
│       ├── __init__.py
│       ├── permutations.py
│       ├── graph.py
│       └── exact_search.py
├── tests/
│   ├── test_commutator.py
│   ├── test_star_family.py
│   └── test_small_n.py
├── results/
│   ├── exact_values.json
│   └── certificates/
└── notebooks/
    └── atomic_holonomy_experiments.ipynb
```

File names ending in `.md` will render more reliably on GitHub than extensionless manuscript files.

---

# Research roadmap

## Phase I — Make the finite problem reproducible

- [ ] Commit the exact enumeration code.
- [ ] Add tests for permutation composition and commutators.
- [ ] Store explicit maximum clique certificates.
- [ ] Store independently checkable upper-bound certificates.
- [ ] Record hardware, runtime, package versions, and solver settings.
- [ ] Verify \(H(n)\) with at least two independent implementations.
- [ ] Attempt \(n=7\) using symmetry reduction and a dedicated clique solver.

## Phase II — Structural mathematics

- [ ] Derive degree formulas in \(\mathcal G_n\) by conjugacy type.
- [ ] Characterize common neighborhoods.
- [ ] Classify maximal cliques for \(n\le6\).
- [ ] Prove nontrivial upper bounds for \(H(n)\).
- [ ] Study support-intersection constraints.
- [ ] Develop spectral, representation-theoretic, and flag-algebra bounds.
- [ ] Determine \(U_n(m)\) in initial regimes.
- [ ] Prove or disprove \(H(n)=\Theta(n)\).

## Phase III — Formal verification

- [ ] Formalize permutations, sign, support, and commutators in Lean.
- [ ] Prove that all commutators in \(S_n\) are even.
- [ ] Prove the \(3\)-point minimal-support lemma.
- [ ] Prove the star-family lower bound.
- [ ] Import computational certificates for small \(n\).

## Phase IV — Measurement-model rigor

- [ ] State the probability space and filtration precisely.
- [ ] Prove existence and uniqueness of the stochastic trajectory.
- [ ] Prove almost-sure localization under explicit hypotheses.
- [ ] Separate conditional quantum trajectories from objective-collapse ontology.
- [ ] Derive energy-transfer bounds.
- [ ] Prove no-signalling at the ensemble level under local couplings.
- [ ] Compare quantitatively with decoherence, CSL, GRW, and continuous-measurement models.

## Phase V — Covariant field theory

- [ ] Add the full covariant action manuscript.
- [ ] Fix gauge, identify constraints, and count physical degrees of freedom.
- [ ] Prove absence of ghosts around specified backgrounds.
- [ ] Derive the retarded and noise kernels.
- [ ] Determine when a Markov limit exists.
- [ ] Address vacuum excitation and energy production.
- [ ] Establish microcausality or state the exact causal limitation.
- [ ] Derive experimentally usable parameter bounds.

## Phase VI — Experimental protocol

- [ ] Specify a hardware-independent pulse sequence.
- [ ] Construct flat and curvature-matched control families.
- [ ] Simulate coherent errors and environmental noise.
- [ ] Pre-register the predicted \(s^2\), orientation-even scaling.
- [ ] Publish null-result bounds as well as positive results.

---

# Contribution standard

Contributions are welcome when they make a claim more rigorous, reproducible, or falsifiable.

## Mathematical contributions

A claimed new value of \(H(n)\) should include:

1. an explicit family giving the lower bound;
2. verification that every pair has a \(3\)-cycle commutator;
3. an exact upper-bound proof or certificate;
4. code and dependency versions;
5. a clear permutation-composition convention.

A claimed theorem should distinguish:

- assumptions;
- statement;
- proof;
- computational evidence;
- conjectural interpretation.

## Computational contributions

Please include:

- deterministic seeds where applicable;
- exact arithmetic where possible;
- solver name and version;
- timeout and hardware;
- raw result files;
- certificate verification code;
- tests that fail under the opposite composition convention.

## Physics contributions

Please separate:

1. ordinary quantum-mechanical identities;
2. results conditional on the proposed dynamics;
3. new physical postulates;
4. experimentally distinguishable predictions;
5. results already known from collapse or quantum-filtering literature.

Do not describe a model as solving the measurement problem merely because it reproduces the Born rule after a collapse process has been assumed.

## Negative results

Counterexamples, failed bounds, null experiments, and parameter exclusions are valuable contributions and should not be removed to preserve a preferred narrative.

---

# Citation

Until an archival paper and DOI are available, cite the repository as:

```bibtex
@misc{paul2026hypermorphicAtomicHolonomy,
  author       = {Shaun Paul},
  title        = {The HyperMorphic Atomic-Holonomy Problem},
  year         = {2026},
  howpublished = {GitHub repository},
  note         = {Extremal permutation problem and conjectural quantum-foundations program}
}
```

When citing a specific claim, cite the corresponding document and commit hash.

---

# References

## Permutation commutators

1. D. Zmiaikou, *The probability of generating the symmetric group with a commutator condition*, arXiv:1205.6718.
2. A. Vavpetič, *Commutators of cycles in permutation groups*, Ars Mathematica Contemporanea **10** (2016), 67–77.
3. P. Bader, *Commutators of \(n\)-cycles in the symmetric group*, arXiv:2509.22749.

## Quantum probability and measurement

4. A. M. Gleason, *Measures on the closed subspaces of a Hilbert space*, Journal of Mathematics and Mechanics **6** (1957), 885–893.
5. G. Lindblad, *On the generators of quantum dynamical semigroups*, Communications in Mathematical Physics **48** (1976), 119–130.
6. R. L. Hudson and K. R. Parthasarathy, *Quantum Itô's formula and stochastic evolutions*, Communications in Mathematical Physics **93** (1984), 301–323.
7. V. P. Belavkin, *Quantum continual measurements and a posteriori collapse on CCR*, Communications in Mathematical Physics **146** (1992), 611–635.
8. A. Bassi, K. Lochan, S. Satin, T. P. Singh, and H. Ulbricht, *Models of wave-function collapse, underlying theories, and experimental tests*, Reviews of Modern Physics **85** (2013), 471–527.
9. F. Wilczek and A. Zee, *Appearance of gauge structure in simple dynamical systems*, Physical Review Letters **52** (1984), 2111–2114.

These references provide context. They do not imply endorsement of the HyperMorphic interpretation.

---

# Terminology

| Term | Meaning in this repository |
|---|---|
| Law | A reversible transformation, usually a permutation or unitary |
| Recovery | Application of the inverse transformation |
| Switching holonomy | Group commutator of two reversible laws |
| Flat pair | Commuting pair |
| Curved pair | Noncommuting pair |
| Atomic curvature | \(3\)-cycle commutator in the permutation model |
| Law manifold | Parameter space of admissible representation laws |
| Representation locking | Proposed stochastic localization into a pointer sector |
| Law-field output | Proposed commuting record used in the conditional trajectory |
| HCARL | HyperMorphic Curvature-Activated Representation Locking |

The use of geometric language is exact only when an appropriate bundle, connection, and curvature have been defined. In the finite permutation problem, “curvature” is an algebraic analogy encoded by the commutator.

---

# License

A `LICENSE` file is not currently included in the repository.

Add an explicit license before inviting third parties to copy, modify, or redistribute the code and manuscripts.

---

# Contact and discussion

Use GitHub Issues for:

- proposed bounds or constructions;
- small-\(n\) computational results;
- literature references;
- proof corrections;
- reproducibility problems;
- experimental-protocol critiques.

When opening an issue, identify whether the claim is:

- proved;
- computationally verified;
- conjectured;
- physically postulated;
- experimentally tested.

---

<p align="center">
  <strong>Core question:</strong><br>
  How large can a family of reversible laws be when every pair generates exactly the smallest possible nonzero switching holonomy?
</p>
