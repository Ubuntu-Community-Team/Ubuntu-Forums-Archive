---
title: "Undefined reference to 'main' error in crt1.o function _start"
date: 2012-06-18
forum: Programming Talk
---

### Post by nigel332 on 2012-06-18
Hello,all
    I've geting problems with my Makefile.
    I'm trying to create a program:peg_in.but,When I try to make using this Makefile, I get the error:
    cc -lm  peg_diag.o   -o peg_diag
/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld return 1

AND my makefile as follows:

```
 12 F90 =             gfortran-4.4
 13 F90FLAGS =  -DDEC_ALPHA
 14 CPP =             gcc -E
 15 CPPFLAGS =  -DLINUX -DD_PRECISION
 16 LDFLAGS =   -lm
 17 LIBS =
 18 CMPLFLAGS =       linux

```

---

### Post by Zugzwang on 2012-06-18
The "peg_diag.o" - where does it come from? Is it compiled from C source code? If yes, does it have a "main" function? If not, then the code that is to be executed upon starting the program is missing, and thus, you can't link it (before you defined a main function).

I don't think that the Makefile provided is the one that you've used: There is no rule for invoking "cc", and this is the step for which you have a problem.

---

### Post by trent.josephsen on 2012-06-18
This probably is the makefile he used -- the rules for making object files and executables from .c files are built in.

However, you're right in that the makefile is completely irrelevant to the output he's seeing, since the files he's trying to make match none of the rules in the file.

---

### Post by nigel332 on 2012-06-18
> **Zugzwang said:**
> The "peg_diag.o" - where does it come from? Is it compiled from C source code? If yes, does it have a "main" function? If not, then the code that is to be executed upon starting the program is missing, and thus, you can't link it (before you defined a main function).

I don't think that the Makefile provided is the one that you've used: There is no rule for invoking "cc", and this is the step for which you have a problem.



hi,thanks for your answer!

I edit my makefile as shown in the question discribe.
And we see that the "peg_diag.o"   comes form peg_diag.F90, as shown in the follows:

peg_diag:	peg_diag.o
	$(F90) $(F90FLAGS) -o peg_diag peg_diag.o \
	$(LDFLAGS) $(LIBS)

these days i asked many people about this problem. As my code write with fortran~~~~ Most of them said there maybe something wrong with my link to the code strting~~~But i just cannot slove it~~~
thanks for help~~

---

### Post by trent.josephsen on 2012-06-18
Ok, now you're *definitely* not posting the error the posted makefile gave you. Run make again and post the new output.

---

### Post by nigel332 on 2012-06-19
it needs "/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o" to compile peg_diag. And function main is invoked for crt1.o. But, I write my code in fortran,and there's no function "main" in code peg_diag.So,I think there must be something wrong with linking, but I donot know what should I do to correct the problem~~
What is more, there is no  file named"/usr/lib/gcc/x86_64-linux-gnu/4.6/../../../x86_64-linux-gnu/crt1.o"  in my system!

What's more, I set CPP=gcc F90=gfortran.But the result shows [COLOR="Red"]cc[/COLOR] -lm peg_diag.o -o peg_diag?
Gods help me!

---

### Post by lisati on 2012-06-19
Fortran files *do* have a "main", but it's not declared quite the same way as in C. 

You might want to make sure that a Fortran compiler is installed. For starters, you might want to try this:
```
sudo apt-get install build-essential
```

This should take care of making sure you have most of what you need for compilation.

---

### Post by nigel332 on 2012-06-19
> **lisati said:**
> Fortran files *do* have a "main", but it's not declared quite the same way as in C. 

You might want to make sure that a Fortran compiler is installed. For starters, you might want to try this:
```
sudo apt-get install build-essential
```

This should take care of making sure you have most of what you need for compilation.

Thanks for answering!
I tried the code sudo apt_get install ……
 and the result shows that I have install all the software as needed.

---

### Post by trent.josephsen on 2012-06-19
Your Makefile is not being read. I don't know why; you use some syntax I'm not familiar with, so perhaps make is finding a problem with the file and ignoring the rest of it, or maybe it's named wrong, or maybe you're not invoking it right.

What command line are you using to run make? Are you running make in the same directory as the Makefile? Is the Makefile named 'Makefile'?

---

### Post by nigel332 on 2012-06-19
> **trent.josephsen said:**
> Your Makefile is not being read. I don't know why; you use some syntax I'm not familiar with, so perhaps make is finding a problem with the file and ignoring the rest of it, or maybe it's named wrong, or maybe you're not invoking it right.

What command line are you using to run make? Are you running make in the same directory as the Makefile? Is the Makefile named 'Makefile'?

hi,Thanks for answering,
   I run command make as we always do: % make. And the makefile named Makefile is in the same directory with the code I want to compile.

---

### Post by avgovind on 2013-01-03
Try to compile using "gfortran" instead of "cc" if peg_diag.o is a fortran program.

---

