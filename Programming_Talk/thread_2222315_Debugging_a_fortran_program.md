---
title: "Debugging a fortran program"
date: 2014-05-06
forum: Programming Talk
---

### Post by Chris_Laskaris on 2014-05-06
I am trying to compile and run a fortran program. The compilation seems to go successfully, but when I run it, I get the error message:

```
Segmentation fault (core dumped)
```

The program in question works for another user who uses Ubuntu (8.04.4) and a similar fortran compiler to mine (ifort 11.0), so I am sure that there isn't a fundamental error in the program. Instead, it seems that there is something in the code which my particular system / fortran compiler does not like. I am using Ubuntu 12.10, and the compiler I am using comes from the free Intel Fortran Composer XE 2013 for Linux package (for non-commercial use). My Intel fortran (ifort) compiler from this package is version 14.0.2.

So, basically, I am using a newer Ubuntu version than my friend, and a newer version / free variant compared to my friend's Intel fortran compiler, and while the program he compiles works for him, it does not work for me.

I am trying to find the source of the error. Based on info I read on this forum in the reply to another user's question, I tried the GDB debugger. However, when I run the program with it, it gives me a very generic error message that doesn't seem to provide any hint on what, exactly, is wrong:

```
Program received signal SIGSEGV, Segmentation fault.
0x08057b75 in MAIN__ ()
```

Does anyone know another debugger I could use, or have any general hints on what I might be able to do to try and get this program to work? I am thankful for any help!

---

### Post by spjackson on 2014-05-06
Welcome to the forums.

The short answer is that you need to build the program for debug in order for gdb to be able to show you the line in your source file where the program is crashing and to enable you to examine variables etc. As I do not use Fortran, I don't know how you do this; I expect there are some switches for the compiler and linker to do it. With gcc for C and C++ (and maybe Fortran too), you use the -g flag. Googling indicates that ifort has -g and -debug flags, so perhaps you need to investigate what these do.

---

### Post by Chris_Laskaris on 2014-05-06
Thank you for the reply.

My problem is that the program has to be compiled using a makefile, a perl script simply named mk. Otherwise, the compilation does not work - I think it needs to call up various routines. So I don't know how to build the program for debug in that manner. I don't even use the fortran compiler directly, as it were, instead it is called up by the script (which is very long and complicated).

---

### Post by ofnuts on 2014-05-06
I would be surprised if there were no way to introduce a debug flag somewhere (it could be an option of the script). Even the author needs to debug his stuff.

---

### Post by steeldriver on 2014-05-06
Does the makefile maybe have some kind of FLAGS variable (equivalent to CFLAGS) that you can overwrite on the command line or via your environment, telling it to add the relevant compiler options?

---

### Post by Chris_Laskaris on 2014-05-06
There are flags in the makefile (along with text descriptions of what they do), but there is none for debug.

Oh well. I guess there isn't much that can be done unless I can figure out how to, somehow, compile this with a debug option.

---

### Post by steeldriver on 2014-05-06
did you grep the makefile(s) for '-g' specifically e.g. something like this from the top of the source tree

```

find . -iname 'makefile' -exec grep -Hw -- '-g' {} \;

```

---

### Post by tgalati4 on 2014-05-06
It could be as simple as 32-bit versus 64-bit architecture.  I would presume the 8.04 machine is running in 32-bit (due to its age) and the 12.10 machine is running 64-bit.  You can't swap binaries this way.  If this was a C-compiled program, you would get a "Wrong Architecture" message instead of a segfault.  For both machines post the following:

```
uname -a
```

Why can't both machines use *gfortran* from their respective repositories?  At least using a consistent compiler will help troubleshoot the differences.  Errors that show up during compilation will give you a clue as to what are the bad actors.

As the others have said, you need to compile with debugging symbols in your code, otherwise it is a black box with no flashlight.

---

### Post by Chris_Laskaris on 2014-05-10
The problem is solved. I downgraded my compiler to ifort 11.0, same as the user's for whom the program works, and now it is working for me as well. Apparemtly, something changes between ifort 11.0 and 14.0.2 that caused the segmentation fault.

Thank you all for your replies.

---

