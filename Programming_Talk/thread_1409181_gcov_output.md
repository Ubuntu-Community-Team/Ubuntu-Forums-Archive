---
title: "gcov output"
date: 2010-02-17
forum: Programming Talk
---

### Post by newport_j on 2010-02-17
I have been looking to find out more about gcov including interpreting its output. I have found very little on the internet that tells me what this output is about. When I run gcov

 gcov -a int_bnd2.c
File 'int_bnd2.c'
Lines executed:93.75% of 64
int_bnd2.c:creating 'int_bnd2.c.gcov'

The line that I do not understand is "Lines executed:93.75% of 64". My guess is it is telling the programmer that 93.75% of the module's execution (by time I believe) occurs in only 64 lines of that file. That seems correct from my using nemiver to walk through the code in : int_bnd2.c. 

That is seems correct by just my examination of the operation of the module: int_bnd2.c. However some things are left out such as exactly what 64 lines is it talking about. I think that I know, but it would be reassuring to see gcov id those lines.

I also would like more gcov info and am unsure how to get it. I know to run gcov with  f, a, and b options. It just seems that gcov can tell me more on it output. I also know to look in the int_bnd2.c.gcov file, but again, I am looking for profiling int_bnd2.c as far as execution time.

Any help appreciated.

Newport)j

I know the is a gcc manual that goes into great detail about gcov among other things. I do not have it, is it online at some website? Also, will lcov tell me what I want as I outlined above?

---

### Post by avidday on 2010-02-17
gcov is for generating coverage statistics. If you are interesting in profiling and timing, use gprof.

---

### Post by newport_j on 2010-02-17
What you say is true, but please understand that gprof by its own admission is statistically inaccurate occasionally. To occasionally in my opinion.  I am looking at specific modules, not the whole program.

Gprof looks at the whole program and gives you rough estimates of the time in each module. I am now looking at one module and trying to learn as much as I can about that one module. 

Gcov seems best for that it can tell you how many time a certain executable line was executed. It also can tell you branch use probabilities that can be very helpful. 

I used gprof to identify the slow modules, now I am looking at a specific module very closely. 

Again what does "93.75% of 64" mean? I assume that statement only pertains to my module that I am examining. This is the output statement I get when I gcov'd the said c module.

Newport_j

---

### Post by avidday on 2010-02-17
That is the percentage of actual code lines that were executed. So 93.75% of the actual compiled code lines were execute, the other 6.25% were not. It does not say anything about timing or frequency, only coverage.

---

### Post by newport_j on 2010-02-17
Okay, and the 64 was the total number of executable lines in that module?

newport_j

---

### Post by avidday on 2010-02-17
Yes. gcov should produce an annotated output showing which lines it counted as executable and whether they were covered or not.

---

