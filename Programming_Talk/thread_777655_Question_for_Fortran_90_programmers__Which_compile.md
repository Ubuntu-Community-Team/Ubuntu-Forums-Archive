---
title: "Question for Fortran 90 programmers:  Which compiler is best?"
date: 2008-05-01
forum: Programming Talk
---

### Post by laptoplinux on 2008-05-01
I used to run gfortran, but I'm pretty much finished with that compiler.  This is due to a numerical computation that I had to perform recently.  Despite triple-checking the code and the math, the output was garbage when I compiled it using gfortran.  Then, on a whim, I compiled the same code using f90, and everything magically worked as it should.

Since I can't trust gfortran anymore, what do you guys recommend as a Fortran 90/95 compiler?  I know about the Intel ifort compiler, and I use it too, but I'm wondering if there are any other good (and free!) options in case I ever decide to do development work on a Mac.  

Any recommendations, along with links to installation instructions, would be appreciated!

---

### Post by Kadrus on 2008-05-01
G77 (g77)
GFortran (gfortran)
Install them using sudo apt-get install g77..etc..or from the package manager..good luck :)

---

### Post by LaRoza on 2008-05-01
> **Kadrus said:**
> G77 (g77)
GFortran (gfortran)
Install them using sudo apt-get install g77..etc..or from the package manager..good luck :)

g77 is only for Fortran 77 I believe and the OP stated she wanted an alternative to gfortran.

@OP Are you sure the code was valid? Most of the time, bad output means a problem with the code, not the compiler.

---

### Post by Kadrus on 2008-05-01
> **LaRoza said:**
> g77 is only for Fortran 77 I believe and the OP stated she wanted an alternative to gfortran.

@OP Are you sure the code was valid? Most of the time, bad output means a problem with the code, not the compiler.
sorry just read the title :p..really tired..

---

### Post by LaRoza on 2008-05-01
> **Kadrus said:**
> sorry just read the title :p..really tired..

It happens.

---

### Post by jdrodrig on 2008-05-01
I use SunStudio 12 that is free (I am almost positive it is not opensource) for Linux.

I will have to check about Mac compatibility.

Something to have in mind is that Intel compilers would usually have an advantage on Intel Platforms, specially if you want to execute the code on Core2Duo or Xeon platforms.

For AMD, at least for Opteron, my experience is that Sun's compiler is faster.

Typically compilers would have a -xtarget or -target flag, where you can indicate that you want your executable to run in specific platforms.

Also relevant is if you want an IDE, SunStudio provides an IDE.

---

### Post by rusi_pathan on 2008-06-29
IMHO the best free compilers are

1. Intel Fortran (free for non-commercial use only)
2. Sun Fortran
3. g95
4. gfortran

Of these the Intel and Sun compilers are really industrial strength. g95 is quite good too but doesnt support features of the 2003 Fortran standard.

gfortran is the new kid and hopefully will get better with age. It still should be good for most applications.

---

### Post by xtacocorex on 2008-06-29
As for OS X Fortran compilers, you're sort of stuck with with stuff that works with XCode (which I have yet to get working and I've messed with it for over a year).  I don't remember where I got it, but there are 

The Intel Compiler is awesome on Linux, but you have to pay for it on OS X as there is no non-commercial version. :(

I had linking issues with GFortran on OS X and because of the trouble with trying to get everything working, I moved development to codes over to C++.

---

### Post by samsmartguy on 2008-06-30
I prefer to write programs with VB.NET. In my opinion this language is simple and powerful.

---

### Post by Bichromat on 2008-06-30
> **laptoplinux said:**
> I used to run gfortran, but I'm pretty much finished with that compiler.  This is due to a numerical computation that I had to perform recently.  Despite triple-checking the code and the math, the output was garbage when I compiled it using gfortran.  Then, on a whim, I compiled the same code using f90, and everything magically worked as it should.

I know triple-checked the code, but are you sure this is not due to a bug? This kind of thing can happen with undeclared variables. I had a code which worked perfectly with some compilers, and produced nonsensical values with another. The reason was that I had initialized variables named a11, a12, a13 etc. but I used b1, b2, b3 instead in the algorithm. I had forgotten "implicit none" so my code did not produce an error but on some compilers implicit variables were automatically set to zero while with other compilers they were set to some random value depending on the content of the memory...
Another source of problems with gfortran is the following:
```

print *, somefunction()

```
If somefunction() itself prints something, your code will crash or produce garbage. The Intel compiler tells you it's forbidden, but gfortran does not (did not?).

---

### Post by Timtro on 2008-06-30
I used to use a lot of FORTRAN for scientific computing... I still do, but I tend to write more in C now.

Anyhow, ifort and pathscale are my pics. It depends on the CPU too though. Unfortunately, I don't know but doubt there is a free pathscale license.

Cheers,


Tim.

---

### Post by rusi_pathan on 2008-06-30
> I used to use a lot of FORTRAN for scientific computing... I still do, but I tend to write more in C now.

FORTRAN (77) in my opinion is ugly, outright messy and a PITA.

Fortran (90/95/2003) on the other hand is simpler, elegant and more powerful.

Personally I find Fortran much easier to use than MATLAB and Python (for numerical computing only). Usually people who hate Fortran either have never used it or used only FORTRAN 77.

---

