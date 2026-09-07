# Cruise Control Simulation (MATLAB/Simulink)

A closed-loop PID control system simulating a vehicle's cruise control,
built to demonstrate three core control behaviors: reference tracking,
response to a setpoint change, and disturbance rejection.

## System Diagram

## What It Demonstrates

1. **Speed Tracking** — Target speed is set to 60 km/h at t=0s; the vehicle's
   actual speed rises and settles at 60 km/h.
2. **Setpoint Change** — Target speed jumps to 80 km/h at t=30s; the vehicle
   tracks the new target and settles at 80 km/h.
3. **Disturbance Rejection** — A simulated uphill grade (disturbance) is
   introduced at t=50s, causing a temporary dip in speed. The PID controller
   compensates and returns the vehicle to 80 km/h.

## Result

![Cruise Control Response](cruise_control_result.png)

*Red dashed line: Target Speed. Blue solid line: Actual Speed.*

## Controller Design

- Controller type: PI(D) — Proportional-Integral control
- Gains: P = 5, I = 5, D = 0
- Vehicle plant modeled as a simplified first-order transfer function
  (mass/drag lumped together): `1 / (5s + 1)`
- Tuned for a fast response with minor overshoot using Simulink's
  built-in PID Tuner

## Tools Used

- MATLAB / Simulink (Online)
- Blocks used: Step, Sum, PID Controller, Transfer Fcn, Mux, Scope,
  To Workspace

## How to Run

1. Open `cruise_control_sim.slx` in Simulink
2. Set Stop Time to 80 seconds
3. Click Run
4. Double-click the Scope block to view the response, or use the
   `To Workspace` outputs (`out.simout`, `out.simout1`) with MATLAB's
   `plot()` function for a cleaner graph

## Possible Extensions

- Replace the simplified transfer-function plant with a more detailed
  vehicle dynamics model
- Compare PID performance against a PWM-based motor control strategy
- Extend to a full EV powertrain model integrating motor and battery
  dynamics

