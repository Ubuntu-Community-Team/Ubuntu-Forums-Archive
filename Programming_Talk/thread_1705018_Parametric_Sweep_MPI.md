---
title: "Parametric Sweep MPI"
date: 2011-03-11
forum: Programming Talk
---

### Post by andradx on 2011-03-11
Hey there!


Just for context:

Until recently I had a workstation for parallel programming using the CUDA framework, but because the PCI bus is shared among devices my four GPU workstation rendered useless for multiple GPU programming. For some applications might not be, but for the simulations I'm running multiple GPUs are a nuisance instead of an advantage.

Yesterday I was granted access to an eight blade workstation with sixteen GPUs. The system is running CentOS and programs can be executed locally on each node or submitted to a top system that dispatches the jobs using MPI.

I have a question regarding a parametric sweep, ie spawning the same programme on all nodes, but with different command line arguments for every one of them.


When I submit the job I input a command like this:

mpirun -prefix /opt/openmpi/1.4.2/ -machinefile <nodes_id> -np X -nolocal <executable> <argv[1]> <argv[2]> ... <argv[N-1]>

Which spawns on X nodes listed in nodes_id the programme executable with argument list argv[1] argv[2] etc.

(nodes_id is a simple text file with the nodes name on which the programme is to be run)


My question is, is there a flag like -argumentlist <argument_list_file>, where argument_list_file is like
0 1 2
3 4 5

so that on node node_id0 programme executes w/ args 0 1 2 and on node_id1 it w/ 3 4 5???


Though not allowed to be typed in the forums, I'm aware that (a combination of)read the manual is possibly the best answer. However, if anyone is able to provide me an answer I'll be able to postpone reading the manual and have my simulation results faster.

Thank you.

---

### Post by talonmies on 2011-03-12
You might be able to use the OpenMPI application context mechanism to do what you want. It is primarily intended for doing MIMD style executions, but will probably work when the application is the same, but the arguments are different.

PS: If you want to ask a question about MPI, you really ought to state which MPI flavour you are using, because they all differ greatly when it comes to stuff not covered by the standard (and this sort of thing is definitely not).

---

### Post by andradx on 2011-03-12
I didn't know that. System's running openMPI. 


(The right nomenclature is parameter sweep, isn't it?!:-\")


[edit] I read the mpirun manpage and noticed there's the --app flag which can be used to specify an application context, upon which all command line arguments for my executable are discarded. I'm still looking for how to write the application context though.

---

### Post by andradx on 2011-03-13
I forgot that to run an mpi job I had to do something like:

mpirun -prefix <path_to_mpi_on_node> -machinefile <path_to_machinefile> -np 2 -nolocal executable


So when I ran :

mpirun -f appfile

-prefix was not specified and the job failed.

I'm now able to launch MPMD jobs.

---

