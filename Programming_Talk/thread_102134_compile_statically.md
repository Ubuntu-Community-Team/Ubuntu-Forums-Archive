---
title: "compile statically"
date: 2005-12-11
forum: Programming Talk
---

### Post by meissner on 2005-12-11
Hello.

I program some Qt4 Stuff and want start the programs on Linux systems where is no Qt4 available. Is there a possibility to compile my programs statically?

---

### Post by meissner on 2005-12-11
I've found a solution. Compile Qt with ./configure -static and than add in the .pro File: CONFIG += static

But the binary is then at least 5MB.

---

### Post by mostwanted on 2005-12-11
Hm... could you make some precompilation stuff to sort it out and then distribute the program by source?

---

### Post by meissner on 2005-12-12
Does that make Sense?

I mean, I offer the source for those who had Qt4 installed and a static binary who don't want install Qt4. So everyone can decide. But I'm not sure if that is allowed to publish closed source by the license of the open source version of Qt4.

I found out that with stripe und upx I can reduce the size of the static binary to 1,8MB, thats only double of the non-static version. However I must test if it works correctly.

Maybe you are right, but I don't see advantages...

---

### Post by LordHunter317 on 2005-12-12
Don't statically compile QT4, lots of features won't work.

Statically compiling most things on Linux tends to lead to trouble.  Better is to ship a precompiled version of the library with your code.

---

