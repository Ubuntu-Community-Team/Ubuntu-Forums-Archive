---
title: "Anjuta and running compiled programs"
date: 2006-10-29
forum: Programming Talk
---

### Post by WiseElben on 2006-10-29
I'm new to the Linux development environment, and I'm not really sure how to run my C++ programs. I compiled it (using Anjuta) and then, using the terminal, I type in <sudo ./main.o>, but I get this error: bash: ./main.o: cannot execute binary file

So basically, how the heck do I run my compiled C++ programs?

---

### Post by koala114 on 2006-10-30
Extension .o is a object code, it used to be linked with the libraries by Linker to create executable file.
In linux, the compiled executable file is extension .out. 
In this case, main.o is not a executable file

---

### Post by Brenlae on 2006-10-30
What you want to do is build, not just compile. If you click build it will create an executable. Run that by clicking Run from the same list or just run it from the command line.

---

### Post by Tiede on 2006-11-03
Hi. And how does one build a program in Anjuta 2.02... It's always greyed out in the build menu...

---

### Post by Relain on 2006-11-03
you could try using terminal. 
Cd to the directory where your project is saved, i don't remember how Anjuta organises this. Then see if there's a makefile, it'd be called Makefile. If there is you can see if it's good by just running make. 

Or you could compile the whole thing manually. Say you have two object files class1.cpp and class2.cpp and one main file main.cpp you'd run:

g++ -c class1.cpp -o class1.o 
g++ -c class2.cpp -o class2.o
g++ -o my_project.out main.cpp class1.o class2.o 

This is assuming you don't need any fancy include statements or have to link against any external libraries, not hard to do though.

So then you've compiled both of your classes into object files and the 3rd line compiles main.cpp and then links it against the class objects to produce my_project.out which you can now execute. Although you might have to: chmod 755 my_project.out if it's not already.

That should work, although it's not ideal. It's basically what the most simplistic uses of make do.

---

