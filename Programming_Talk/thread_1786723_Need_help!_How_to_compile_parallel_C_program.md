---
title: "Need help! How to compile parallel C program?"
date: 2011-06-20
forum: Programming Talk
---

### Post by kelvin490 on 2011-06-20
I have a simple testing program like this:

/*The Parallel Hello World Program*/
#include <stdio.h>
#include <mpi.h>

main(int argc, char **argv)
{
   int node;
   
   MPI_Init(&argc,&argv);
   MPI_Comm_rank(MPI_COMM_WORLD, &node);
     
   printf("Hello World from Node %d\n",node);
            
   MPI_Finalize();
}

My program is, I can't compile this program using gcc, and I can't find something like pgcc in ubuntu. How should I compile this program? After compiling, what should I do to run this program?


Thank you.

---

### Post by NovaAesa on 2011-06-20
Could you show the command you used to invoke gcc as well as the error message(s) it produced?

---

### Post by kelvin490 on 2011-06-20
> **NovaAesa said:**
> Could you show the command you used to invoke gcc as well as the error message(s) it produced?

I use gcc to compile but cannot work

shsh@ubuntu:~/Desktop/Try$ gcc tryhpc.c -o try.exe
tryhpc.c:3:17: error: mpi.h: No such file or directory
tryhpc.c: In function ‘main’:
tryhpc.c:10: error: ‘MPI_COMM_WORLD’ undeclared (first use in this function)
tryhpc.c:10: error: (Each undeclared identifier is reported only once
tryhpc.c:10: error: for each function it appears in.)

---

### Post by NovaAesa on 2011-06-20
I did some quick googling, I don't think you are meant to use gcc to compile the program, I'm not sure though - I've never done anything with MPI before. I'm trying to work it out now :)

---

### Post by schauerlich on 2011-06-20
What version of MPI are you using? If it's MPICH or LAM, check out these tutorials:

[http://heather.cs.ucdavis.edu/~matloff/MPI/NotesMPICH.NM.html](http://heather.cs.ucdavis.edu/~matloff/MPI/NotesMPICH.NM.html)
[http://heather.cs.ucdavis.edu/~matloff/MPI/NotesLAM.NM.html](http://heather.cs.ucdavis.edu/~matloff/MPI/NotesLAM.NM.html)

General MPI information here:
[http://heather.cs.ucdavis.edu/~matloff/mpi.html](http://heather.cs.ucdavis.edu/~matloff/mpi.html)

To put it lightly, setting up MPI correctly is a bitch. Good luck.

---

### Post by NovaAesa on 2011-06-20
Okay, I got *something* happening. Install the package libopenmpi-dev ```
sudo apt-get install libopenmpi-dev
```
Then you should be able to compile your program with ```
mpicc helloworld.c
```
You can then run it with
```

./a.out

```
although I'm getting some strange errors when I run the program.

---

### Post by kelvin490 on 2011-06-20
[/code]although I'm getting some strange errors when I run the program.[/QUOTE]


Thanks, it can be run now but I got some error like this:

shsh@ubuntu:~/Desktop/Try$ mpicc tryhpc.c -o try2
tryhpc.c:6: warning: return type defaults to ‘int’
tryhpc.c: In function ‘main’:
tryhpc.c:15: warning: control reaches end of non-void function
shsh@ubuntu:~/Desktop/Try$ ./try2
Hello World from Node 0

BTW, can I use something like mpirun to run it? I want to try to use both cores of my computer to run it and make it shows Node 1 also besides Node0.

Thanks a lot.

---

### Post by cgroza on 2011-06-20
> **kelvin490 said:**
> 
[/code]although I'm getting some strange errors when I run the program.


Thanks, it can be run now but I got some error like this:

shsh@ubuntu:~/Desktop/Try$ mpicc tryhpc.c -o try2
tryhpc.c:6: warning: return type defaults to &#8216;int&#8217;
tryhpc.c: In function &#8216;main&#8217;:
tryhpc.c:15: warning: control reaches end of non-void function
shsh@ubuntu:~/Desktop/Try$ ./try2
Hello World from Node 0

BTW, can I use something like mpirun to run it? I want to try to use both cores of my computer to run it and make it shows Node 1 also besides Node0.

Thanks a lot.
Declare main as int main and don't forget to return from it and the warnings should go away.

---

### Post by kelvin490 on 2011-06-20
> **cgroza said:**
> Declare main as int main and don't forget to return from it and the warnings should go away.
 
Thank you, man.

---

### Post by ramsrambo on 2011-09-15
Install openmpi-bin pkg by 

sudo apt-get install openmpi-bin

then once installation is successful then
 mpirun ./try

it is working for me:)

---

