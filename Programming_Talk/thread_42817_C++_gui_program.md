---
title: "C++ gui program"
date: 2005-06-19
forum: Programming Talk
---

### Post by ante0 on 2005-06-19
Hi, i've been searching on google for a c++ program with gui, but havnt found any good. can you recommend some to me? 

I want to learn c++ in linux, but i cant just make a *.cpp file and then run gcc *.cpp in a terminal, beacuse it probably needs a makefile, so it gets errors. so i thought of getting a gui version...
 
Please, help =)

---

### Post by cwaldbieser on 2005-06-19
I am not sure from your post whether you are trying to learn to program in C++ or whether you want to compile and existing C++ program.  It seems you are looking for a graphical IDE to manage the compiling aspect of the project.  

I can't say that I have really used a graphical IDE for compiling C++ programs in Linux, but I seem to recall that the Eclipse project had some support for C++.      KDevelop also springs to mind for some reason.

If you are just learning to program in C++, you probably don't need to worry about makefiles until your programs start spanning lots of files.  If you are just starting out with toy programs, you can do the following:
```

$ ls
myfile.cpp
myfile.h

$ g++ myfile.cpp
$ ls
myfile.cpp
myfile.h
a.out
$ ./a.out
Hello, C++ World!
```

If you are trying to compile source code from a project (from the Internet, maybe), many times the configuration scripts and the makefile are already in place:

```
$ ./configure
Blah blah blah
Configure is complete.  Now run make.  Good Luck!
$ make
$ sudo make install
```

---

### Post by ante0 on 2005-06-19
yeah, i know how to compile a program.
But, im using a C++ tutorial which i found out had lots of errors in their code. Im searching for a Borland C++ alike program for linux, i would have used wine/wineX with borland c++ but it isnt working that good with linux.

And yes, i just want to toy around some with example code i found in the tutorial.
But do i need to have a makefile if i just want to print the results of the code in a terminal? 

I tried with the code i got from the tutorial, put it in a *.cpp file and typed gcc *.cpp in a terminal. But it gave me lots of errors, plus, the iostream.h file that is included takes lots of time to go through.

---

### Post by ante0 on 2005-06-19
Oh, i know what the problem was... i didnt use the command c++ before, just gcc ;)
Oh well, thanks anyway! (But i still wonder if there are any Borland C++ alike programs for linux out there =))

---

### Post by Kimm on 2005-06-20
As far as I know there arent realy any good C++ GUI designers for Linux, by that I mean like Borland, there is Glade but it only designes the GUI and doesnt let you write the rest of the code. If your using KDE QtDesigner might be of interest, I have never used it myselfe but I think its somewhat like VB/Borland.

Another nice IDE is Anjuta for Gnome, it doent designe GUI's but its realy nice anyway ^^

If you realy need this, you can try Borland Kylix, its a free program and it includes a Delphi and a C++ compiler with GUI designers. Personaly I realy realy dont like it however, I have never managed to sucessfully compile a program in Kylix, when I press compile the program simlpy locks up and doesnt let me do anything, and it stays like that untill I kill it from a terminal. I also hear it has graphics problems in Ubuntu

---

### Post by stubby on 2005-06-20
[QUOTE=ante0]yeah, i know how to compile a program.
But, im using a C++ tutorial which i found out had lots of errors in their code. Im searching for a Borland C++ alike program for linux, i would have used wine/wineX with borland c++ but it isnt working that good with linux.

And yes, i just want to toy around some with example code i found in the tutorial.
But do i need to have a makefile if i just want to print the results of the code in a terminal? 

I tried with the code i got from the tutorial, put it in a *.cpp file and typed gcc *.cpp in a terminal. But it gave me lots of errors, plus, the iostream.h file that is included takes lots of time to go through.[/QUOTE]
 to compile c++ (.cpp) programs you use g++, instead of  plain c (.c) program, which uses gcc

Seems you figured it out, Just posting in case anyone else comes searching.

---

### Post by ante0 on 2005-06-20
I think i will try Kylix and Anjuta =)
Thanks for all the help.

I've tried Glade and as you say, it doesnt let you do any coding, just inserting buttons/windows/whatever. 

If none of Kylix or Anjuta work, i will just go with the oldfashioned way, coding in a texteditor and save to a .cpp file and then run c++ *.cpp.

Now that i think of it, i dont need a program that can create GUI programs. but a program that uses graphics, doesnt have to be fancy at all, just so it has a built-in editor and a compile/build button =P

Thanks again!

---

### Post by trivialpackets on 2005-06-20
[QUOTE=ante0]I think i will try Kylix and Anjuta =)
Thanks for all the help.

I've tried Glade and as you say, it doesnt let you do any coding, just inserting buttons/windows/whatever. 

If none of Kylix or Anjuta work, i will just go with the oldfashioned way, coding in a texteditor and save to a .cpp file and then run c++ *.cpp.

Now that i think of it, i dont need a program that can create GUI programs. but a program that uses graphics, doesnt have to be fancy at all, just so it has a built-in editor and a compile/build button =P

Thanks again![/QUOTE]
 Then anjuta will be right up your alley.  It's my gui of choice for my playing around in C++

---

