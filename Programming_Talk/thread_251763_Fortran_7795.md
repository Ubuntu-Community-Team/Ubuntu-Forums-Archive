---
title: "Fortran 77/95"
date: 2006-09-05
forum: Programming Talk
---

### Post by raublekick on 2006-09-05
I need to do a small Fortran project for school. Really, it only requires a loop or two, an array, some input, some output, and a function, just the basics. I was told that Fortran 95 is backwards compatible with 77, and we're supposed to write it in 77. 

Now, when I searched for Fortran compilers in Synaptic I found g77 and gfortran. I'm not really sure which is set up in the lab at school, but I believe it is g77. However, g77 depends on an older (pre-4.0) version of gcc and some other packages. Will I screw myself if those packages get installed?

In other words: if I install those packages, will gcc still use the newer version, and would the older version only be invoked by gcc-3.95 (or whatever the version number is)?

---

### Post by toojays on 2006-09-06
Yes, if you install the older gcc packages, gcc will still use the newer one by default, and the old one will be available under gcc-3.4.

---

### Post by raublekick on 2006-09-06
thanks you very much!

---

### Post by arixahmad on 2008-09-25
Hello,
I really need help on a simple programming..
I have 3 columsn (X,Y,Z coordinates)sand 1728 rows of datas.
After I read all the datas from a file, I want to sum all the elements in each column, to get 1 value for each column.
How can I do that
Please teach me..
tq

---

### Post by LaRoza on 2008-09-25
> **arixahmad said:**
> Hello,
I really need help on a simple programming..
I have 3 columsn (X,Y,Z coordinates)sand 1728 rows of datas.
After I read all the datas from a file, I want to sum all the elements in each column, to get 1 value for each column.
How can I do that
Please teach me..
tq
This thread is over two year old, about a Fortran compiler.

Please make your own thread to post. [http://ubuntuforums.org/showthread.php?t=726219](http://ubuntuforums.org/showthread.php?t=726219)

---

