---
title: "How to check for errors in code without compiling?"
date: 2010-05-01
forum: Packaging and Compiling Programs
---

### Post by ZequeZ on 2010-05-01
Well, I'm really starting with that ".configure" and "make" thing... And today I realized that for large programs, a "make" may take a looooong time... So, there is a way to check for errors without actually compile the program? Because it sucks when it find errors after 15 min of the start =/

---

### Post by Bachstelze on 2010-05-01
No, because the only way to "know" whether or not an error will occur is to execute the program (in that case, the compilation). One could probably convert that to the halting problem.

---

### Post by SevenMachines on 2010-05-01
Remember, 'make' looks to recompile only files who have changed since it was last run. In theory if you 'make' a 1000 file project and then change one file, only that 1 file will be recompiled on a following 'make'. In practice obviously any other files that depend on the changed file will themselves be recompiled too and so on. For this reason you'll often find that changing a source file might only cause a short recompile whereas changing a header file causes a much larger one since it is #include'd by any number of others

---

### Post by MadCow108 on 2010-05-01
There are IDE's which do fast partial compilation as you type. Visual studio for example.
I think netbeans is a free IDE capable of doing that but unfortunately gcc is not well suited for that. Consider using LLVM and clang.


you can make in verbose mode (which is mostly default)
make V=1
then copy paste the command which compiles your particular edited file and execute it by hand.

This may save you some time when modifying headers which are included in all other files, forcing long recompilation.

If you only modify source files make should compile the minimal requirements by itself. If you are doing that and make compiles everything your Makefile make be suboptimal (I have seen projects where make executes a rm *.o before compiling...)

For C++ you can use the pimple (pointer to implementation) design idiom do avoid long compilation times which is a huge problem in C++.

If the linking is a problem, consider using the gold linker in binutils (still beta)
It is supposed to be quite a bit faster than ld

---

### Post by conradin on 2010-05-01
Hm, Doesnt Qdevelop also provide partial compilation?

---

### Post by Bachstelze on 2010-05-01
IDEs aren't really a solution here, though. If I understand correctly, what the OP wants is download a piece of software as a source tarball and know beforehand whether or not compilation will be successful. It's different from a programming project of your own in an IDE.

---

### Post by MadCow108 on 2010-05-01
if you have a multicore pc you can increase the speed by compiling in parallel
increase the number of jobs with the -j flag of make

you can also use distcc to compile on several connected computers in parallel

---

### Post by ZequeZ on 2010-05-02
> **SevenMachines said:**
> Remember, 'make' looks to recompile only files who have changed since it was last run. In theory if you 'make' a 1000 file project and then change one file, only that 1 file will be recompiled on a following 'make'. In practice obviously any other files that depend on the changed file will themselves be recompiled too and so on. For this reason you'll often find that changing a source file might only cause a short recompile whereas changing a header file causes a much larger one since it is #include'd by any number of others

I didn't know that! :O
Thanks ^^

[QUOTE=MadCow108]
if you have a multicore pc you can increase the speed by compiling in  parallel
increase the number of jobs with the -j flag of make

you can also use distcc to compile on several connected computers in  parallel 	[/QUOTE]

Thanks! It's a very useful parameter, it should use it by default xD.

---

