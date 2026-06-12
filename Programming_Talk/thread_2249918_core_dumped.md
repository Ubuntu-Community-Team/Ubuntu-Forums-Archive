---
title: "core dumped?"
date: 2014-10-25
forum: Programming Talk
---

### Post by anakin2 on 2014-10-25
Hi all;
as a homework i am supposed to write a a code to get a file containing a array of integer and sort it by merge sort and bubble sort together , this means firstly i should split array of integer to fixed amount of number( representing by BLOKSIZE) and sort them by bubble method and then continue merging by merge sort, but when i run this code i face this error " segmentation fault (core dump) i know what this error means but i can't find my fault in the code, i would be grateful hearing your ideas.
p.s: i should also write merge sort only ( i write it ommiting bubblesort function ,and those first two if in mergesort function, but suprisingly output file contains 0 sorted with another number whereas 0 hadn't been in input file! this is my second problem!)

---

### Post by steeldriver on 2014-10-25
Hello and welcome to the forums

What have you done so far to debug the issue? You should at least be able to isolate at what point your code is failing (either by stepping through your code in a debugger, or simply by putting some print/cout statements throughout the code). That in turn should give you a clue as to which variable's memory you are improperly accessing.

---

### Post by anakin2 on 2014-10-25
thanks for reply, i debugged it by code block but it found nothing, this error came up when i wanted to run it in a terminal!

---

