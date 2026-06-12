---
title: "Help needed on compiling my C code using gcc"
date: 2013-03-09
forum: Packaging and Compiling Programs
---

### Post by recklesshao on 2013-03-09
this is for school assignment. I made my code and it runs fine on my school sever. However, everytime I sue my local gcc to compile it give this error message

gcc -c -m32 a3.c
In file included from /usr/include/stdio.h:28:0,
                 from a3.c:1:
/usr/include/features.h:324:26: fatal error: bits/predefs.h: No such file or directory
compilation terminated.
make: *** [a3.o] Error 1

I tried to reinstall my gcc library a couple of time it does help at all. and the I am not using some custome library at all. can some one help to fix it?

---

### Post by Mr. Shannon on 2013-03-09
Since you are using the -m32 (32 bit) flag I assume you have 64 bit Ubuntu and are trying to compile a 32 bit binary.  Doing a search for :compile 32 bit binary on 64 bit ubuntu" gives [http://en.kioskea.net/faq/1137-compiling-testing-in-32-bit-on-ubuntu-x86-64](http://en.kioskea.net/faq/1137-compiling-testing-in-32-bit-on-ubuntu-x86-64) as the first result which says to do:
```
sudo apt-get install gcc-multilib libc6-i386 libc6-dev-i386
```

Is there any particular reason why you are using the 32 bit flag?

---

### Post by recklesshao on 2013-03-09
yes, because my prof asks for 32bit... i want to test my code and my make file on my local machine... so ikept the -m32 flag

---

### Post by Mr. Shannon on 2013-03-09
So did that solve the problem?

> **recklesshao said:**
> yes, because my prof asks for 32bit... i want to test my code and my make file on my local machine... so ikept the -m32 flag
That's odd, I have never had a programming homework be due in a binary form.  FYI, as far as I know (fellow student talking), except for the size of some data types (and thus some bit level operations like masking and shifting), the result of 64 bit and 32 bit compilation will give the same program behavior.  The assembly and thus Opcode generated will be drastically different however.  It was a good idea to test in 32 bit mode though.

---

### Post by recklesshao on 2013-03-09
yes, it works, but there is a mistake in the line. the correct one should be

   sudo apt-get install gcc-multilib libc6-i386 libc6-dev-i386

---

### Post by peng6662001 on 2013-03-11
I study it.

---

