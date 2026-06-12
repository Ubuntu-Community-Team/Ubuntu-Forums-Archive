---
title: "OpenMPI Throwing Nonreproducible Errors"
date: 2012-07-03
forum: Programming Talk
---

### Post by dingidforrester on 2012-07-03
Hi all,

I'm fairly new to MPI, and polishing someone else's existing MPI application (odd distribution of work, I know) that solves fluid dynamics and nonlocal transfer problems simultaneously. I'm getting strange results that I haven't been able to resolve or make much headway on by browsing the internet. Here is the basic outline of the (C) program:

 - Initialize MPI, etc. and set up communicators

 - Launch fluid and nonlocal transfer time loops. One MPI process handles the fluid integrator and the rest deal with nonlocal transfer.

 - Begin loop over time. The main signal transfers are (a) a 3D array of fluid variables that the nonlocal code uses and (b) a 3D array of intensities that the fluid code uses. 

 - Cleanup and finish, but we never get here.

This time loop proceeds happily for 50 - 1000 steps or so until, randomly, I get one of the following errors, tracked with printf statements:

Culprit:
MPI_Irecv(&FLUIDVARS[0][0][0], dim1*dim2*numvars, MPI_DOUBLE, 0, 0, intercomm, &request);

Output:
[my.computer.myinstitution.edu:20374] *** An error occurred in MPI_Irecv
[my.computer.myinstitution.edu:20374] *** on communicator MPI_COMM_WORLD
[my.computer.myinstitution.edu:20374] *** MPI_ERR_COMM: invalid communicator
[my.computer.myinstitution.edu:20374] *** MPI_ERRORS_ARE_FATAL: your MPI job will now abort

Culprit:
MPI_Irecv(&FLUIDVARS[0][0][0], dim1*dim2*numvars, MPI_DOUBLE, 0, 0, intercomm, &request);

Output:
[my.computer:20393] *** Process received signal ***
[my.computer:20393] Signal: Segmentation fault: 11 (11)
[my.computer:20393] Signal code: Address not mapped (1)
[my.computer:20393] Failing at address: 0x10

I'm not really sure what to make of these, particularly since everything memory-wise works fine for a number of previous timesteps. The machine does not appear to be running out of memory (indeed, the memory addresses for FLUIDVARS and NONLOCVARS stay the same throughout the program's life). I am an MPI noob so I assume this is some generic and obvious mistake. However, I can't just post the program and don't really know what other parts could be responsible -- if there is another element of the program that would help you trace this error let me know and I will show how it works.

If it matters, I am running this on Mac OS X 10.7 via the command 'mpirun -np 3 ./foo'. Also, if myrank < nprocs - 1, the process deals with the nonlocal problem, and otherwise it deals with the fluid problem.

Thanks for any help!

DF

---

### Post by 11jmb on 2012-07-03
without looking at any code, I'd guess that your problem comes from not using the non-blocking receive safely. If that is the case, your options are either to switch from MPI_Irecv to MPI_Recv, which will block until your application buffer can be accessed. If you want to keep using non-blocking calls, you should make sure that you use MPI_Wait or MPI_Test to make sure that the application buffer is safe to use.

---

