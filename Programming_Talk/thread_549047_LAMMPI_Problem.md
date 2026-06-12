---
title: "LAM/MPI Problem"
date: 2007-09-12
forum: Programming Talk
---

### Post by terabite on 2007-09-12
I have installed LAM/MPI.
Now Whenever i run 'lamboot', it says:
bash: hboot: command not found.

HELP ME!!!!

---

### Post by moma on 2007-09-12
An idea,

If you can,  choose OpenMPI instead of LAM/MPI.  LAM/MPI is in maintenance mode and all development efforts are put on OpenMPI. (so say the LAM/MPI's website) 

[http://www.open-mpi.org/](http://www.open-mpi.org/)

Start synaptic and search for "openmpi" packages and install'em.

$ [COLOR="SeaGreen"]apt-cache search openmpi[/COLOR]
[INDENT][SIZE="2"]openmpi-bin - high performance message passing library
openmpi-common - high performance message passing library
openmpi-dbg - high performance message passing library
openmpi-dev - high performance message passing library
openmpi-libs0 - high performance message passing library
[/SIZE][/INDENT]


Use 
mpicc   :  to compile parallel  c code. Wraps  gcc.
mpicxx or mpic++ : to compile parallel c++ code. Wraps g++.
mpif90 : to compile parallel fortran code (install gfortran package first).

Here is a parallel "hello world" code in c.
[http://www.slac.stanford.edu/comp/unix/farm/mpi.html](http://www.slac.stanford.edu/comp/unix/farm/mpi.html)

Compile it:
$ [COLOR="SeaGreen"]mpicc hello.c -o hello [/COLOR]

Parallelly start 4 copies of ./hello (on 4 different processors or nodes if you have a cluster or grid) .  Study the [documentation.. ]("http://www.open-mpi.org/faq/")for exact parms.
$ [COLOR="SeaGreen"]mpirun -np 4  ./hello [/COLOR]
----------------------

**See also: [http://www.futuredesktop.org/hpc_linux.html](http://www.futuredesktop.org/hpc_linux.html)** 
Build your own supercomputer for $2501.  Follow the link....

---

### Post by aswinms on 2008-05-06
> **moma said:**
> An idea,

If you can,  choose OpenMPI instead of LAM/MPI.  LAM/MPI is in maintenance mode and all development efforts are put on OpenMPI. (so say the LAM/MPI's website) 

[http://www.open-mpi.org/](http://www.open-mpi.org/)

Start synaptic and search for "openmpi" packages and install'em.

$ [COLOR="SeaGreen"]apt-cache search openmpi[/COLOR]
[INDENT][SIZE="2"]openmpi-bin - high performance message passing library
openmpi-common - high performance message passing library
openmpi-dbg - high performance message passing library
openmpi-dev - high performance message passing library
openmpi-libs0 - high performance message passing library
[/SIZE][/INDENT]


Use 
mpicc   :  to compile parallel  c code. Wraps  gcc.
mpicxx or mpic++ : to compile parallel c++ code. Wraps g++.
mpif90 : to compile parallel fortran code (install gfortran package first).

Here is a parallel "hello world" code in c.
[http://www.slac.stanford.edu/comp/unix/farm/mpi.html](http://www.slac.stanford.edu/comp/unix/farm/mpi.html)

Compile it:
$ [COLOR="SeaGreen"]mpicc hello.c -o hello [/COLOR]

Parallelly start 4 copies of ./hello (on 4 different processors or nodes if you have a cluster or grid) .  Study the [documentation.. ]("http://www.open-mpi.org/faq/")for exact parms.
$ [COLOR="SeaGreen"]mpirun -np 4  ./hello [/COLOR]
----------------------

**See also: [http://www.futuredesktop.org/hpc_linux.html](http://www.futuredesktop.org/hpc_linux.html)** 
Build your own supercomputer for $2501.  Follow the link....

I installed openmpi and lam-runtime by doing an "apt-get" and it worked the first time I booted lam without a problem(compilation and execution). Now, when I try to compile, it gives me no errors and it obviously doesn't compile since there is no output file. I find it very strange that it doesn't compile anymore, do you have a clue on what I should do to get it to work again?!

---

### Post by ryot on 2008-05-06
You are using OpenMPI's wrapper to compile, right?

---

### Post by aswinms on 2008-05-06
> **ryot said:**
> You are using OpenMPI's wrapper to compile, right?

I'm not sure what you mean, but if you're asking if there's a G++ compiler(All my MPI programs are in C++) on my machine, the answer is yes. The thing is, the first time, they worked without G++! Now I installed G++ and it still doesn't work!

---

### Post by ryot on 2008-05-06
Is your compile line something like?

mpicc program.c -o program

---

### Post by aswinms on 2008-05-08
> **ryot said:**
> Is your compile line something like?

mpicc program.c -o program

Yes it is, to be precise..:
mpic++ program.cpp

---

### Post by ryot on 2008-05-08
Can you compile your code using g++? I would ditch lam! It's really really really old. Is there a specific reason you are using the lam-runtime? I would also attempt to compile the "hello world" code in the link from Moma.

"Here is a parallel "hello world" code in c.
http://www.slac.stanford.edu/comp/unix/farm/mpi.html"

---

### Post by aswinms on 2008-05-09
> **ryot said:**
> Can you compile your code using g++? I would ditch lam! It's really really really old. Is there a specific reason you are using the lam-runtime? I would also attempt to compile the "hello world" code in the link from Moma.

"Here is a parallel "hello world" code in c.
http://www.slac.stanford.edu/comp/unix/farm/mpi.html"
Yes I can compile using g++, my programs use mpi, it would be helpful if i got LAM running, what are the alternatives anyway to compile mpi code in C++?

---

### Post by ryot on 2008-05-09
Go with MPICH or MPICH2. [http://www-unix.mcs.anl.gov/mpi/](http://www-unix.mcs.anl.gov/mpi/)

---

### Post by aswinms on 2008-05-10
> **ryot said:**
> Go with MPICH or MPICH2. [http://www-unix.mcs.anl.gov/mpi/](http://www-unix.mcs.anl.gov/mpi/)

... and all my MPI programs will work out of the box?! Do I need to install anything else?!

---

### Post by aswinms on 2008-05-10
> **ryot said:**
> Go with MPICH or MPICH2. [http://www-unix.mcs.anl.gov/mpi/](http://www-unix.mcs.anl.gov/mpi/)
Another thing I needed to know is, what are the steps I need to take to compile?! I used to do:
~$lamboot
~$mpic++ program.cpp
~$mpirun -np 5 ./a.out

   I obviously can't do a lamboot with MPICH, and it doesn't compile with "mpic++", so what should I do?

---

### Post by ryot on 2008-05-10
Are you running this on a single machine or a small cluster? If you are installing this for small cluster you will have to worry about inter-node communications. To compile MPICH make sure you have your C, C++ and Fortran compilers( I use gfortran) and decide where you want to have MPICH installed.   Do as follows:

tar xfvz mpich.tar.gz

CC=gcc CXX=g++ F77=gfortran ./configure --prefix=/foo

make && make install

Once MPICH is installed in /foo you can compile your mpi program. Running your mpi program is done by a command similar to this:

/foo/bin/mpirun -hostfile $name_of_machinesfile np=$however_many_procs ./$your_program_name_here

There are other possibilities but this is the simplest and most straight forward way of doing it. I can go into more detail if needed. Good Luck!

---

### Post by aswinms on 2008-05-11
> **ryot said:**
> Are you running this on a single machine or a small cluster? If you are installing this for small cluster you will have to worry about inter-node communications. To compile MPICH make sure you have your C, C++ and Fortran compilers( I use gfortran) and decide where you want to have MPICH installed.   Do as follows:

tar xfvz mpich.tar.gz

CC=gcc CXX=g++ F77=gfortran ./configure --prefix=/foo

make && make install

Once MPICH is installed in /foo you can compile your mpi program. Running your mpi program is done by a command similar to this:

/foo/bin/mpirun -hostfile $name_of_machinesfile np=$however_many_procs ./$your_program_name_here

There are other possibilities but this is the simplest and most straight forward way of doing it. I can go into more detail if needed. Good Luck!

I installed MPICH by doing an "apt-get install" and I'm simulating it as of now (single node).

---

### Post by bebops_lost on 2009-05-31
ok guys, I'm sorry, but the above exchange is really not clear.
I have a similar problem in that everytime I try to compile my parallel job on my home pc (to check for compile errors before uploading it to cluster) I get:

mpic++: Command not found

so what I'm trying to do is install whatever it is that I need to install so that mpic++ becomes a valid command that will actually compile the code (yes, I realize that it's actually using the g++ compiler, and that this is a "wrapper", if I need to install something else entirely I'm ok with that)

so, what I need to do is type:

```

$sudo apt-get install *******

```

now my question to you is : what should I put in place of the *****'s so that mpic++ will now work. any help you can offer would be hugely appreciated, I've installed so much useless stuff I'm starting to run out of drive space.

---

### Post by bebops_lost on 2010-11-02
ok, so I'll just answer my own question here:

the package you need, me (and anyone else that wants a really basic starting point), is *****= 'libopenmpi-dev', so type:

```

sudo apt-get install libopenmpi-dev

```

---

