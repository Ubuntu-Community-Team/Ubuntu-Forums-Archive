---
title: "cant run mpi program because library not found error"
date: 2018-04-17
forum: Packaging and Compiling Programs
---

### Post by sion.halim on 2018-04-17
I want to run an mpi program from my laptop into my lab's server computer via WLAN but it doesn't want to run because of this error that i can read on slurmXXX.out file:

-------------------------------------------------------
Primary job  terminated normally, but 1 process returned
a non-zero exit code.. Per user-direction, the job has been aborted.
-------------------------------------------------------
./coba2.exe: error while loading shared libraries: libmpi_mpifh.so.20: cannot open shared object file: No such file or directory

mpirun detected that one or more processes exited with non-zero status, thus causing
the job to be terminated. The first process to do so was:

  Process name: [[25487,1],0]
  Exit code:    127
--------------------------------------------------------------------------


please help... i want to run my research simulation program but it doesnt work now becausse of this error...

---

### Post by kerry_s on 2018-04-17
sudo apt install libopenmpi2

---

