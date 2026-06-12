---
title: "How to install MPICH2?"
date: 2007-09-17
forum: Programming Talk
---

### Post by Silveira on 2007-09-17
Hello there, this is my first post in ubuntuforums.org. ):P

What I'm trying is **how installing MPICH2 in Ubuntu**. In fact, what I need is MPICH2 to use MPI_Comm_connect to attach a new process to a current running MPI group. I guess is only possible to use this function in MPICH2. I'm trying to do this using MPICH  1.2.7p1, described bellow:

I have two files, *server.c* and *client.c*. The first one is:

```
#include<mpi.h>
#include<stdio.h>
#include<stdlib.h>
 
int size, rank, msg;
 
int main(int argc, char *argv[]){
   MPI_Comm cliente;
   MPI_Status status;
   char portname[MPI_MAX_PORT_NAME];
 
   MPI_Init(&argc,&argv);
   MPI_Comm_size(MPI_COMM_WORLD,&size);
   MPI_Comm_rank(MPI_COMM_WORLD,&rank);
 
   MPI_Open_port(MPI_INFO_NULL, portname);
   printf("portname: %s\n", portname);
   MPI_Comm_accept(portname, MPI_INFO_NULL, 0, MPI_COMM_SELF, &cliente);
   printf("client connected\n");
   MPI_Recv(&msg, 1, MPI_INT, MPI_ANY_SOURCE, MPI_ANY_TAG, cliente, &status);
   printf("msg: %d\n", msg);
   MPI_Comm_free(&cliente);
   MPI_Close_port(portname);
   MPI_Finalize();
}
```

The client.c content:

```
#include<mpi.h>
#include<stdio.h>
#include<stdlib.h>
#include<string.h>
 
int size, rank;
int main(int argc, char *argv[]){
   MPI_Comm servidor;
   int msg, tag, dest;
   char portname[MPI_MAX_PORT_NAME]; 
 
   MPI_Init(&argc,&argv);
   MPI_Comm_size(MPI_COMM_WORLD,&size);
   MPI_Comm_rank(MPI_COMM_WORLD,&rank);
   if (argc >= 2){
      printf("Trying connect to %s\n", argv[1]);
      strcpy(portname, argv[1]);
      MPI_Comm_connect(portname, MPI_INFO_NULL, 0, MPI_COMM_WORLD, &servidor);
      msg = 42; tag = 0; dest = 0;
      MPI_Send(&msg, 1, MPI_INT, dest, tag, servidor);
      MPI_Comm_disconnect(&servidor);
   }
   MPI_Finalize();
}
```

I try to compile this with:
```
mpicc server.c -o server
mpicc client.c -o client
```

I got no problems to compile (strange). So I try to run it:
```
$ mpirun -np 1 server
portname: 0.1.0:2000
```

So my name is 0.1.0 (strange too) and port 2000. I try to run the client program:
```
$ mpirun -np 1 client 0.1.0:2000
```

I  got this error:
```
Trying connect to 0.1.0:2000
[irmaos:13280] [0,1,0] ORTE_ERROR_LOG: Pack data mismatch in file dss/dss_unpack.c at line 171
[irmaos:13280] [0,1,0] ORTE_ERROR_LOG: Pack data mismatch in file dss/dss_unpack.c at line 145
[irmaos:13280] *** An error occurred in MPI_Comm_connect
[irmaos:13280] *** on communicator MPI_COMM_WORLD
[irmaos:13280] *** MPI_ERR_UNKNOWN: unknown error
[irmaos:13280] *** MPI_ERRORS_ARE_FATAL (goodbye)
```

I also tried this, without sucess:
```
$ mpirun -np 1 client 127.0.0.1:2000
Trying connect to 127.0.0.1:2000
```

[LIST]
[*]Anyone knows what I'm doing wrong?
[*]Anyone knows how to install MPICH2?
[/LIST]

---

### Post by antiregulator on 2007-11-22
actually i have installation issues concerning mpich2 too.

the configuration file will not be produced, although i follow the installation instructions by the book!

anyone, plz!

---

### Post by monkeyking on 2007-11-23
I installed mpich2 on feisty,
and it was absolutly hell.

We had problems connecting starting up processes on the different machines.
And it seems you have the same problem.

I can't really recall, but what we did was the followin I guess.

set up the hosts.conf or whatever the name is on each of the clients.

And the the crazy part is the following.

you have to edit the /etc/hosts,
so that you /etc/hostname isn't the loop back address.

that is you localhost etc, should direct to you real ip.


If you still have problems, I can check the machine I installed it on.

good luck

---

### Post by olejorgen on 2008-01-15
```
~$ sudo apt-get install mpich
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mpich is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mpich has no installation candidate

```

hm... (I guess this is mpich1?)

---

### Post by aswinms on 2008-05-10
> **olejorgen said:**
> ```
~$ sudo apt-get install mpich
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mpich is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mpich has no installation candidate

```

hm... (I guess this is mpich1?)

try..
~$ sudo apt-get install mpich-bin

---

