---
title: "MPI and MPE"
date: 2008-12-22
forum: Programming Talk
---

### Post by nick.not.used on 2008-12-22
Hello everybody,
I have a problem in implementing MPE with MPICH in C++, I wrote a test to learn a little bit how it works: each processor should fill the vector vec whith PID+1 in the position PID+1, where PID is the processor ID. The output is a logfile that should work with the program clog2TOslog. However when I run it prints the following error

clog2TOslog2 logTest.clog2
GUI_LIBDIR is set. GUI_LIBDIR = /usr/scratch/crosetto/mpe/lib
**** Error! State!=State
java.lang.reflect.InvocationTargetException

I compiled with 

 g++ ./main_test.cpp -o out -L/usr/include/mpi -lmpi -L/usr/scratch/crosetto/mpe/lib -lmpe

Anyone has some clue? Here is the source code.
Thanks in advance.

#include "/usr/include/mpi/mpi.h"
#include "/usr/scratch/crosetto/mpe/include/mpe.h"

int main(int argc, char** argv)
{
    MPI_Init(&argc, &argv);
    MPE_Init_log();
    int rank, numtasks;
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Comm_size(MPI_COMM_WORLD, &numtasks);
    int vec[numtasks+1];
    vec[0]=0;
    vec[rank+1] = rank+1;
    MPE_Describe_state(1, 2, "broadcasts", "red");
    MPE_Start_log();
    MPE_Log_event(1, 0, "start broadcasts");
    for(int j=1; j<numtasks+1 ; ++j)
         MPI_Bcast( &vec[j], 1, MPI_INT, j-1, MPI_COMM_WORLD);
    MPE_Log_event(1, 0, "end broadcasts");
    MPE_Stop_log();
    MPE_Finish_log("logTest");
    MPI_Finalize();
}

---

### Post by monkeyking on 2008-12-22
Are you sure it's installed correctly?
Are you running it on a cluster?

It seems your running some specialized java gui.

I had problems in the past making mpich work from the reposatiries.
So I ended up installing it from source.

that worked perfectly.
edit:

try just a hello world mpi application,
just to check if the different nodes are up

---

### Post by nick.not.used on 2008-12-23
hi monkeyking, thank you for the answer. 
A first problem was that I had to download the java2 sdk package instead of the jre. 
Indeed I tried both linking the mpe librairies from mpich and compiling the librairies in a different directory, obtaining almost the same results. 
I'm working locally, on a 4-cores pc. MPI alone works fine, also the program hello world that you suggested works.

In the compilation of the MPE librairies I noticed that that something went wrong while compiling the files thus, to avoid the debugging, I used the MPE librairies installed with mpich, that is, I compiled with

 g++ ./main_test.cpp -o out -I/usr/include/mpi -L/usr/lib/mpich/lib/ -lmpi -I/usr/include/mpi -L/usr/lib/mpich/lib -lmpe -llmpe

Launching jumphot and trying to convert from clog to slog2 format I gott this error:

Error > State{ Primitive[ infobox[ TimeBBox(0.0,0.0) Category=ObjDef{ evts=(1,2), Category[ index=1, name=broadcasts, topo=State, color=(255,0,0,255,true), isUsed=true, width=1, vis=true, search=true, ratios=0.0,0.0, count=0 ] }: ] (0.0, 1) (0.0, 1) ] bsize=32 }
Error > Drawable.Order: WARNING! Equal Drawables?

Do you have an idea of what it means?
Thanks again!


PS: The code of the previous post had an error. The one that I'm trying to use is this:

#include "mpi.h"
#include "mpe.h"
#include <iostream>
using namespace std;
int main(int argc, char** argv)
{
    MPI_Init(&argc, &argv);
    MPE_Init_log();

    int rank, numtasks;
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Comm_size(MPI_COMM_WORLD, &numtasks);
    int vec[numtasks+1];
    vec[0]=0;
    vec[rank+1] = rank+1;
        MPE_Describe_state(1, 2, "broadcasts", "red");
    //MPE_Start_log();
    for(int j=1; j<numtasks+1 ; ++j)
        {
            MPE_Log_event(1, 0, "start broadcasts");
            MPI_Bcast( &vec[j], 1, MPI_INT, j-1, MPI_COMM_WORLD);
            MPE_Log_event(2, 0, "end broadcasts");

        }
    //MPE_Stop_log();

    cout << "hello world" << endl;
    MPE_Finish_log("logTest");
    MPI_Finalize();
}

---

### Post by kjohansen on 2008-12-23
so is the code you are using have the MPE_Start_log() and MPE_Stop_log() commented out or is it uncommented?

---

### Post by nick.not.used on 2008-12-23
I commented it because I got an error at runtime. Actually taking out of the loop the MPE_Log_event calls I don't get any errors, but the final slog2 file is empty!

---

### Post by monkeyking on 2008-12-23
You should be very carefull that your installation actually works.
Consider reinstalling and notice the error messages.

Which version of java sdk did you install, are you sure it works with your mpi version.
You should consider using an old version of java.

For your choice of libraries.

Are you planning to move your program to a cluster?

mpi is meant as message passing between different computers,
not different cores.

You should use normal threading pthread, if your different processers share memory.

---

### Post by nick.not.used on 2008-12-23
yes I was trying to link the MPE libraries to a finite element code already working in parallel on a cluster, I was just testing it locally.
As you suggest I will check the installation, perhaps I'll try to reinstall mpich with mpe.

thank you for the help, and merry christmas.

---

### Post by nick.not.used on 2009-01-06
Ok, it worked out without reinstalling mpich, I simply compiled a previous version of mpe (since I'm using mpich1 and not mpich2), with the flag --disable-F77 to the configure.

---

