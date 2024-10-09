# Poly-Spline Finite-Element Method

This repository contains the scripts to regenerate the figures in the paper:
> Decoupling Simulation Accuracy from Mesh Quality

```bibtex
@article{Schneider:2019:PFM,
 author = {Schneider, Teseo and Dumas, J{\'e}r{\'e}mie and Gao, Xifeng and Botsch, Mario and Panozzo, Daniele and Zorin, Denis},
 title = {Poly-Spline Finite-Element Method},
 journal = {ACM Transactions on Graphics},
 month = {3},
 number = {3},
 pages = {19:1--19:16},
 publisher = {Association for Computing Machinery (ACM)},
 volume = {38},
 year = {2019},
}
```

This branch contains updated scripts. For the original check the [original](https://github.com/polyfem/Poly-Spline-Finite-Element-Method/tree/original) branch.


# CPP installation

First clone the polyfem repository:

```bash
git clone https://github.com/polyfem/polyfem.git
```

and follow the instructions to compile it.

**Note** the examples in the paper use Padiso which requires a licence. It is free for academia or can be obtained trough MKL. This is however not necessary to reproduce the data.

**Note** if you have Pardiso installed, remove `"solver_type": "Eigen::UmfPackLU",` from the JSON file to fallback to the default Pardiso solver.

then run Polyfem with
```bash
./PolyFEM_bin --json <path to the json> --cmd
```
You can then see the *solution.vtu* using Paraview.

# Dependencies

## PolyFEM

All figures where generated with [PolyFEM](https://github.com/polyfem/polyfem). Refer to the [turorial](https://polyfem.github.io/tutorial/) and the [JSON api](https://polyfem.github.io/documentation/) for details.

Make sure that [PARDISO](https://panua.ch) is found and enabled, otherwise you might not be able to generate certain figures (see below). In PolyFEM, `FindPardiso.cmake` will look for the PARDISO library in `~/.local` or `~/.pardiso`. If you installed PARDISO in a different location, you may need to update this file accordingly.

## Solver

As stated in the paper, we use [PARDISO](https://panua.ch) for the all figures.

If you use the python version (or don't have PARDISO), polyfem will fallback to the algebraic multigrid solver [HYPRE](https://computing.llnl.gov/projects/hypre-scalable-linear-solvers-multigrid-methods).

If you try to generate the any figure with an iterative solver, running times may be exceedingly long, so it is not recommended.


# Data

The 2D mesh dataset can be found [here](https://drive.google.com/drive/folders/11KpI297PzSnArLTbZH_3UWjAytf020Ct?usp=sharing), the 3D hybrid meshes can be found [here](https://drive.google.com/drive/folders/14DmCBjiEQ-LeupLA1VOdbV87UP1lXsLA?usp=sharing), and the 3D pure hex [here](https://drive.google.com/drive/folders/1xLWq2fmsE8tc1lHkjTrftaHVMu0qEido?usp=sharing).

Smaller meshes used for the convergence plot can be downloaded [here](https://drive.google.com/drive/folders/1s23XhO5nKbTGMFm6D__lak5DMXSdAOpd?usp=sharing).
