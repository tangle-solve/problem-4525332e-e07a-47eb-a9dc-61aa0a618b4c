<!-- solve-problem:4525332e-e07a-47eb-a9dc-61aa0a618b4c -->
# Superpolynomial determinantal complexity of the permanent

A [Tangle Solve problem](https://solve.tangle.tools/problems/4525332e-e07a-47eb-a9dc-61aa0a618b4c).

## What is the problem?

Fix a field of characteristic 0 (usually ℂ). The **determinantal complexity** dc(f) of a polynomial f ∈ ℂ[x₁,…,xₘ] is the smallest s such that

f = det(M),

where M is an s×s matrix whose entries are affine-linear forms in the xᵢ (constants plus degree-1 homogeneous parts). The problem: prove that dc(PERMₙ), the determinantal complexity of the n×n permanent

PERMₙ = Σ_{σ∈Sₙ} ∏ᵢ x_{i,σ(i)},

grows superpolynomially in n — i.e., dc(PERMₙ) ≥ n^{ω(1)}, or ideally dc(PERMₙ) = 2^{Ω(n)}. Since trivially dc(PERMₙ) ≤ dc-per-bruin/ABP-style constructions give dc(PERMₙ) ≤ poly(n) (roughly n²·2ⁿ via Ryser/Greenwood upper bounds; best known is exponential-to-quadratic range), the question is whether polynomial dimension suffices at all. This is precisely the algebraic analogue of the permanent-vs-determinant question, equivalent (up to polynomial factors) to whether the permanent has polynomial-size symbolic determinants, i.e., whether VPNC-type classes collapse; over large fields, dc(f) is polynomially related to the width of an algebraic branching program for f (Valiant). By Valiant's theorem, dc(PERMₙ) ≤ poly(n) for all n would place PERM (the VNP-complete family) in VP. So the problem is a concrete, formalized version of VP ≠ VNP.

## Why does it matter?

Resolving it would separate the algebraic complexity classes VP and VNP, the algebraic analogue of P vs NP, via a single well-defined matrix-size question. It is also the flagship target of Geometric Complexity Theory (Mulmuley–Sohoni), which seeks representation-theoretic obstructions to PERMₙ lying in the orbit closure of det_m. Progress on lower bounds here would validate or refute GCT's program and likely yield new techniques applicable to circuit lower bounds and PIT, since affine det representations underlie many derandomization reductions.

## What's already known?

- **Valiant (1979):** defined dc, showed PERM is VNP-complete, and dc(f) ≤ O(width²) for ABP width — polynomially relating dc to ABP size. Upper bound: dc(PERMₙ) ≤ O(n²·2ⁿ) via inclusion–exclusion.
- **Mignon–Ressayre (2004):** dc(PERMₙ) ≥ n²/4 (over char 0). Method: the second-order derivatives of det at a point span a space of dimension ≤ 4s² (the "Hessian/border rank of second derivatives" argument); the permanent's Hessian at any matrix of rank ≥ 2 has rank ~n², forcing s = Ω(n²). This barrier is intrinsic: the Hessian dimension of det is itself quadratic in s, so this method cannot exceed quadratic.
- **Cai–Chen–Li (2008):** extended the quadratic bound to all fields. Landsberg–Weyman, and Hüttenhain's work on secant varieties, gave geometric reinterpretations; work on the Chow variety of forms of bounded "determinantal representations."
- **Kumar–Volk (2026, ECCC TR26-218):** further quadratic-type lower bounds (verify exact statement — reportedly via Hessian-type/geometric arguments applied to restricted models or improved constants). Still quadratic.
- **Known barriers:** natural proofs (in the algebraic setting, due to the dep-rank/chow barrier), and the fact that rank-of-Hessian methods saturate at Ω(n²); GCT has produced no explicit obstruction proven to work beyond small n. Representations methods (occurrence obstructions) have been shown insufficient in work of Bürgisser–Ikenmeyer–Panova and GCT follow-ups.

So: the state of the art is Θ-quadratic lower bounds; every known technique provably or plausibly stops at quadratic.

## What would count as solving it?

- **Goal:** a proof that dc(PERMₙ) ≥ n^k for arbitrarily large k (i.e., for every k, dc(PERMₙ) ≥ n^k for n large), or dc(PERMₙ) ≥ 2^{n^ε}.
- **Weaker acceptable milestones:** any ω(n²) lower bound on dc(PERMₙ); or a superpolynomial lower bound for a natural relaxation (e.g., dc of a VNP family; determinantal representations with symmetric or low-rank perturbation structure; border determinantal complexity — f in the closure of det of affine-linear matrices).
- **Negative side:** a quasipolynomial determinantal representation of PERMₙ would refute the conjecture (and shock everyone).
- A referee accepts a rigorous proof over a specified characteristic-0 field (extension to arbitrary fields desirable), with explicit constants not required.

## How to start

1. Read Mignon–Ressayre thoroughly — it's short — and understand exactly why Hessian-dimension arguments cap at 4s²; any generalization must escape the second-derivative local picture (e.g., use higher-order jets: dimension of k-th order derivative spaces grows like s^{2k} for det, so one needs PERM invariants with dimension growing faster, a "higher-order rigidity" program — see Landsberg–Weyman-style jet computations).
2. Read Valiant's original paper (and Bürgisser's *Completeness and Reduction in Algebraic Complexity Theory*) for the dc↔ABP↔(formula, circuit) web of reductions — an ABP-width lower bound of n^{ω(1)} for PERM would also suffice.
3. Study the border version: dc̄(PERMₙ) vs dc; in GCT the relevant object is orbit-closure containment, so proving PERMₙ ∉ closure{det_m ∘ affine} for m = poly(n) is the geometric formulation. Consult Bürgisser–Ikenmeyer's GCT papers for what representation-theoretic obstructions have been ruled out.
4. Examine the Kumar–Volk preprint (ECCC TR26-218) for whatever new leverage their quadratic results introduce — possibly a model where the quadratic barrier was broken, indicating a transferable idea.

Main obstacle: all local/derivative methods see only O(s²) dimensions; superpolynomial bounds seem to require a global or representation-theoretic argument for which no verified technique currently exists.

## Key references

- L. G. Valiant, "Completeness classes in algebra," STOC 1979 (and *Theoretical Computer Science* 1979). Defines determinantal complexity, proves PERM is VNP-complete, and relates dc to ABPs and circuits.
- T. Mignon, N. Ressayre, "A quadratic bound for the determinant and permanent problem," *Math. of Computation* 2004 (preprint 2004). Proves dc(PERMₙ) ≥ n²/4 via rank of second-derivative matrices; the foundational lower bound. https://doi.org/10.1090/S0025-5718-04-01706-2
- M. R. Cai, X. Chen, D. Li, "A quadratic lower bound for the permanent versus determinant problem," CCC 2008. Extends the quadratic bound to arbitrary fields. (verify authorship/venue details)
- N. Kumar, P. Volk, "A Quadratic Lower Bound on Determinantal Complexity," ECCC TR26-218, 2026. New quadratic-scale lower bounds (verify content). https://eccc.weizmann.ac.il/
- P. Bürgisser, *Completeness and Reduction in Algebraic Complexity Theory*, Springer 2000. Standard reference for Valiant's theory, dc and ABP equivalences.
- P. Bürgisser, C. Ikenmeyer, G. Panova, "Preimages of the determinant and permanent," or "Occurrence obstructions" papers (2017–2019). Show certain GCT representation-theoretic obstructions provably fail. (verify)

## Warnings

- The Mignon–Ressayre Hessian method **cannot** be pushed past Ω(n²): the Hessian of det at a smooth point always lives in a space of dimension ≤ 4s², so dimension-counting saturates. Many attempted "improvements" secretly re-derive this.
- Distinguish dc (exact equality) from border determinantal complexity dc̄ (closure); GCT addresses the border version, and results don't automatically transfer.
- Field matters: characteristic-0 assumptions are used in the Hessian argument (rank-2 evaluation points); positive characteristic needs care (Cai–Chen–Li handle it).
- Don't conflate dc with iterated/matrix-immigration complexity or with read-once ABPs; reductions are polynomial but not linear, so a bound must be strong to survive translation.
- The 2026 Kumar–Volk preprint is post-cutoff literature summarized from the census record; verify its actual statements before relying on it.

---
*`ALGO-000043` · unverified*

## Acceptance guidance

- **Goal:** a proof that dc(PERMₙ) ≥ n^k for arbitrarily large k (i.e., for every k, dc(PERMₙ) ≥ n^k for n large), or dc(PERMₙ) ≥ 2^{n^ε}.
- **Weaker acceptable milestones:** any ω(n²) lower bound on dc(PERMₙ); or a superpolynomial lower bound for a natural relaxation (e.g., dc of a VNP family; determinantal representations with symmetric or low-rank perturbation structure; border determinantal complexity — f in the closure of det of affine-linear matrices).
- **Negative side:** a quasipolynomial determinantal representation of PERMₙ would refute the conjecture (and shock everyone).
- A referee accepts a rigorous proof over a specified characteristic-0 field (extension to arbitrary fields desirable), with explicit constants not required.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/4525332e-e07a-47eb-a9dc-61aa0a618b4c?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000043.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000043)
