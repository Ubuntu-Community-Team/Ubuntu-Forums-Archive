---
title: "problem in executing c program:  glibc detected"
date: 2012-05-21
forum: Programming Talk
---

### Post by Ashotti on 2012-05-21
Hi all,

I'm trying to execute a program written in c and I get this message:

*** glibc detected *** ./program-name : free(): invalid next size (normal): 0x08a78dc0 ***

While compiling I don't get any error message and I'm sure the problem doesn't come from the program because it's been already used. So that I think that the problem is in the version of glibc that I use.

Here is what I have installed on my ubuntu 11.10
-gcc version 4.6.1
-libglib2.0

I tryed to type "rpm -q glibc" and it says that it's not installed, but when I type "sudo apt-get install glibc" I get the following answer:  "impossible to fnd the package"

I am not an expert, neither with c language nor with Linux, so I have no idea where the problem could be!

Thanks a lot!!

Ashotti

---

### Post by Bachstelze on 2012-05-21
The problem is almost certainly in your code, not in glibc. The compiler cannot detect all errors. Run your program in Valgrind.

---

### Post by sisco311 on 2012-05-21
Moved to **Programming Talk.**

---

### Post by Ashotti on 2012-05-22
Ok, now I'll try that!

Thank you for your answer!

---

