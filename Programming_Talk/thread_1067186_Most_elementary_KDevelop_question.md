---
title: "Most elementary KDevelop question"
date: 2009-02-11
forum: Programming Talk
---

### Post by dargaud on 2009-02-11
Hello all,
I'm an experienced programmer and I've been developing for Linux for years but I've always hand-crafted my own makefiles. I tried to get to use KDevelop a few times before but never could get past the most elementary problems...

OK, so I can get the Hello World example to compile and run... but how do I add a second .c file to the project ?!? I've gone 3 times through all the menus and submenus and I don't have a clue.

Thanks

---

### Post by Zugzwang on 2009-02-12
The answer is: It depends on the type of your project. In this post, I assume that you made a new "Hello World project"-

For adding *new* files, you can simply try File->New. For adding existing files, click on the "Automake Manager" at the right border of the window and right-click on the build target in the lower half of the manager panel. It has some adding functionality.

---

### Post by dargaud on 2009-02-12
> **Zugzwang said:**
> For adding *new* files, you can simply try File->New.
D'oh! I had no idea that it would add them to the project at the same time. Even seems completely wrong to me...

> For adding existing files, click on the "Automake Manager" at the right border of the window and right-click on the build target in the lower half of the manager panel. It has some adding functionality.
Well, I could have stared at their user interface for a year without noticing that thing. Grumble stupid grumble interface grumble design.

But I lied when I said I did compile a hello world (it did work on another install). Even that won't work, and I've tried both the normal and the CMake (same results with less cruft in the latter):
```

cd '/home/dargaud/Dargaud/WebPageStuff/AccessLog/AnalyzeCounterLin/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
make all-recursive
Making all in src
linking analyzecounterlin (CC)
../libtool: line 818: X--tag=CC: command not found
../libtool: line 851: libtool: ignoring unknown tag : command not found
../libtool: line 818: X--mode=link: command not found
../libtool: line 985: *** Warning: inferring the mode of operation is deprecated.: command not found
../libtool: line 986: *** Future versions of Libtool will require --mode=MODE be specified.: command not found
../libtool: line 2223: X-O0: command not found
../libtool: line 2223: X-g3: command not found
../libtool: line 2392: Xanalyzecounterlin: command not found
X: user not authorized to run the X server, aborting.
../libtool: line 2404: Xanalyzecounterlin: command not found
../libtool: line 2412: mkdir /.libs: No such file or directory
mkdir: cannot create directory `/.libs': Permission denied
make[2]: *** [analyzecounterlin] Error 1
make[2]: Target `all' not remade because of errors.
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

```
I can find those errors on google but the solutions are surprisingly not helpful. I'm absolutely not familiar with automake and autoconf.

Why is there an 'X' prepended to compiler options, file names and others ?!? If that's not a bug I don't know what is !

---

### Post by Krotow on 2009-03-08
Cause of bug is clearly wisible :)

> ../libtool: line 2412: mkdir /.libs: No such file or directory

libtool was tried to create a directory ".libs" into system root directory. And I assume, you're not working as root and your user account don't have a write permission for "/". Of course, it is a libtool related error that must be fixed ASAP. By now you may use a workaround: create an empty directory into system root directory "/" and give permission 777 for it.

---

