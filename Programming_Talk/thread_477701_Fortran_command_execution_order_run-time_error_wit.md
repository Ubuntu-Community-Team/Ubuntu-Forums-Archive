---
title: "Fortran command execution order run-time error with Intel 10 compiler"
date: 2007-06-18
forum: Programming Talk
---

### Post by jhollett66 on 2007-06-18
I can compile my code with no errors, but when I run I get a "Column count incorrect" error message.  Also I am plotting with gracebat, but the batch file is written after the system command to run gracebat(of course the writing of the batch file occurs before the grace command in my code).  What's going on? Is the error message related to my mixed-up I/O? 

Any help is appreciated

---

### Post by xtacocorex on 2007-06-18
Is the error from the FORTRAN code or the Bash script?  I do know that the newest Intel FORTRAN compiler has a lot of debugging output when you do stuff wrong (I crashed the stack in my Feisty VM with a FORTRAN code and it gave me pages of errors).

It could be you are calling an array out of bounds in the FORTRAN code.

---

### Post by jhollett66 on 2007-06-18
The code compiled for me and runs fine, producing the plot in grace with the batch file, on another computer(running mandrake, different processor, and likely intel 9 compiler).  But on this computer I compile fine, and when I execute it does produce the plot(runs grace), but without the batch file.  I have a feeling the "Column count incorrect" message is coming from grace when it tries to use the batch file that is still opened by the fortran program.

For some reason it runs the system(command) line in my code before the write to the batch file, although the write appears before.  I removed all optimization(-O0) but it still mixes it up.  Or at lest I think that's what's happening.

---

### Post by xtacocorex on 2007-06-18
You can use a system() call in FORTRAN?  I haven't tried that, nor have I messed with grace.

Is it FORTRAN 77 or 90?  It could be using a number jump out of order if it's 77 code to the system call.

---

### Post by jhollett66 on 2007-06-19
It's fortran 90.  The system call just appears after the write statements, and the close of the file, yet it seems to be executing before the close.  Weird!

---

### Post by jhollett66 on 2007-06-19
I can only think that it is the compiler doing something

---

### Post by jhollett66 on 2007-06-19
Found the problem, not the compiler or the code, it was the -fixed option I was giving grace.  The arguments it requires must have changed from the version I used on another computer.

Thanks anyways

---

### Post by xtacocorex on 2007-06-19
Glad you were able to fix the problem.

---

### Post by JamsSmith on 2012-03-16
Based on your description, it seems that you want to apply Intel Fortran V10 compiler.

Referring to your concern, for Intel Fortran Compiler 10, this version of the Intel compiler supports more from Microsoft Visual Studio 2005. VS2008 supports **[FONT=&quot]command line only[/FONT]** in this release.
Please check: [http://en.wikipedia.org/wiki/Intel_Fortran_Compiler#Versions](http://en.wikipedia.org/wiki/Intel_Fortran_Compiler#Versions)
Thus, if you're running VS2008, to apply Intel Fortran Compiler, I would suggest you to upgrade to Intel Visual Fortran Compiler 11.1.

For Intel Fortran Compiler 11, you can check the this helpful instruction of using Intel Visual Fortran Compiler 11, please see: [http://cache-www.intel.com/cd/00/00/40/59/405976_405976.pdf](http://cache-www.intel.com/cd/00/00/40/59/405976_405976.pdf) or [http://software.intel.com/en-us/articles/intel-fortran-compiler-for-windows-required-and-optional-microsoft-development-software/](http://software.intel.com/en-us/articles/intel-fortran-compiler-for-windows-required-and-optional-microsoft-development-software/).

BTW, this forum is for the support of Visual Studio installation. For Intel Fortran Compiler, you could post your thread on [Intel® Visual Fortran Compiler for Windows]("http://software.intel.com/en-us/forums/intel-visual-fortran-compiler-for-windows/") forum. You will get more useful help there.
   
  [http://www.techyv.com/questions/intel-fortran-run-time-error-help](http://www.techyv.com/questions/intel-fortran-run-time-error-help)

---

### Post by oldos2er on 2012-03-16
Closed, necromancy.

---

