---
title: "Eclipse C++"
date: 2007-10-01
forum: Programming Talk
---

### Post by sdmike on 2007-10-01
What is the quickest way for me to get Eclipse with C++?

Also can some show me a tutorial on how to build and make my C++ projects?

---

### Post by Natr0n on 2007-10-01
```
$ sudo apt-get install eclipse eclipse-cdt
```also [ [COLOR="Blue"]_CDT - Eclipsepedia_[/COLOR]]("http://wiki.eclipse.org/index.php/CDT")

---

### Post by sdmike on 2007-10-01
So I got it installed. I made a project and added a source file with the very cool originall hello world code. 

I saved the project but it won't compile. 

What am I missing here?

Does anyone have a picture tutorial?

---

### Post by Natr0n on 2007-10-01
What kind of errors are you getting?

---

### Post by sdmike on 2007-10-01
when I click on Buil-all

the console does nothing in eclipse it just says
[COLOR="Red"]
make -k all 
make: *** No rule to make target `all'.[/COLOR]

and stays that way so I can never run anything.

---

### Post by Natr0n on 2007-10-01
[[COLOR="Blue"]Creating a simple Standard C++ Project[/COLOR]]("http://wiki.eclipse.org/CDT/User/FAQ#Creating_a_simple_Standard_C.2B.2B_Project_--_.22Hello_World_on_a_Windows_Platform.22")
Nevermind the Windows Platform stuff, the instructions should still apply. I think step 7 is what you're missing (the part about editing the makefile).

---

### Post by sdmike on 2007-10-01
when I made the makefile and then built the project I get this error in console about the make file.
```

make -k all 
makefile:2: *** missing separator.  Stop.
```

this si what is in the make file
```

     hello.o : hello.cpp
     	g++ -c hello.cpp

```

---

### Post by Natr0n on 2007-10-01
Put this in the makefile
```

hello.exe : hello.o
     	g++ -o hello.exe hello.o

hello.o : hello.cpp
     	g++ -c hello.cpp
     	
all : hello.exe
clean :
     	-rm hello.exe hello.o

```
and make sure that on all lines that are indented you have inserted ***one*** tab and no spaces or anything else before the text or else make won't be able to understand the makefile.

---

### Post by Natr0n on 2007-10-01
It might be easier to start over and select "Managed C++ Project", then follow these instructions:  [[COLOR="Blue"]Creating a simple Managed C++ Project[/COLOR]]("http://wiki.eclipse.org/CDT/User/FAQ#Creating_a_simple_Standard_C.2B.2B_Project_--_.22Hello_World_on_a_Windows_Platform.22"). That way you don't have to goof around with the makefile - it will be automatically generated.

---

### Post by sdmike on 2007-10-01
that would be awesome.

So originally when I was using Gedit and compiling in the terminal it was making a makefile for me automatically?

---

### Post by sdmike on 2007-10-01
so get this when I save it says this:
```


**** Build of configuration Debug for project lab6 ****

make -k all 
Building file: ../hello.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"hello.d" -MT"hello.d" -o"hello.o" "../hello.cpp"
../hello.cpp:8:2: warning: no newline at end of file
Finished building: ../hello.cpp
 
Building target: lab6
Invoking: GCC C++ Linker
g++  -o"lab6"  ./hello.o   
Finished building target: lab6
 
Build complete for project lab6
```

my code is this

```
#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}
```

I can't run it because it says this error

warning: no newline at end of file

What am I doing wrong here?

---

### Post by CptPicard on 2007-10-01
You should be able to run it, the build finishes ok but with a warning, which means what it says... the compiler expects a newline at the end of file... press enter at the end of file :p

---

### Post by sdmike on 2007-10-02
got it!!!
I didn't know it was automatically building my project.

That is kinda cool.

Ok now I can go forth and actually work on my projects.

---

