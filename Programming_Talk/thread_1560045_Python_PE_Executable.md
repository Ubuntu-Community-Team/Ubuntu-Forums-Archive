---
title: "Python: PE Executable"
date: 2010-08-24
forum: Programming Talk
---

### Post by Sailor5 on 2010-08-24
Ahoy Sailors!

So I finished my Python built project for windows a few months ago, Since I've been trying to slim the file size, As this is a slight factor, Currently with everything compressed the size stands at 1.7MB. I've removed all unneeded modules & compressed all the files but now I wondered if there is any further improvement?

I used Py2Exe and it seems there hasn't been a new version out since two thousand & eight. Is this has good as it gets for Python on windows systems? The only other method I could think of is to change some of the functions that I use for smaller ones but that won't save all that much KB.

Anyone shed some light unto this?

See Ya!

---

### Post by nvteighen on 2010-08-24
When dealing with dynamic languages like Python, it's very difficult to have native statically compiled program like you get in C or C++. The easiest way is to create an executable that includes the interpret and bundles the code so what you get is the same dynamic language as an executable that Windows can recognize and execute directly

In Unix-like OSs this is irrelevant because you can use the shebang for most scripting languages, but not all of them. For example with Common Lisp you get the same issue as the one you experience in Windows with Python: you have to create an executable which bundles the code with the interpreter. The same goes for Forth.

I guess that you've done the most you can.

---

### Post by juancarlospaco on 2010-08-24
*But now, with TeraByte HDDs 1,7Mb is so tiny...*

---

### Post by smartbei on 2010-08-26
You could create two versions - one that includes the interpreter, and one that does not, and merely checks that python of a compatible version is installed.

---

