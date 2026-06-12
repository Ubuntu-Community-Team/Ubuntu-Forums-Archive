---
title: "problem in MPI"
date: 2011-03-09
forum: Programming Talk
---

### Post by joud on 2011-03-09
Hi

I'm beginner in Ubuntu and I  have installed  Openmpi & Mpich without problem

but when I try to execute some examples, it don't work....why???

just this example works

[PHP]#include <stdio.h>
#include <mpi.h>

int main(int argc, char** argv) {
    int myrank, nprocs;

    MPI_Init(&argc, &argv);
    MPI_Comm_size(MPI_COMM_WORLD, &nprocs);
    MPI_Comm_rank(MPI_COMM_WORLD, &myrank);

    printf("Hello from processor %d of %d\n", myrank, nprocs);

    MPI_Finalize();
    return 0;
}
[/PHP] I want to do  a difficult code, for example: using two processors,the first  adds two numbers  and  the second do the multiplication
please, help me

thanks in advance

---

### Post by talonmies on 2011-03-09
You are probably unwittingly mixing openMPI and mpich2 libraries and binaries. Try only having one or the other installed and see what happens.

---

### Post by joud on 2011-03-09
Thanks talonmies

I try to uninstall Mpich and leave only OpenMpi

but the problem  does not resolve

---

### Post by joud on 2011-03-11
any reply may help me!!!!

---

### Post by SevenMachines on 2011-03-11
As a test, how are you trying to run your example? For example, here...

```
$ sudo apt-get install openmpi-bin libopenmpi-dev 
$ mpicc -o example example.c
$ mpirun -np 4  ./example
Hello from processor 0 of 4
Hello from processor 1 of 4
Hello from processor 3 of 4
Hello from processor 2 of 4
```So it certainly runs, whether it 'works' i couldnt say :)

[EDIT] Sorry, ignore that, i didnt read the post correctly.. its friday :) If you post some example you're having trouble with though?

---

### Post by joud on 2011-03-13
ok no problem :)

Yes I try the code that you post and all run , but only with a simple example
 and with this example ,  nooooo
 
[PHP]#include<stdio.h>
#include<stdlib.h>
#include"mpi.h"
#define MCW MPI_COMM_WORLD
int * produitMatrice(int * a,int* b,int m,int l,int k){
    int i,j,x;int *res; res=(int*)malloc(m*k*sizeof(int));
    for(i=0;i<m;i++)
        for(j=0;j<m;j++)
            for(*(res+(i*k)+j)=0,x=0;x<l;x++){
                *(res+(i*k)+j)+=*(a+(i*l)+x) * (*(b+(x*k)+j));
            }
    return res;
}
int main(int argc,char ** argv){
    int me,size,m,l,k,x,*matA,*matB,i,j,*ligne,*colonne,*matC;
    MPI_Status st;
    MPI_Init(&argc,&argv);
        MPI_Comm_rank(MCW,&me);
    MPI_Comm_size(MCW,&size);
    if(!me){
        printf("Donnez le nombre des lignes de A: ");scanf("%d",&m);
        printf("Donnez le nombre des colonnes de A: ");scanf("%d",&l);
        printf("Donnez le nombre des colonnes de B: ");scanf("%d",&k);
        /// lecture des matrices A et B
        matA=(int*)malloc(m*l*sizeof(int));
        matB=(int*)malloc(l*k*sizeof(int));
        for(i=0;i<m;i++)for(j=0;j<l;j++) *(matA+i*l+j)=i+j+2;
        for(i=0;i<l;i++)for(j=0;j<k;j++) *(matB+i*k+j)=i*j+2;
        for(printf("\n\n"),i=0;i<m;printf("\n"),i++)for(j=0;j<l;j++)printf("%d\t",*(matA+i*l+j));
        for(printf("\n\n"),i=0;i<l;printf("\n"),i++)for(j=0;j<k;j++)printf("%d\t",*(matB+i*k+j));
    }
    MPI_Bcast(&m,1,MPI_INT,0,MCW);
    MPI_Bcast(&l,1,MPI_INT,0,MCW);
    MPI_Bcast(&k,1,MPI_INT,0,MCW);
    matC = (int*)malloc(m*k*sizeof(int));
    ligne = (int*)malloc(m/size*l*sizeof(int));
    colonne = (int*)malloc(l*k/size*sizeof(int));
    /// envoi de matrice A
    if(!me){
        for(i=0;i<m/size;i++)for(x=0;x<l;x++) *(ligne+(i*l)+x)=*(matA+(i*l)+x);
        printf("matrice A vers processus[%d]\n",me);for(i=0;i<m/size;printf("\n"),i++)for(j=0;j<l;j++)  printf("%d\t",*(matA+(i*l)+j));printf("\n");
        
        for(i=0;i<l;i++)for(x=0;x<k/size;x++) {*(colonne+(i*k/size)+x)=*(matB+(i*m)+x);}
        printf("matrice B vers processus[%d]\n",me);
        for(i=0;i<l;printf("\n"),i++)for(j=0;j<k/size;j++)  printf("%d\t",*(colonne+(i*k/size)+j));printf("\n");

        for(i=1;i<size;i++){
        MPI_Send(matA+(i*l*m/size),l*m/size,MPI_INT,i,i+size,MCW);
        printf("matrice A vers processus[%d]\n",i);
        for(j=0;j<m/size;printf("\n"),j++)for(x=0;x<l;x++) printf("%d\t",*(matA+(i*m/size*l+(l*j))+x));printf("\n");
        // créer portion
        int *portion; portion =(int*)malloc(l*k/size*sizeof(int));
        for(j=0;j<l;j++)for(x=0;x<k/size;x++) *(portion+(j*k/size)+x)=*(matB+(i*k/size+(j*m))+x);
        printf("matrice B vers processus[%d]\n",i);
        for(j=0;j<l;printf("\n"),j++)for(x=0;x<k/size;x++) printf("%d\t",*(portion+(j*k/size)+x));printf("\n");
        // fin 
        MPI_Send(portion,l*k/size,MPI_INT,i,i+size,MCW);
        }
    }
    else{
        MPI_Recv(ligne,l*m/size,MPI_INT,0,me+size,MCW,&st);
        MPI_Recv(colonne,l*k/size,MPI_INT,0,me+size,MCW,&st);
    }
    printf("mat A processus[%d]\n",me);for(j=0;j<m/size;printf("\n"),j++)for(i=0;i<l;i++) printf("%d\t",*(ligne+(j*l)+i));printf("\n");
    printf("mat B processus[%d]\n",me);for(j=0;j<l;printf("\n"),j++)for(i=0;i<k/size;i++) printf("%d\t",*(colonne+(j*k/size)+i));printf("\n");
    
    int * res;
    res=(int*)malloc((m/size)*(k/size)*sizeof(int));
    res=produitMatrice(ligne,colonne,m/size,l,k/size);printf("produit \n");
    /// MAJ matC
    for(i=0;i<m/size;i++)for(j=0;j<k/size;j++) *(c+(i*k/size)+j)=*(res)
    for(i=1;i<size-1;i++){
        MPI_Send(colonne,l*k/size,MPI_INT,(me+1)%size,me+size,MCW);
        MPI_Recv(colonne,l*k/size,MPI_INT,(me-1)%size,me+size,MCW,&st);
        int * res;
        res=(int*)malloc((m/size)*(k/size)*sizeof(int));
        res=produitMatrice(ligne,colonne,m/size,l,k/size);printf("produit \n");    
    }


    if(!me){
        int * res;res=(int*)malloc((m/size)*(k/size)*sizeof(int));
        res=produitMatrice(ligne,colonne,m/size,l,k/size);printf("produit \n");
        for(i=0;i<m/size;printf("\n"),i++)for(j=0;j<k/size;j++) printf("%d\t",*(res+(i*k/size)+j));printf("\n");
    }    
    MPI_Finalize();
}[/PHP]

the error is: 
```
.........@ubuntu:~$ mpicc mat.c -o mat
mat.c: In function ‘main’:
mat.c:71: error: ‘c’ undeclared (first use in this function)
mat.c:71: error: (Each undeclared identifier is reported only once
mat.c:71: error: for each function it appears in.)
mat.c:72: error: expected ‘;’ before ‘for’

```

I don't understand

---

### Post by joud on 2011-03-13
I think that the problem is in library stdlib.h , it doesn't work with me or always in ubuntu?????

---

### Post by talonmies on 2011-03-13
So despite what you said earlier in the thread, the problem is not that you can't run MPI programs at all. It is that you can't compile a specific example? How did you possibly imagine someone could help you before you had actually posted the code? 

The compiler is telling you there is are two errors with this line:

```

for(i=0;i<m/size;i++)for(j=0;j<k/size;j++) *(c+(i*k/size)+j)=*(res)
```

and there are. Neither has anything to do with MPI. If you cannot understand why that line is wrong, even after the compiler gives an error which says exactly what is wrong, perhaps you should spend some time learning basic C syntax before you go worrying about parallel programming APIs like MPI.

---

### Post by joud on 2011-03-18
Sorry for being late
Thanks talonmies for your reply... I try to correct the error and compile it without problem

but I don't know how to use MPI 
I compile the code and no problem, what can I do to execute the code using more processus in the same machine??

---

### Post by joud on 2011-03-18
```

............@ubuntu:~$ mpicc example.c -o example


```I'm trying to compile the example by using this command but how can  I  execute the example ?

---

### Post by joud on 2011-03-31
Sorry , I'm late, I had problem in my OS Ubuntu

but i'm return now :)

Please .... help me

---

### Post by Arndt on 2011-03-31
> **joud said:**
> ```

............@ubuntu:~$ mpicc example.c -o example


```I'm trying to compile the example by using this command but how can  I  execute the example ?

I don't know mpicc, but if it works like gcc, it will produce an executable file "example", which you can run by issuing the command "./example".

---

### Post by SevenMachines on 2011-03-31
you need to run in the openmpi environment rather than from the directly. As a simple example, as mentioned in post #5, could be run with something like
```
$ mpirun -np 4  ./example
```This says, 'Run the example binary in openmpi using 4 processes'.

---

### Post by joud on 2011-03-31
Thanks , 
I know that  it must use this command **mpirun -np 4 ./example**

but.. how can I make process n°1 do some instructions, process n°2 do auther instructions...etc

for exmaple, when I want to calculate the multiplication of two matrices A*B=C

what can I do???

---

### Post by SevenMachines on 2011-04-01
theres an example of matrix multiplication here,
[http://www.pdc.kth.se/training/Tutor/MPI/Templates/mm/mm.c](http://www.pdc.kth.se/training/Tutor/MPI/Templates/mm/mm.c)
but obviously you would need to alter it to make it useful. More importantly you need to get stuck into a good tutorial/book on mpi, how to split a job onto different processes is quite fundamental to mpi.

---

### Post by joud on 2011-04-01
Thanks SevenMachines  for your aid

mmmmmm can you give me  tutorials on mpi, in english or french language as you like
 
I have  some tutorials but may your choice is more comprehensin and clear  :)

speacially how to split a job onto different processes

---

### Post by SevenMachines on 2011-04-01
I doubt my choices would be any more comprehensive or clear than yours to be honest, i had a need to learn some mpi a while ago but nothing too advanced. I think I read '[A Users Guide to MPI]("http://www.wellesley.edu/CS/courses/CS331/notes/mpi.guide.pdf")', which is free and seemed ok. The author has a new book which isnt free, but the source code for the examples is, and is on his homepage [http://www.cs.usfca.edu/~peter/ppmpi/]("http://www.cs.usfca.edu/%7Epeter/ppmpi/") so it might be worth looking through some of the examples. I'll try to think of more, its been a while though.

---

### Post by joud on 2011-04-03
Thank you very much SevenMachines for all your efforts to help me

are you have or know some examples in mpi which for sorting arrays of course in mpi?

just a simple example..

---

