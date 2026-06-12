---
title: "Question about mpirun"
date: 2011-06-20
forum: Programming Talk
---

### Post by kelvin490 on 2011-06-20
[INDENT]I have changed my previous hello world program for testing the command mpirun. I want to run the program with my computer which has two cores and I want to use both cores, here is the simple testing program:

/*The Parallel Hello World Program*/
#include <stdio.h>
#include <mpi.h>

int main(int argc, char **argv)
{
int node;

MPI_Init(&argc,&argv);
MPI_Comm_rank(MPI_COMM_WORLD, &node);

printf("Hello World from Node %d\n",node);

MPI_Finalize();
return 0;
}

I use mpicc to compile in ubuntu and I run it trying to use commands "mpirun -np 2 ./try.exe" and "mpirun ./try.exe" but some error message comes out:

mpiexec_ubuntu: cannot connect to local mpd (/tmp/mpd2.console_shsh); possible causes:
1. no mpd is running on this host
2. an mpd is running but was started without a "console" (-n option)
In case 1, you can start an mpd on this host with:
mpd &
and you will be able to run jobs just on this host.
For more details on starting mpds on a set of hosts, see
the MPICH2 Installation Guide.


What do it means? can I use mpirun in ubuntu? [/INDENT]

---

### Post by schauerlich on 2011-06-21
Well, read the error message. You need to have a daemon called mpd running on every computer in your cluster. It looks like you're using MPICH2, so follow the tutorial I linked you to in your other thread: [http://heather.cs.ucdavis.edu/~matloff/MPI/NotesMPICH.NM.html](http://heather.cs.ucdavis.edu/~matloff/MPI/NotesMPICH.NM.html)

To use both of your cores, try this:

```
mpd --ncpus=2 &
mpirun -np 2 --host localhost ./try.exe
```

---

