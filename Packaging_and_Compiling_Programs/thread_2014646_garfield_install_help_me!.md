---
title: "garfield install help me!"
date: 2012-07-02
forum: Packaging and Compiling Programs
---

### Post by kimhyeongi on 2012-07-02
I try install garfield, ubuntu 10.04 (32bit)

sudo apt-get install gfortran
sudo apt-get install cernlib
sudo apt-get install libsl0-dev
sudo apt-get install nypatchy
sudo apt-get install g77
sudo apt-get install libgraflib1-gfortran libgrafx11-1-gfortran libmathlib2-gfortran libkernlib1-gfortran liblapack3gf liblapack-dev libpacklib-lesstif1-gfortran libpacklib1-gfortran libgsl0-dbg libblas3gf gsl-bin libgsl0ldbl

and user name : test
mkdir home/test/garfield/ 

and input data file

garfield-7.car
garfadd-9.cra
garfield-9.cra
garfield.hlp
heed101garf.car
magboltz-7.car
patchy_step

and install neBEM

home/test/V1.8.10
and
make clean
make all

and reference by this link
[http://ubuntuforums.org/showthread.php?p=10195676#post10195676](http://ubuntuforums.org/showthread.php?p=10195676#post10195676)

make a file 'gfortran_iargc.c'
and input text

extern int _gfortran_iargc(void);
int iargc_()
{
return _gfortran_iargc();
}

and save

terminal input the 
gfortran -c _gfortran_iargc.c

and makefile $DUMMYIARGCOBJ to the location of this file.

and
chmod +x patchy_step


so finally

make garfield-9

test@ubuntu:~/garfield$ make garfield-9
rm *.f *.o
rm: cannot remove `*.f': No such file or directory
rm: cannot remove `*.o': No such file or directory
make: [garfield-9.f] Error 1 (ignored)
./patchy_step garfield-9
./patchy_step garfadd-9
fcasplit garfield-9.f
 FCASPLIT executing.
             Input file : garfield-9.f
           Shell script : garfield-9.shfca
              Make file : garfield-9.mkfca
        Fortran    name : gfortran  
        Fortran options : -c -g -O2 -fno-automatic  
             CC    name : gcc  
             CC options : -c -g -O2  
      Assembler    name : as  
      Assembler options :   
At line 786 of file /build/buildd/cernlib-2006.dfsg.2/src/patchy/fcasplit.F (unit = 11, file = '')
Fortran runtime error: File 'garfield-9.f' does not exist
make: *** [main-9.f] Error 2


How to fix it ?

plz somebody help me,

---

### Post by oldos2er on 2012-07-02
Moved to Packaging and Compiling Programs.

---

