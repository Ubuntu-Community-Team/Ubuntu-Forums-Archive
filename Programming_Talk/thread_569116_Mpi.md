---
title: "Mpi"
date: 2007-10-06
forum: Programming Talk
---

### Post by dubemasterd88 on 2007-10-06
Hey,
I installed MPI and everything... I can get it to compile and run my programs... but it seems like it is not recognizing 2 processors. I run my MPI hello world program, but it only prints hello world once.  To run the program, I am typing "mpirun C hello" (hello is the compiled program)

I have a core 2 duo pentium... .Anyone have any suggestions??

Thanks

---

### Post by dubemasterd88 on 2007-10-07
OK, I uninstalled everything, then installed libmpich1.0-dev and lam-runtime... I compiled this code: 

#include <stdio.h>
#include <mpi.h>

int main(int argc, char **argv)
{
  MPI_Init( &argc, &argv); 

  printf("Hello world\n"); 

  MPI_Finalize();
}

I compile this code using the command "mpicc hello.c"
it compiles fine

then I run it using the command "mpirun C a.out"

It then prints the following: 

Hello world
-----------------------------------------------------------------------------
It seems that [at least] one of the processes that was started with
mpirun did not invoke MPI_INIT before quitting (it is possible that
more than one process did not invoke MPI_INIT -- mpirun was only
notified of the first one, which was on node n0).

mpirun can *only* be used with MPI programs (i.e., programs that
invoke MPI_INIT and MPI_FINALIZE).  You can use the "lamexec" program
to run non-MPI programs over the lambooted nodes.
-----------------------------------------------------------------------------

Now I have even less of a clue what I should do.
PLEASE HELP!!!

---

### Post by Keneo on 2007-10-16
<deleted>

---

### Post by public_void on 2007-10-16
I'm not too knowledgeable of MPI yet, but as I understand it, the program is correct, I think.

However, use the -n number_of_nodes argument to run your program on more nodes, in your case processors.
```
mpiexec -n 2 a.out
```

If your using MPI-2 then use mpiexec, it has more functionally then mpirun. mpirun is for backwards compatibility with MPI.

---

### Post by hondacodonbk on 2009-05-12
I alse use LAM/MPI for parallel program,this is my program about "hello world":
```

#include <mpi.h>
#include <stdio.h>
 
int main(int argc,char *argv[])
{
		/* DATA */
	int rank,numProc;
	
		/* BODY OF PROGRAM */
	MPI_Init(&argc,&argv);			// init
	MPI_Comm_rank(MPI_COMM_WORLD,&rank);	// get rank
	MPI_Comm_size(MPI_COMM_WORLD,&numProc);	// get number of Proccess
	
	printf(""hello world\n");
	
	MPI_Finalize();				// terminal all MPI proccess
	return 0;
}

```
then,I compile it : mpicc -o file file.c
and run it with 4 processes: mpirun -np 4 file file.c

---

