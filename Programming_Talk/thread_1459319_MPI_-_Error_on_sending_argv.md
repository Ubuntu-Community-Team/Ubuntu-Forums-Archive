---
title: "MPI - Error on sending argv"
date: 2010-04-21
forum: Programming Talk
---

### Post by awiles on 2010-04-21
Hi all,
I write a simple MPI program to send a text message to another process. The code is below.
(test.c)
```
#include "mpi.h"
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char* argv[]) {
    int dest, noProcesses, processId;
    MPI_Status status;
    
    char* buffer;
    
    char* text = "ABCDEF";
    
    MPI_Init(&argc, &argv);
    MPI_Comm_size(MPI_COMM_WORLD, &noProcesses);
    MPI_Comm_rank(MPI_COMM_WORLD, &processId);
    
    buffer = (char*) malloc(256 * sizeof(char));
    
    if (processId == 0) {
      fprintf(stdout, "Master: sending %s to %d\n", text, 1);
      MPI_Send((void *)&text, strlen(text) + 1, MPI_CHAR, 1, 0, MPI_COMM_WORLD);
    } else {
      MPI_Recv(&buffer, 128, MPI_CHAR, MPI_ANY_SOURCE, MPI_ANY_TAG, MPI_COMM_WORLD, &status);
      fprintf(stdout, "Slave: received %s from %d\n", buffer, status.MPI_SOURCE);
    }
    MPI_Finalize();
    return 0;
}
```
After compiling and executing it I get the following output:
```
[root@cluster Desktop]# mpicc -o test test.c
[root@cluster Desktop]# mpirun -np 2 test
Master: sending ABCDEF to 1
Slave: received ABCDEF from 0
```
In the source code above, I replace
```
char* text = "ABCDEF";
```
by
```
char* text = argv[1];
```
then compile and execute it again with the following commands:
```
[root@cluster Desktop]# mpicc -o test test.c
[root@cluster Desktop]# mpirun -np 2 test ABCDEF
```
Then I get the following output:
```
Master: sending ABCDEF to 1
[cluster:03917] *** Process received signal ***
[cluster:03917] Signal: Segmentation fault (11)
[cluster:03917] Signal code: Address not mapped (1)
[cluster:03917] Failing at address: 0xbfa445a2
[cluster:03917] [ 0] [0x959440]
[cluster:03917] [ 1] /lib/libc.so.6(_IO_fprintf+0x22) [0x76be02]
[cluster:03917] [ 2] test(main+0x143) [0x80488b7]
[cluster:03917] [ 3] /lib/libc.so.6(__libc_start_main+0xdc) [0x73be8c]
[cluster:03917] [ 4] test [0x80486c1]
[cluster:03917] *** End of error message ***
--------------------------------------------------------------------------
mpirun noticed that process rank 1 with PID 3917 on node cluster.hpc.org exited on signal 11 (Segmentation fault).
--------------------------------------------------------------------------
```
I’m very confused because the only difference between the two source codes is the difference between
```
char* text = "ABCDEF";
```
and
```
char* text = argv[1];
```
Can any one help me why the results are so different? How can I send argv[i] to another process?
Thank you very much!

---

### Post by MadCow108 on 2010-04-21
the problem is this:
MPI_Send((void *)&text...
MPI_Recv(&buffer, ...

the functions expect a pointer to a buffer, not a pointer to a pointer to a buffer.
You are actually transferring/receiving the pointer + some garbage
remove the & in both cases

---

### Post by awiles on 2010-04-21
> **MadCow108 said:**
> the problem is this:
MPI_Send((void *)&text...
MPI_Recv(&buffer, ...

the functions expect a pointer to a buffer, not a pointer to a pointer to a buffer.
You are actually transferring/receiving the pointer + some garbage
remove the & in both cases

Thank MadCow108. Just remove the two ampersands and the application runs without any error.
Thanks again :)

---

