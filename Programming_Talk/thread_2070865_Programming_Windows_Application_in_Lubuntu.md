---
title: "Programming Windows Application in Lubuntu"
date: 2012-10-13
forum: Programming Talk
---

### Post by Joon Lee on 2012-10-13
I know how to create a program that records the names of the windows a user uses on Windows 7. However, I want to program it on Lubuntu, my current OS, without setting up Dev-C or the likes on a Windows XP virtual machine.
I have Code::blocks installed on Lubuntu - is there a way to compile and export an .exe of the program?
(I'm a decent programmer, yet I know next-to-nothing about libraries, dependencies, and the like, which is why I am asking how to create a windows executable through Code::blocks on Linux)

---

### Post by trent.josephsen on 2012-10-13
The term you want to search for is "cross compiling".

---

### Post by Joon Lee on 2012-10-14
Thanks. Is that an option in the Code::Blocks menu (couldn't find it under compiler and debugger options and everywhre else I looked)?

---

### Post by KdotJ on 2012-10-14
Entering these magic words into Google:

> code::blocks cross compiling

... yields the top result of [this]("http://wiki.codeblocks.org/index.php?title=Code::Blocks_and_Cross_Compilers").

I believe it's what you're after. 

Good luck!

---

### Post by Joon Lee on 2012-10-14
Oh wow, why didn't I just Google it before...
Thank you very much for the help!

---

### Post by ofnuts on 2012-10-14
> **Joon Lee said:**
> Oh wow, why didn't I just Google it before...
Thank you very much for the help!
You'll also have to search for "cross-debugging" because how are you going to debug this on Linux alone?

---

### Post by KdotJ on 2012-10-14
Makes you wonder if it's just easier to set up Windows in a vm

---

### Post by Joon Lee on 2012-10-23
I have XP on a Virtual Machine, except I'm only on a gig of RAM, with only 256 to spare the VM.

---

### Post by dazman19 on 2012-10-24
Yeh VM is the best idea. 

You can cross compile, but depending on how large and how many librarys your app uses, it will probably  be better to at least test it on a windows machine. 

I have had different results on XP/win7 etc for the same app, even using MS frameworks.

---

### Post by Joon Lee on 2012-11-18
After playing around with settings, I got cross-compiling to work!

---

