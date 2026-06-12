---
title: "cannot compile openmp in gcc 4.2"
date: 2007-10-22
forum: Programming Talk
---

### Post by carl.alv on 2007-10-22
Hi all!

I have just updated my pc to ubuntu gutsy and I wanted to make som parallel programing with libgomp, but im using -fompenmp and i cannot compile the program, the compiler sais:

cc1plus: error: unrecognized command line option "-fopenmp"
 
and it allso does not find the omp.h header. Anyone that has allready used openmp in gcc 4.2 can help me?

---

### Post by duff on 2007-10-22
Are you sure you're using 4.2? "gcc" is gcc-4.1.2 for me.  I need to use "gcc-4.2" for omp.

---

### Post by carl.alv on 2007-10-23
When I try gcc-4.2 it tells me

gcc-4.2 -O3 -m64 -lm -fopenmp -o Hello_para ompHello.cc
gcc-4.2: error trying to exec 'cc1plus': execvp: No such file or directory

:(

---

### Post by duff on 2007-10-23
Since your using C++, run "g++-4.2" instead.

---

### Post by carl.alv on 2007-10-24
yes, I instaled the gcc-4.2 source files (which I dont know if are needed) and the g++-4.2 with sudo apt-install and now I can compile the program, but there is a think that does not work properly still. 

The program looks like this:

```
#include <iostream>
#include <omp.h>
using namespace std;

main(){
  #pragma omp parallel
  {
     cout << omp_get_thread_num() << " test1" << endl;
  }
  cout << "test2" << endl;
}
```

if I compile it using -fopenmp i works fine, but if I do it without this option it does not work, which means that he is thrying to read the omp_get_thread_num() function. I thought that the pragma thing was supposed to tell the compiler that it should compile the omp directives only if the -fopenmp option was given. So now Im confused. :confused:

---

### Post by carl.alv on 2007-10-25
OK, now it works! I was not including the -lgomp :p

---

### Post by retrow on 2007-11-16
> **carl.alv said:**
> When I try gcc-4.2 it tells me
gcc-4.2 -O3 -m64 -lm -fopenmp -o Hello_para ompHello.cc

I tried using omp.h for a c program to create a ssh tunnel and bring up vnc interface. My program still has bugs, but there are no error wrt "** #include <omp.h>**"

I used

[INDENT]*gcc-4.2 -o sshTunnelVNC sshTunnelVNC.c -lm -fopenmp*[/INDENT]

*-lm* is kinda meaningless in the program, but its compiling without error in Geany.

---

