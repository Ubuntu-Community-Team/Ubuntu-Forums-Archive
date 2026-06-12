---
title: "[C++] Is There a Reason to Create an Object File?"
date: 2010-05-11
forum: Packaging and Compiling Programs
---

### Post by dodle on 2010-05-11
For example, with these three files in the source directory: test.cpp mylib.h mylib.cpp

I don't know a whole lot about compiling, but wouldn't the following two sets of commands do the same thing?
```
g++ test.cpp mylib.cpp mylib.h -o test
```
```
g++ -c mylib.cpp
g++ test.cpp mylib.o mylib.h -o test
```
I understand that to make a shared or static library you need to create the object file, but am I correct in saying that in this example both methods do exactly the same thing?

---

### Post by Tony Flury on 2010-05-11
The major benefit is when you have a complex project with multiple source files.

If you can simply check the dates of your object files against your source file, and avoid need to recompile the source files that have up to date object files, you can vastly improve your rebuild times - since compile times can be long.

This methodology is exactly that used by the make utility, when you define a make target and its sources, it will only reconstruct the target if either the target does not exist or the target is less recent than one of it's sources.

In your case you could edit mylib.cpp (without changing test.cpp) and only need to rebuild mylib.o (and of course relink it) without recompiling test.cpp

---

### Post by dodle on 2010-05-11
Thank you for the info.  I have yet to build a very large C++ project.

---

### Post by MadCow108 on 2010-05-11
in your example both commands do exactly the same
in both cases the compiler compiles both source files to object files and then links them
just in the first case the object files get deleted in the end.
but you can keep them (along with a few other files) with the flag -save-temps, but they get regenerated when you run the command again

this deletion is also the reason you often do it in separate steps in bigger projects, because you can avoid recompilation, and you can reuse the object files for other executables.

also you shouldn't add headers to the command line. headers should be included by the source files over #include

side note: in C you can actually combine the files to a single source file and compile the whole thing with the -combine flag, this allows for better optimization (use with -fwhole-program for best effect)

---

### Post by dodle on 2010-05-11
I didn't know that headers were not necessary in the command line.  Thank you.

---

