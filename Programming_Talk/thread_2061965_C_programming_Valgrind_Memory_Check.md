---
title: "C programming: Valgrind Memory Check"
date: 2012-09-23
forum: Programming Talk
---

### Post by hailholyghost on 2012-09-23
Hello,

I've been writing a scoring program for a molecular dynamics simulation.  It has checked out fine with all compiler warnings enabled in the c99 standard, and gdb can't find any problems with it.

However, I realized that it was not giving the warnings for uninitilized values that I was used to in Perl.  I found some bugs that I thought I had corrected.  I've put many printfs and confirmed that the data is being read in as I intend it to.

A small segment of this 1544 line program, which prints out many errors:

```
 const double RAD = 3.14159/180;
 FILE *faz;
 faz = fopen("dmpshifts.ans","r"); //open file dmpshifts.ans for reading
 double p2[29799], p3[29799], p4[29799]; //create 3 error arrays
 if (faz != NULL) { //only go through this if the file exists
    double A[5183], Z[5183], GIAO[5183]; //arrays for 1st,2nd, and 3rd columns
    unsigned int C = 0; //index for A, Z, and GIAO arrays
    double PERR = 1.0; //error to be used later
    while (!feof(faz)) {
       if (fscanf(faz,"%lf %lf %lf\n",&A[C],&Z[C],&GIAO[C]) != 3) {
          continue;
       }
       C++; //increase index for next step
    }
    fclose(faz); //close file handle
    /*------------------*/
    FILE *fz1, *fa2;
    fz1 = fopen("zeta1.99X","r");
    fa2 = fopen("alpha2.99X","r");
    if ((fz1 != NULL) && (fa2 != NULL)) {
       double z[30000], a[30000];
       char x; //disposable variable
       unsigned int c = 0;
       while (!feof(fz1)) {
          if (fscanf(fz1,"%s %lf",&x,&z[c]) != 2) { //first column not stored
             continue;
          }
          if (z[c] < 0) {
             z[c] += 360;
          }
          c++;
       }
       fclose(fz1);
       c = 0;
       while (!feof(fa2)) {
          if (fscanf(fa2,"%s %lf",&x,&a[c]) != 2) {
             continue;
          }
          if (a[c] < 0) {
             a[c] += 360;
          }
          c++;
       }
       fclose(fa2);
       unsigned int j;
       for (j = 200; j <= 30000; j++) {
          double xsumz = 0.0, ysumz = 0.0, xsuma = 0.0, ysuma = 0.0;
          unsigned int k = j-200, m;
          for (m = k; m <= j; m++) {
             xsumz += cos(z[m]*RAD);
             ysumz += sin(z[m]*RAD);
             xsuma += cos(a[m]*RAD);
             ysuma += sin(a[m]*RAD);
          }
          double sumz = (180/3.14159)*(atan2(ysumz,xsumz));
          double suma = (180/3.14159)*(atan2(ysuma,xsuma));
          if (sumz < 0) {
             sumz += 360;
          }
          if (suma < 0) {
             suma += 360;
          }
          if (sumz > 358.72) {
             sumz = 0;
          }
          if (suma > 358.72) {
             suma = 0;
          }
          unsigned int n, q = 0;
          for (n = 0; n <= 5183; n++) {
             if (
                 (fabs(sumz-Z[n]) <= 2.5) && (fabs(suma-A[n]) <= 2.5) && (fabs(GIAO[n]+1.15) < 1)
                ) {
                 score[k]++;
                 q++;
                 break;
             }
          }
          if (q == 1) {
             p2[k] = 0;
          } else {
             p2[k] = 1;
          }
       }
    } else {
      printf("Could not open Z1/A2\n");
    }
  }
```

```
==7322== 1 errors in context 1 of 125:
==7322== Invalid write of size 4
==7322==    at 0x400CF9: main (score.c:67)
==7322==  Address 0x7fefffe00 is on thread 1's stack
==7322== 
==7322== 
==7322== 1 errors in context 2 of 125:
==7322== Invalid read of size 8
==7322==    at 0x400CEA: main (score.c:65)
==7322==  Address 0x7fefffc70 is on thread 1's stack
==7322== 
==7322== 
==7322== 1 errors in context 3 of 125:
==7322== Invalid write of size 4
==7322==    at 0x400C37: main (score.c:55)
==7322==  Address 0x7fefffdfc is on thread 1's stack
==7322== 
==7322== 
==7322== 1 errors in context 4 of 125:
==7322== Invalid read of size 8
==7322==    at 0x400C28: main (score.c:54)
==7322==  Address 0x7fefffc68 is on thread 1's stack
==7322== 
==7322== 
==7322== 1 errors in context 5 of 125:
==7322== Invalid write of size 4
==7322==    at 0x400B75: main (score.c:44)
==7322==  Address 0x7fefffdfc is on thread 1's stack
```

The program says this for almost every single variable in the program.

I thought that it might be trying to put a floating point into a char might throw it off, but I changed that to a floating point and it didn't change the problem.

My programming paradigm is to keep my variables as local as possible to prevent these kinds of problems and keep the memory usage as low as possible.

I have made printf tests at the offending lines which show that the program is in fact, doing what I want it to.

Do these errors matter?  How can I fix them?

I realize this is a really long post.  Please let me know if I was in any way unclear and I appreciate you taking time to read this!):P

-DC

---

### Post by Bachstelze on 2012-09-23
And how are we supposed to know which actual line a line number of the valgrind log refers to? ;) Post your program on a pastebin if it's too long to post here, or gzip and attach it.

---

### Post by hailholyghost on 2012-09-23
> **Bachstelze said:**
> And how are we supposed to know which actual line a line number of the valgrind log refers to? ;) Post your program on a pastebin if it's too long to post here, or gzip and attach it.

Hello Bachstelze, thanks so much!

Unfortunately the file size limits are only a small fraction of the compressed tar files (this program opens and closes 40 files just for reading).  I can't attach the files that it's designed to work with (976.6 KB is pretty small).

The compressed files that this program reads are 3.9 MB and 2.1 MB.  Is there any way I could get around the size limitation?

---

### Post by Bachstelze on 2012-09-23
Was the log really done with this .c file? The line numbers don't seem to match.

---

### Post by hailholyghost on 2012-09-24
> **Bachstelze said:**
> Was the log really done with this .c file? The line numbers don't seem to match.

Sorry about that!  The error file is very long, so I have to hit control-C before it finishes.

---

### Post by spjackson on 2012-09-24
As Bachstelze says, the line numbers reported in the valgrind log do not seem to match the line numbers in the source, so it is difficult to determine what is going on.

However, I would point out that you are not checking in your code that you have enough room in your stack arrays for the amount of input you have. i.e. if file fz1 has too many values, you will write outside the bounds of the array when you fscanf (line 46).

You have the same buffer overflow potential with other arrays that you are using.

---

### Post by vexorian on 2012-09-24
Since variable declarations usually push to the stack, then it is possible that an issue with stack overflow could cause this sort of issue in simple variable declariation.

Edit: I see the valgrind log and I am unsure if it is the start of the log or the end or the middle. When looking at these logs it is best to start at the very first error you can read, as the first error that happens tend to cause the remaining ones.

---

### Post by Bachstelze on 2012-09-24
Your problem probably has a lot to do with the fact that you are storing WAY too much data on the stack.

```
 double p2[29799], p3[29799], p4[29799];

    double A[5183], Z[5183], GIAO[5183];

       double z[29999], a[29999];
```

This belongs on the heap, really.

*EDIT:* Also do not run with -v unless you have a good reason to. Here it is not necessary, and it pollutes the log with irrelevant information.

---

### Post by hailholyghost on 2012-09-24
> **Bachstelze said:**
> Your problem probably has a lot to do with the fact that you are storing WAY too much data on the stack.

```
 double p2[29799], p3[29799], p4[29799];

    double A[5183], Z[5183], GIAO[5183];

       double z[29999], a[29999];
```

This belongs on the heap, really.

*EDIT:* Also do not run with -v unless you have a good reason to. Here it is not necessary, and it pollutes the log with irrelevant information.

Thanks much Bachstelze, spjackson, and vexorian, I've learned a lot today!  

The solution is to set Valgrind's maximum stackframe to it's suggested value in the logfile [which should be written, this is one reason I had this problem] and track the origins of uninitialized variables.  As Bachstelze said, there was a LOT of irrelevant info in there and I didn't see the key piece of information.

C seems to be stricter with what is "uninitialized" than perl.  It will give you an error if you say "double a; a++; printf("%lf\n",a);" where a should implicitly be 0 when set.
```

    con@Inspiron-1545:~/Chemistry/lna.caau.99X/x$ time valgrind --tool=memcheck --log-file=score.log --max-stackframe=9051448 --track-origins=yes ./score
    The minimum is 18/36 = 50.0%
    The Mean is 25.31/36 or 70.3% with a standard deviation of 2.62 or  7.3%
    The Maximum is 29/36 = 80.6%

    real    7m57.079s
    user    7m52.922s
    sys    0m0.940s
```

and the empty error file:
```

    ==3219== Memcheck, a memory error detector
    ==3219== Copyright (C) 2002-2011, and GNU GPL'd, by Julian Seward et al.
    ==3219== Using Valgrind-3.7.0 and LibVEX; rerun with -h for copyright info
    ==3219== Command: ./score
    ==3219== Parent PID: 2171
    ==3219==
    ==3219==
    ==3219== HEAP SUMMARY:
    ==3219==     in use at exit: 0 bytes in 0 blocks
    ==3219==   total heap usage: 1,175,226 allocs, 1,175,226 frees, 300,870,960 bytes allocated
    ==3219==
    ==3219== All heap blocks were freed -- no leaks are possible
    ==3219==
    ==3219== For counts of detected and suppressed errors, rerun with: -v
```

Thanks so much for your help today!

---

### Post by Bachstelze on 2012-09-25
> **hailholyghost said:**
> 
C seems to be stricter with what is "uninitialized" than perl.  It will give you an error if you say "double a; a++; printf("%lf\n",a);" where a should implicitly be 0 when set.


No, no, no. C will not give you an error, Valgrind will. Also, in C it is a mistake to think things "should" be initialised "implicitly". Things are not initialised implicitly, period. With a code like the one you describe, you don't end up with an error but with a behavior that could very well not be what you expect, which is the definition of a bug. (And this is exactly the kind of bugs Valgrind was designed to catch.)

---

