---
title: "how to set path to include g++ libraries"
date: 2008-02-29
forum: Programming Talk
---

### Post by bebops_lost on 2008-02-29
(please pardon the repeat post, I put this up in another section and was advised it was more appropriate here.)

I have done a fair bit of programming in c++, but I am pretty much a nube at Linux.

I've written a c++ code that has dependencies on gsl (gnu scientific library) and I had thought that setting the compiler to include the path to link with your libraries involves adding a simple line to the .bashrc file. For me it has not been so simple.
I've run it several times on other computers, so I know the code itself is bug-free, but it won't link when I try to compile it at home using this: 

$ g++ program.cpp -o executable.x
(I also tried using -lgsl, and a few others at the end of this)

my .cpp file starts off like this:

#include <gsl/gsl_sf_log.h>
#include <gsl/gsl_sf_airy.h>
// plus a few other "includes" let's just use these 2 as an example

int main(int argc, char *argv[])
{
double x = gsl_sf_log(3.5);
double y = gsl_sf_airy(2.9);

return 0;
}
//--------------------------------------------------
and then I edited my .bashrc file to include the following 2 lines:

export CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/usr/local/ include/
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/include
// I also tried putting ~ symbols before the :

so then I saved copies of all of the header files such as " gsl_sf_log.h" and "gsl_sf_airy.h" in a folder (gsl) i created : 
/usr/local/include/gsl

and I also saved libgsl.a, and libgslcblas.a, in that same folder as well as the corresponding .def, and .dll.a files. 
Just to be redundant I also tried saving copies of all the above files in /usr/local/include itself as well as /usr/local/lib . I also saved copies of all these files in the directory that I'm working in, and I also tried replacing the #include <> commands with #include "" 
then, of course I restarted my terminal program to reload the .bashrc file and tried to compile it as above; I got :
error
undefined reference to `gsl_sf_log'
undefined reference to `gsl_sf_airy_Ai'

anybody know what I'm doing wrong?
-B
__________________

---

### Post by k2t0f12d on 2008-02-29
Have you tried adding -Ipath/to/the/header to your g++ call?  i.e.
```
$ g++ -Ipath/to/the/header program.cpp -o executable.x
```

[COLOR="Sienna"]EDIT: ++ what volanin said ---VVV[/COLOR]

---

### Post by volanin on 2008-02-29
**-I** : Sets the path to the include files.
**-L** : Sets the path to the libraries.
**-l** : Use this library (eg. **-l**m to use libmath.so, **-l**pthread to use libpthread.so)

You can have multiple **-I**, **-L** and **-l** entries.
So, your final command should look like this:

*g++ program.cpp -o executable -I /path/to/includes -L /path/to/libraries -l library1 -l library2*

---

### Post by WW on 2008-02-29
> **bebops_lost said:**
> 
export LIBRARY_PATH=$LIBRARY_PATH:/usr/local/include
The library files would be in /usr/local/lib.


GSL uses pkg-config, so an alternative would be something like this:


program.cpp
```


#include <iostream>
#include <gsl/gsl_sf_log.h>
#include <gsl/gsl_sf_airy.h>


using namespace std;

int main(int argc, char *argv[])
{
double x = gsl_sf_log(3.5);
double y = gsl_sf_airy_Ai(2.9,GSL_PREC_DOUBLE);

cout << "x = " << x << endl;
cout << "y = " << y << endl;

return 0;
}
```

Examples of pkg-config:
> 
$ pkg-config --cflags gsl
-I/usr/local/include  
$ pkg-config --libs gsl
-L/usr/local/lib -lgsl -lgslcblas -lm  
$


Use pkg-config to compile and run program.cpp:
> 
$ g++ $(pkg-config --cflags gsl) -c program.cpp
$ g++ program.o $(pkg-config --libs gsl) -o program
$ ./program
x = 1.25276
y = 0.00788631
$ 
 
I installed the GSL library from source, and it is installed in /usr/local.  If you use the Ubuntu packages, the files are in /usr (i.e. the include files are in /usr/include, and the libs are in /usr/lib).

EDIT: It looks like pkg-config is not installed by default, so to use pkg-config, you'll have to install the Ubuntu package that has the command, called appropriately **pkg-config**. E.g.
> $ sudo aptitude install pkg-config
or use Synaptic Package Manager.

---

### Post by bebops_lost on 2008-02-29
Thanks everyone.
after I copied all the header files from the servers directory to an ~/include/gsl/ folder I made myself, and copying the lgsl.a and lgslcblas.a files to  ~/lib/ and then typing:
 g++ elogstates.cpp -o elog.x -lgsl -lgslcblas
as long as my .bashrc files contain these lines:
export CPLUS_INCLUDE_PATH=$CPLUS_INLUDE_PATH:~/include:/..../gsl/current/include
export LIBRARY_PATH=$LIBRARY_PATH:~/lib:/opt/..../lib
then it compiles properly. I really don't see how this is any different from what I was doing before (since both the server /include/ folder and my user /include/ folder were supposed to be included) but it works now... maybe I was copying things down wrong somehow, but at this point I think it was just *magic*.
thanks anyway:
-B

---

