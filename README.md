Custom OpenFOAM solver and wall boundary condition for reactive scalar transport.

Components
1- reactiveScalarTransportFoam (Solver)
A custom scalar transport solver that computes advection–diffusion–reaction of a scalar field in the fluid domain. 
It advances the scalar field in time while accounting for bulk transport and any volumetric reaction terms. 
The solver follows standard OpenFOAM structure and integrates directly with custom boundary conditions.

2- reactiveWallFlux (Boundary Condition)
A flux-based scalar wall boundary condition that imposes a reaction-controlled normal flux at solid surfaces.
Instead of prescribing a fixed concentration, the boundary computes the wall flux based on a kinetic parameter k, allowing modeling of surface reaction rates coupled to transport.
It is specified in the field file (e.g., 0/T) as:
patch
{
    type    reactiveWallFlux;
    k       0.01;        // reaction rate
    value   uniform 0;   // initial patch value
}

The solver and boundary condition compile using wmake and follow standard OpenFOAM conventions.
