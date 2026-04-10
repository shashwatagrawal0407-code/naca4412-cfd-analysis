# NACA 4412 Aerofoil CFD Analysis (ANSYS Fluent)
 A 2D Computational Fluid Dynamics (CFD) analysis of a NACA 4412 aerofoil to evaluate aerodynamic performance using ANSYS Fluent.

## Overview

This project performs a steady-state 2D CFD analysis of a NACA 4412 aerofoil at multiple angles of attack (AoA).

The objective was to evaluate:

* Lift coefficient (Cl)
* Drag coefficient (Cd)
* Aerodynamic polar curves (Cl vs AoA, Cd vs AoA)

This type of analysis is widely used in aircraft design, UAV development, and wind turbine optimization.

## Tools & Software

* ANSYS Workbench 2026 R1 (Student Edition)
* ANSYS Fluent
* SpaceClaim (Python scripting for geometry)

### Methodology

## Flow Setup

* Analysis Type: 2D steady-state external flow
* Fluid: Air (ρ = 1.225 kg/m³, μ = 1.7894×10⁻⁵ Pa·s)
* Freestream Velocity: 15 m/s
* Reynolds Number: ~1,000,000

## Turbulence Model

* k-ω SST model

  * k-ω near wall → accurate boundary layer capture
  * k-ε in freestream → stable outer flow

### Geometry & Domain

* Aerofoil: NACA 4412
* Chord Length: 1.0 m
* Domain size:

  * 10c upstream
  * 20c downstream
  * 10c top and bottom

### Mesh

* Global element size: 50 mm
* Inflation layers: 3
* Growth rate: 1.2
* Quad-dominant mesh

### Boundary Conditions

* Inlet: Velocity inlet (Vx, Vy based on AoA)
* Outlet: Pressure outlet (0 Pa)
* Top/Bottom: Symmetry
* Aerofoil: No-slip wall

## Results — Aerodynamic Performance

| AoA (°) | Cl     | Cd     | L/D   |
| ------- | ------ | ------ | ----- |
| -4      | 1.0874 | 0.0537 | 20.25 |
| 0       | 1.1741 | 0.0547 | 21.46 |
| +4      | 1.2489 | 0.0554 | 22.54 |
| +8      | 1.3162 | 0.0556 | 23.67 |
| +12     | 1.3775 | 0.0557 | 24.73 |


## Key Observations

* Cl increases consistently with AoA — physically correct for a cambered aerofoil
* Cd increases gradually due to increased pressure drag
* L/D ratio improves with AoA and peaks at 12°
* Positive Cl even at -4° due to camber
* No stall observed within tested range


### Flow Visualisation

## Velocity Contour

* High velocity observed on upper surface
* Indicates low pressure region → lift generation

## Pressure Contour

* Low pressure on upper surface
* High pressure on lower surface
* Maximum pressure difference near leading edge

## Velocity Vectors

* Flow acceleration over upper surface
* Downwash visible behind trailing edge

## Convergence

* Residuals reduced by 3–4 orders of magnitude
* Lift and drag coefficients converged to stable values
* All simulations completed in ~200 iterations


## Key Learnings

* Cambered aerofoils generate lift even at negative AoA
* Proper AoA implementation is critical for correct results
* Boundary layer resolution is important for accuracy
* Mesh and domain size significantly affect CFD results


## Challenges Faced

* Incorrect Cl trend due to sign error in velocity components
* SpaceClaim scripting issues with .NET data types
* Mesh size limitations due to student license
* Geometry setup issues (2D vs 3D interpretation)


## Angle of Attack Implementation

Instead of rotating geometry, AoA was simulated by decomposing inlet velocity:

* Vx = V · cos(α)
* Vy = V · sin(α)

This approach avoids remeshing and ensures consistent mesh quality.


## Applications

* Aircraft wing design
* UAV aerodynamic analysis
* Wind turbine blade optimization
* Motorsport aerodynamics


## Project Files

* Detailed CFD report (PDF)
* Simulation result images
  

## 🚀 Future Work

* Extend analysis to higher AoA to capture stall
* Perform transient simulations
* Validate results with experimental data

