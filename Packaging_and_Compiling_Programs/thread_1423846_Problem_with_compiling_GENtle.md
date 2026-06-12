---
title: "Problem with compiling GENtle"
date: 2010-03-07
forum: Packaging and Compiling Programs
---

### Post by DzmitryG on 2010-03-07
I was trying to compile GENtle, a cool tool for molecular biology, and while running "make" I get "ureadseq.c:141: error: conflicting types for ‘getline’". It is architecture independent, I believe, as I tried it on PPC and PC (32) and get same error. All the information regarding the source files is **[here]("http://ubuntuforums.org/showthread.php?t=1420747&page=2")**.

There is a compiled version available **[here]("http://gentle.magnusmanske.de/GENtle.tar.gz")**, but it is only for PC (32). I want to install it on PPC at work. Moreover, if this error get fixed with your help, I would really like to have it as a package.

---

### Post by gmargo on 2010-03-07
The "getline" routine in ureadseq.c is local to that file but conflicts with the system function of the same name.  I renamed all instances of "getline" to "getline_gentle" in ureadseq.c and the compile completed.  I was able to run it but I don't know what to do with it.  I compiled the latest from CVS on 32-bit Karmic and 32-bit Hardy (which did not require that edit).

---

### Post by DzmitryG on 2010-03-07
Tried it on 32-bit Karmic Koala - worked as magic! I will try tomorrow on PPC, but I am pretty certain it will work, so big thanks, gmargo! This library provides support for different formats of files (nucleotide or amino acids sequences), I tested this and it seems to be working.

---

### Post by DzmitryG on 2010-03-08
Worked on PPC as well.

---

