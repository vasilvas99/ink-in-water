# Ink In Water Solver


A toy project to experiment with NG Solve.

![Paraview image](assets/img.png)

The system we are solving is:

$$
\bar u = (u , v)
$$

$$
\partial_t u + \bar u \cdot \nabla u  - \nu \nabla^2 u + \partial_x p = 0
$$
$$
\partial v + \bar u \cdot v -\nu \nabla^2 v + \partial_y p + \beta g c = 0
$$
$$
\nabla \cdot \bar u = 0
$$
$$
\partial c +  \bar u \cdot \nabla c - D \nabla c - \nabla \cdot [ \delta_{\mathcal K} \bar u (\bar u \cdot c) ]  = 0
$$

on $\Omega  = (-10, 10)^2$.

Subject to:

$$
\frac{\partial c}{\partial n} = 0
$$

$$
u = 0 \quad v = 0
$$

on $\partial \Omega$

I.e. $\Omega \cup \partial \Omega = [-10, 10]^2$ a simple square.

$$
u(0, x, y) = v(0, x, y) = 0
$$

$$
c(0, x, y) = c_0(x,y) = e^{-\frac{x^2 + (y-5)^2}{5}}
$$

Therefore this is a Navier-Stokes system, coupled to a diffusion of a Gaussian hill ("ink drop") with a SUPG-like stabilization
of the strong advection in the Boussinesq approximation

Runs reasonably fast, but loses stability on vortex formation.