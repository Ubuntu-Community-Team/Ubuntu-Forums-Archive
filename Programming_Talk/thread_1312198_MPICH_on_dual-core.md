---
title: "MPICH on dual-core"
date: 2009-11-02
forum: Programming Talk
---

### Post by fluppet on 2009-11-02
I have a dual-core laptop, and want to install MPI on it so that I can run my MPI codes on it during development.

I installed the mpich-bin, libmpich1.0gf, libmpich1.0-dev, and mpi-doc packages.

Running a code with MPI_Init in it causes a segfault.

Running tstmachines produces the following output:

----------

Unexpected response from localhost:
--> ssh: connect to host localhost port 22: Connection refused
If your .cshrc, login, .bashrc, or other startup file
contains a command that generates any output when logging in,
such as fortune or hostname or even echo, you should modify
that startup file to only print such a message when the
process is attached to a terminal.  Examples of how to do
this are in the Users Manual.  If you do not do this, MPICH
will still work, but this script and the test programs will
report problems because they compare expected output from
what the programs produce.
    The test of /usr/bin/rsh <machine> true  failed on some machines.
    This may be due to problems in your .login or .cshrc files; 
    some common problems are described when detected.  Look at the 
    output above to see what the problem is.

    If the problem is something like 'permission denied', then the 
    remote shell command /usr/bin/rsh does not allow you to run programs.
    See the documentation about remote shell and rhosts.

Errors while trying to run /usr/bin/rsh localhost -n /bin/ls /home/alanr/mpichfoo
Unexpected response from localhost:
--> ssh: connect to host localhost port 22: Connection refused
    The ls test failed on some machines.
    This usually means that you do not have a common filesystem on 
    all of the machines in your machines list; MPICH requires this
    for mpirun (it is possible to handle this in a procgroup file; see
    the documentation for more details).

    Other possible problems include:
        The remote shell command /usr/bin/rsh does not allow you to run ls.
           See the documentation about remote shell and rhosts.
        You have a common file system, but with inconsistent names.
           See the documentation on the automounter fix.

 
1 errors were encountered while testing the machines list for LINUX

----------

Your help would be appreciated

---

### Post by fluppet on 2009-11-03
OK, I managed to fix one of the problems:

I added localhost to the $HOME/.rhosts file and I added a passwordless RSA key to my authorized_keys. That allows me to rsh to localhost without a password. The tstmachines test now does not report any errors.

I am still getting a segfault when I try to run MPI codes, however.

```

#include <mpi.h>
#include <stdio.h>

int main(){
	int rank, size;

	MPI_Init(NULL, NULL);

//	MPI_Comm_rank(MPI_COMM_WORLD, &rank);
//	MPI_Comm_size(MPI_COMM_WORLD, &size);

//	printf("Hello from %d of %d\n", rank, size);

	MPI_Finalize();

	return 0;
}

```

mpicc mpitest.c
mpirun -np 1 ./a.out

The MPI_Init call in this code causes a segmentation fault.

---

### Post by TheStatsMan on 2009-11-03
I used openmpi to build and run and I don't get a segmentation fault. Maybe it has something to do with your installation?

I get the following output, after un-commenting the code you commented out.

```

Hello from 0 of 1

```

---

### Post by fluppet on 2009-11-03
Hi, and thanks for the reply.

I know there is nothing wrong with the code - I am saying that I installed MPICH in the way I described above, and I am getting that error, so I want to know what is wrong with my MPICH installation.

---

