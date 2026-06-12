---
title: "Shared memory segments in Fortran (gfortran)"
date: 2010-08-27
forum: Programming Talk
---

### Post by jtappin on 2010-08-27
This is probably a long shot, but does anybody know of a way to handle shared memory segments in fortran without needing to use the fixed address hack described on gfortran.org?

The particular problem is a modelling code (currently in IDL [Interactive Data Language]) that needs to run multiple instances to check convergence consistency, however there is a read-only look-up table of about 4GB in size. Currently both the driver/controller and the code that runs the individual instances are in IDL (albeit with some external calls to fortran code for speed), but I'd like to convert the instances to fortran, but they would need to be able to access the shared look up table produced by the driver code.

---

