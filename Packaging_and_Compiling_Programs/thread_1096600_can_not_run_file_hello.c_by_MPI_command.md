---
title: "can not run file hello.c by MPI command ?"
date: 2009-03-15
forum: Packaging and Compiling Programs
---

### Post by hondacodonbk on 2009-03-15
hi everybody,I have a problem with lam/MPI in U.
I  installed MPICH2 into U,then I installed 2 package : lam-runtime_7.1.2-1.4_i386.deb and lam4-dev_7.1.2-1.5_i386.deb
I am learning parallel programing with MPI,I create a file hello.c to try run this program
this is my code:
```


#include <mpi.h>
#include <stdio.h>

int main(int argc, char* argv[]) {
	int rank, nprocs;
	MPI_Init(&argc, &argv);
	MPI_Comm_rank(MPI_COMM_WORLD, &rank);
	MPI_Comm_size(MPI_COMM_WORLD, &nprocs);
	char s[30];
	gethostname(s, 30);
	printf("Hello world from: host@process_rank = %s@%d \n", s, rank);
	MPI_Finalize();
	return 0;
}

```
I compier this file by command : mpicc -o hello hello.c and successfull
But when I run this by command : mpirun -np 4 hello .It doesn't work and send an error in Terminal:
```

mpiexec_saothienhat: cannot connect to local mpd (/tmp/mpd2.console_saothienhat); possible causes:
  1. no mpd is running on this host
  2. an mpd is running but was started without a "console" (-n option)
In case 1, you can start an mpd on this host with:
    mpd &
and you will be able to run jobs just on this host.
For more details on starting mpds on a set of hosts, see
the MPICH2 Installation Guide.

```.
Can you help me ? I don't how to correct it and run my program
thank

---

### Post by sanderj on 2009-03-15
> **hondacodonbk said:**
> 
```

mpiexec_saothienhat: cannot connect to local mpd (/tmp/mpd2.console_saothienhat); possible causes:
  1. no mpd is running on this host
  2. an mpd is running but was started without a "console" (-n option)
In case 1, you can start an mpd on this host with:
    mpd &
and you will be able to run jobs just on this host.
For more details on starting mpds on a set of hosts, see
the MPICH2 Installation Guide.

```
Can you help me ? I don't how to correct it and run my program
thank

Well, have you done what the quoted error message says? So: run mpd, and run it in the correct way?

---

### Post by hondacodonbk on 2009-03-15
I think I press command of mpd exactly
Thank for your help,I did it.I remove mpich2 and then I install lam-runtime and lamdev.So,now I can do with parallel programming ^_^

---

### Post by dunghtk on 2009-04-27
I used to install MPICH2 and have the same trouble. I called: which mpd, which mpiexec, mpirun, they all appeared. But I cant run any MPI prgram. Then I removed all mpi programs I had installed before. After that I installed mpich-bin, mpich-mpd-bin, openmpi-bin,lam-runtime, mpich-shmem-bin. When I compiled an MPI C program ( mpi_hello.c) as: mpicc -o mpi_hello mpi_hello.c, it's ok. But when I called: mpirun -np 4 mpi_hello, it ran out nothing.  
who can tell me how I can solve this trouble? Thankyou!

---

### Post by delirejisor on 2010-10-31
> **dunghtk said:**
> I used to install MPICH2 and have the same trouble. I called: which mpd, which mpiexec, mpirun, they all appeared. But I cant run any MPI prgram. Then I removed all mpi programs I had installed before. After that I installed mpich-bin, mpich-mpd-bin, openmpi-bin,lam-runtime, mpich-shmem-bin. When I compiled an MPI C program ( mpi_hello.c) as: mpicc -o mpi_hello mpi_hello.c, it's ok. But when I called: mpirun -np 4 mpi_hello, it ran out nothing.  
who can tell me how I can solve this trouble? Thankyou!

it has been awhile, but i had the same problem and solved it as what's said at previous messages.(btw im running this program at my pc for testing purposes)

1-uninstall mpich2
2-install lam-runtime and lamdev
3-compile with "mpicc ..."
4-and run with "mpirun C exec_file"

---

