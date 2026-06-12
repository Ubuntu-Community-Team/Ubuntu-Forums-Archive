---
title: "Replacing Simulink Algebraic Constraint with user-defined solver"
date: 2010-03-17
forum: Programming Talk
---

### Post by imbuto on 2010-03-17
Hi all,

I am having troubles with the Algebraic Constraint solver (I've got some algebraic loop which I cannot eliminate, and which seem to be too hard for the solver to handle) so I would like to replace the solver with a solver of my own (e.g. implemented as Level-2 function).

How can I accomplish that? That is, I know how to write a Level-2 function which takes some input and gives some output for the given time step, but how can I say: "Hey, take some input and give some output until the solver converged, than take the output as timestep output"?.

Sorry if it sounds vague, but I'm not that familiar with Simulink... I'm searching the web for examples, but I couldn't find any so far.

Thanks in advance!

---

