---
title: "Makefile problems"
date: 2008-09-06
forum: Programming Talk
---

### Post by Andruk Tatum on 2008-09-06
I am trying to develop a makefile for the open source version of [OpenQM]("http://www.openqm.com/cgi/lbscgi.exe").  It originally comes with a build script, but the build script compiles everything at once, even if only one file changes.  I am trying to stick to the same directory structure that it comes with, which is:
gpl.qmsys/        <-- Parent directory
gpl.qmsys/gplsrc/  <-- Source directory
gpl.qmsys/gplobj/  <-- Object directory
gpl.qmsys/bin/     <-- Binary directory (for executables)

I am trying to get the makefile to compile everything from gplsrc/ into objects (named correspondingly) in gplobj/, and then link the objects together into the executable in bin/.  So far, I can get make to link the main target (qm) out of the objects, but I cannot get make to update any of the objects.  It returns, "make: `../bin/qm' is up to date."

I have attached my makefile (kept in gplsrc/ for now) and the original build script, any input is greatly appreciated.

-- Andruk

---

### Post by nsche on 2008-09-06
Some general observations on your makefile (this based on my experiences in building makefiles for some large systems)

1 - I would suggest you use something like makedepend (you can use gcc -M to make sure everything is sollowed the same) to generate header file dependencies. 
 
2 - Your dependencies are not really the best.  The objects are dependent on the .c and .h files.  The library is dependent on the objects.  The executable is dependent on the libraries that it uses.  You are better off using small steps.  Makedepend or gcc -M will do the .o to .c and .h part.

---

### Post by Andruk Tatum on 2008-09-07
Here is my updated makefile.  I have removed the headers prereq for the first target (qm).  It is now compiling every prerequisite for qm in its corresponding object except for qm.c, even though qm.c is in the prerequisites list for qm.  It bails on the linking after it can't find ../gplobj/qm.o, even though the implicit rule .c.o should have compiled it into ../gplobj/qm.o.

Thanks for your help.
-- Andruk

---

### Post by nsche on 2008-09-07
I would run ```
make -d > /tmp/debug
```I am sure you will find qm is not dependent on qm.o.  You probably need to add qm.o as an explicit dependency of qm and that will cause qm.c to be compiled.

I cannot really tell if that is correct because you have the list of sources in a file instead of listing them in the makefile.

---

### Post by Andruk Tatum on 2008-09-07
I just found the problem.  I had an extraneous qm.o in gplsrc, and so make was seeing the prerequisite, but the command that was being run was not finding a qm.o in gplobj (because it wasn't there).  Make was also not compiling qm.c because it saw the updated qm.o in gplsrc.

Thanks for your help.  I think it works now.  I have uploaded the latest makefile, I'm fairly certain it works for the default (first) goal.  I will continue to work on it, and upload the makefile that works for all of the goals.

-- Andruk

---

### Post by Andruk Tatum on 2008-09-07
Here is the final makefile, simply change the "PARENT" variable to "./" (without the quotes) if you move it from the gpl.qmsys/gplsrc directory to the gpl.qmsys directory.  You will also need to rename the file to simply Makefile (remove the .txt extension) to get it to do anything.

Thanks for your help.

Reply if you have any problems.
-- Andruk

---

### Post by nsche on 2008-09-09
A few observations:
1 - As a long time Unix programmer I really like to see my separators.  This is probably because I splice strings in shell scripts by putting macros with strings.  I would prefer to see something like:
```
MAIN     := ..
GPLSRC   := $(MAIN)/gplsrc
GPLDOTSRC := $(MAIN)/gpl.src
```Then when they are used they look like regular Unix/Linux paths.
2 - The .c.o rule should only compile a .c file to a .o file with the same name.  I guess you have it as you do because for some reason you want your objects in a directory above your build location.  I don't understand why you would complicate life like that.  A makefile generally is for building the files in a single directory.  In systems I have built if they are very large I have a makefile that invokes makefiles in subordinate directories as needed.  Would your system work to just build the executables and libraries in a single directory and then have a copy stanza to move things (if newer) to the installed directory?  Life is complicated enough without doing things in a way some other person will find hard to understand.
3 - If you have any header (.h) files that are not part of the system include files, you need to account for the dependancies of the objects on those header files.  I recommend using makedepend with a DEPEND: target to automaticly generate those dependencies.

You have a good start but remember makefiles are for making things easier and more reliable.

---

