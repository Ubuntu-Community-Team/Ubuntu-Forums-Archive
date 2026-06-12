---
title: "how can i program in C++? im new in linux"
date: 2008-08-27
forum: Programming Talk
---

### Post by macmoy on 2008-08-27
im very new to linux - ubuntu.

before, i make games using C++ in windowsXP.

here in linux how can i code in C++?

what compiler?

what IDE?

and PLEASE explain to me how to install those.

i cant understand how linux install apps.

im really confused!


Thanks for any help!!

---

### Post by howlingmadhowie on 2008-08-27
you can install apps using synaptic package manager. go to system->administration and select synaptic. it will ask you for your password. then you can select the applications you want to install. 

to get a c++ compiler you need build-essential. this will install the gnu c and c++ compilers. then you can use c++ or g++ on the command line to compile the program. i'm afraid i don't do much c++ programming, so i don't know which ide i'd recommend. eclipse and netbeans are also installable over synaptic, but they're pretty big and bloated.

---

### Post by leg on 2008-08-27
The easiest way to install apps in Linux is to open synaptic and search for the ones you want. When you have found the one you want installed click it and check install. When finished click apply (or whatever it is). As for compiling programs you have some choice.

First off install build-essential (not sure if that is the correct package name but someone will correct if not). That will install GCC which is the [Gnu Compiler Collection]("http://gcc.gnu.org/"). 

IDE:

personal favourite of mine would be Code::Blocks but not sure if that is in the repos or not. Search for it.

Eclipse can do C++ projects if you add the right plug in to it.

Geany is a great little editor

Gedit best text editor I have used (please no flame war)

I am sure others will give you more choices.

---

### Post by monkeyking on 2008-08-27
You can install all the relevant haeders and libs by installing
build-essential

```
sudo apt-get install build-essential
```

---

### Post by jespdj on 2008-08-27
[Please *READ THIS* before posting (We mean it)](http://ubuntuforums.org/showthread.php?t=832449)

---

### Post by dribeas on 2008-08-27
> **leg said:**
> Eclipse can do C++ projects if you add the right plug in to it.

That would be Eclipse CDT. Also consider Anjuta (gnome) or KDevelop (KDE). I use a text editor (vi, but any editor should suffice) and command line tools. Not as user friendly as an IDE though...

   David

---

### Post by macmoy on 2008-08-27
Thanks for your help guys!!!

I can now make C++ programs using GEDIT. then go to terminal then type:

g++ main.cpp -o main
./main

BUT! 

how about if it's not only 1 file (main.cpp)

for example:


```
//hello.h
#include<iostream>
using namespace std;

void display()
{
      cout<<"hello";
}


//main.cpp
#include "hello.h"

int main()
{
     display();
     return 0;
}

```

How can i compile/run that program?

I really appreciate your help guys!
Thanks!

---

### Post by leg on 2008-08-27
> **macmoy said:**
> Thanks for your help guys!!!

I can now make C++ programs using GEDIT. then go to terminal then type:

g++ main.cpp -o main
./main

BUT! 

how about if it's not only 1 file (main.cpp)

for example:


```
//hello.h
#include<iostream>
using namespace std;

void display()
{
      cout<<"hello";
}


//main.cpp
#include "hello.h"

int main()
{
     display();
     return 0;
}

```

How can i compile/run that program?

I really appreciate your help guys!
Thanks!
If the .h and .cpp files are in the same dir then the same command will suffice. If you mean you want to split into different dirs then you need to pass the paths in as args. Can't remember exactly but I think -L<path> for a lib and -l<path> for files. I hope thats correct anyway.

---

### Post by jespdj on 2008-08-27
You still have one *.cpp file there. You still use the same command to compile it:
```
g++ main.cpp -o main
```
If you have multiple C++ source files, it would simply be:
```
g++ main.cpp second.cpp third.cpp -o main
```
See the [online documentation for gcc](http://gcc.gnu.org/onlinedocs/). Please do some searching, for example for [linux c++ tutorial](http://www.google.nl/search?q=linux+c%2B%2B+tutorial&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:nl:official&client=firefox-a).

---

### Post by LaRoza on 2008-08-27
See the sticky the one that asks you to read it before posting and has a link to a guide on how to program in C++ step by step on Ubuntu, and links to tutorials.

---

### Post by macmoy on 2008-08-27
```
marc@marc-laptop:~/Programming/sample$ g++ main.cpp -o main
In file included from /usr/include/c++/4.2/backward/iostream.h:31,
                 from hello.h:1,
                 from main.cpp:2:
/usr/include/c++/4.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
main.cpp: In function ‘int main()’:
main.cpp:8: error: ‘Hello’ was not declared in this scope
main.cpp:8: error: ‘Im’ was not declared in this scope
marc@marc-laptop:~/Programming/sample$ 

```

it cant find the hello.h.
main.cpp and hello.h is on the same directory

---

### Post by mike_g on 2008-08-27
maybe try adding:
```
#include "hello.h"
```
to the top of the code in main.cpp

---

### Post by macmoy on 2008-08-27
YES!! it is now working, sorry, my fault..

guys, if I use ide like anjuta, will there be a button to compile automatically the files?

---

### Post by LaRoza on 2008-08-27
> **macmoy said:**
> 
guys, if I use ide like anjuta, will there be a button to compile automatically the files?

Most IDE's do have something like that, and it is great when it works, but when they don't work you are left with very little to go on. I suggest learning how things work first before automating it.

---

### Post by hessiess on 2008-08-27
You can use 'makefiles' to contain all the settings for the compiler

[http://www.gnu.org/software/make/](http://www.gnu.org/software/make/)

> before, i make games using C++ in windowsXP.

if you were using directX, you will need to learn OpenGL.

---

### Post by macmoy on 2008-08-27
i already know opengl a bit because before learning dx, i started to learn opengl.

guys! i have another problem.

where will i put the library of opengl?(gl.h,glu.h,glaux.h,opengl32.lib,glaux.lib,glu32.lib)

where shall i put those?

i got G++ using synaptic.

Thanks for any help guys!!!

Thanks!:)

---

### Post by MarkieB on 2008-08-27
no longer participating in ubuntuforums.org

---

### Post by stevescripts on 2008-08-27
> **LaRoza said:**
> Most IDE's do have something like that, and it is great when it works, but when they don't work you are left with very little to go on. I suggest learning how things work first before automating it.

+1 ... (again)

A little time spent with the command line will prove extremely valuable a bit later on.

Steve

---

### Post by leg on 2008-08-27
> **macmoy said:**
> Thanks for your help guys!!!

I can now make C++ programs using GEDIT. then go to terminal then type:
...
Open Gedit and click on Edit >> Preferences and select the plugins tab. From there you have some choice of extra function to help you along. One you may find interesting is Embedded Terminal. Check it and then click done. Now go to View >> Bottom Pane and you have a terminal screen at the bottom of your editor to use.

You can now take LaRozas and other peoples advice and use the command line to learn how to use GCC without having to keep changing windows to get to it.

Some of the other plugins may interest you also.

---

### Post by LaRoza on 2008-08-27
> **leg said:**
> Open Gedit and click on Edit >> Preferences and select the plugins tab. From there you have some choice of extra function to help you along. One you may find interesting is Embedded Terminal. Check it and then click done. Now go to View >> Bottom Pane and you have a terminal screen at the bottom of your editor to use.

Some of the other plugins may interest you also.

Install "gedit-plugins" as well. I find the file browser tab, the highlight current line, and highlight matching braces to be very useful as well.

---

### Post by slavik on 2008-08-27
> **jespdj said:**
> [please *read this* before posting (we mean it)](http://ubuntuforums.org/showthread.php?t=832449)

qft.

---

### Post by dwhitney67 on 2008-08-28
> **macmoy said:**
> i already know opengl a bit because before learning dx, i started to learn opengl.

guys! i have another problem.

where will i put the library of opengl?(gl.h,glu.h,glaux.h,opengl32.lib,glaux.lib,glu32.lib)

where shall i put those?

i got G++ using synaptic.

Thanks for any help guys!!!

Thanks!:)
Please use the command line to compile programs.  Once you understand that (i.e. the 101 of s/w development), then you can migrate to using an IDE.

Please heed this advice.  Others have already written the same.  Don't disregard it by using anjunta or Eclipse.  Use the command line of a (gnome) terminal!!!

Peace!

---

### Post by macmoy on 2008-08-28
YES. Im using the Terminal.

My questions is where is the compiler located?(include & lib folder)

so that i can see if there's the opengl sdk or not.

---

### Post by dwhitney67 on 2008-08-28
The compiler/linker is g++.

Typical open-source libraries are located in /usr/lib and /lib.

If yours is not there, then you use the -L option to specify the location.  To specify the library name that you want linked in with your program, then you use the -l (lowercase l) and the library name minus the 'lib' and extension.

For example:
```
g++ MySuperProgram.cpp -L/home/snoopy/lib -lsnoopy
```

'snoopy' of course refers to libsnoopy.so (or libsnoopy.a), which is located in the directory /home/snoopy/lib

P.S.  There are other options that can be passed to 'g++'; refer to the man-page for additional information.

P.S.S.  There are instances when the -L option is not required (because the library is in /usr/lib or /lib), but nevertheless you need to specify the library you want linked to the program.  In this scenario only the -l (lowercase l) and the shortened library name (as demonstrated above) are required.

---

### Post by Xealot on 2008-08-28
> **macmoy said:**
> 
where will i put the library of opengl?(gl.h,glu.h,glaux.h,opengl32.lib,glaux.lib,glu32.lib)


I might be wrong, so ignore/correct me if I am, but arent .lib files windows static libraries?

If they are, you cannot use them here. They are simply compiled for the wrong platform..

---

### Post by slavik on 2008-08-28
> **Xealot said:**
> I might be wrong, so ignore/correct me if I am, but arent .lib files windows static libraries?

If they are, you cannot use them here. They are simply compiled for the wrong platform..
you are correct.

@OP: use synaptic for installing libraries. there's a reason we like package managers :)

---

### Post by Zugzwang on 2008-08-28
> **Xealot said:**
> I might be wrong, so ignore/correct me if I am, but arent .lib files windows static libraries?

No, you are wrong. ;-) .lib files can be *either* static libraries or tell the linker about the functions available in a dynamic library (and how it is called). So if you've got a windows .dll file, you run it through the IMPLIB (correct?) tool and get a .lib file you need to link against to use this functions right from the start of your program.

@OP: Anyway, the .h and .lib files from Windows should *not* be copied for compiling the stuff in Linux. The .h files also might be slightly different. Follow the instructions above since the build process in Linux is totally different in comparison to the (usual) Windows build process.

---

### Post by Xealot on 2008-08-28
> **Zugzwang said:**
> No, you are wrong. ;-) .lib files can be *either* static libraries or tell the linker about the functions available in a dynamic library (and how it is called). So if you've got a windows .dll file, you run it through the IMPLIB (correct?) tool and get a .lib file you need to link against to use this functions right from the start of your program.


Whoops, Only partially correct then. Thanks for the correction. :KS

---

