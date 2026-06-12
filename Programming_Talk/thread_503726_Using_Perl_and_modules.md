---
title: "Using Perl and modules"
date: 2007-07-18
forum: Programming Talk
---

### Post by Marc Hoffman on 2007-07-18
I am trying to complete a perl assignment that involves writing modules.

How and where do I save my .pm files in order for the program to find them and work?

Thanks in advance.

---

### Post by nitro_n2o on 2007-07-18
if you use h2xs it will create everything you need including a Makefile.PL, which you should perl Makefile.PL 
then make then sudo make install 

hope this helps

---

### Post by Marc Hoffman on 2007-07-18
Thanks for that.

Actually was just being daft and had cocked up the coding.

Program worked by leaving everything in the home folder- but i was working to some notes on how to use perl in windows.

---

