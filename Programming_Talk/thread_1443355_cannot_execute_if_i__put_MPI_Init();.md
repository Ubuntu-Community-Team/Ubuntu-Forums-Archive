---
title: "cannot execute if i  put MPI_Init();"
date: 2010-03-31
forum: Programming Talk
---

### Post by spanBobHere on 2010-03-31
hye everyone
i have a problem with this MPI & C++ codes. can u guys help me?

[COLOR=RoyalBlue]#include <cstdio> 
#include <mpi.h> 
using namespace std; 
int main(int argc, char *argv[]) { 
[/COLOR][INDENT][COLOR=RoyalBlue][COLOR=Red]MPI_Init(&argc, &argv);[/COLOR] 
[/COLOR][/INDENT][INDENT][COLOR=RoyalBlue]printf("test\n"); 
[COLOR=Red]MPI_Finalize(); [/COLOR]
[/COLOR][/INDENT][COLOR=RoyalBlue]} [/COLOR]

OUTPUT:
if i execute the above code, it will give this error.
*** Oops -- I cannot open the LAM help file.
*** I tried looking for it in the following places:
***
***   $HOME/lam-helpfile
***   $HOME/lam-7.1.2-helpfile
***   $HOME/etc/lam-helpfile
***   $HOME/etc/lam-7.1.2-helpfile
***   $LAMHELPDIR/lam-helpfile
***   $LAMHELPDIR/lam-7.1.2-helpfile
***   $LAMHOME/etc/lam-helpfile
***   $LAMHOME/etc/lam-7.1.2-helpfile
***   $SYSCONFDIR/lam-helpfile
***   $SYSCONFDIR/lam-7.1.2-helpfile
***
*** You were supposed to get help on the program "MPI"
*** about the topic "no-lamd"
***
*** Sorry!
-----------------------------------------------------------------------------

the same code, if i take out the MPI....
[COLOR=RoyalBlue]#include <cstdio> 
#include <mpi.h> 
using namespace std; 
int main(int argc, char *argv[]) { 
[/COLOR][INDENT][COLOR=RoyalBlue][COLOR=Red]//MPI_Init(&argc, &argv);[/COLOR] 
  [/COLOR][/INDENT][INDENT][COLOR=RoyalBlue]printf("test\n"); 
  [COLOR=Red]//MPI_Finalize(); [/COLOR]
  [/COLOR][/INDENT][COLOR=RoyalBlue]} [/COLOR]

OUTPUT:
x1@PC-MPI-0:~/ccCode1$ mpic++ -O -c ccCode1.cpp
x1@PC-MPI-0:~/ccCode1$ mpic++ -O -o ccCode1 ccCode1.o
x1@PC-MPI-0:~/ccCode1$ mpiexec -n 4 ./ccCode1
test
test
test
test

so like.. the error comes from the code MPI_Init and MPI_Finalize. but i have to use that code in order to execute in multiple machine.
can you guyz help me plz..

thanks

---

### Post by spanBobHere on 2010-04-01
nvm...
i have already found the solution...
i used the WRONG compiler..
i should use mpicxx -DMPICH_IGNORE_CXX_SEEK -o fileName fileName.cc
;)

---

