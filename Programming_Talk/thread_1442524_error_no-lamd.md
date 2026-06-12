---
title: "error no-lamd"
date: 2010-03-30
forum: Programming Talk
---

### Post by spanBobHere on 2010-03-30
I have tried to execute C program using MPI. it is working. 
but this error has occur when i want to execute C++ program

[COLOR=Red]-----------------------------------------------------------------------------
*** Oops -- I cannot open the LAM help file.
*** I tried looking for it in the following places:
***
***   $HOME/lam-helpfile
***   $HOME/lam-7.1.2-helpfile
***   $HOME/etc/lam-helpfile
***   $HOME/etc/lam-7.1.2-helpfile
-----------------------------------------------------------------------------
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
[/COLOR]
the commands that i used to compile the c++ code (.cc) are
[B][FONT=Courier New][SIZE=3]mpic++ -c fileName.cc
mpic++ -o fileName fileName.cc
mpirun -np 6 ./fileName[/SIZE][/FONT][/B]

An error occur right after i execute the mpirun code
any suggestion?

---

