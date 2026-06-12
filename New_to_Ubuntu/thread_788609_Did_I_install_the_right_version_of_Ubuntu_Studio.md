---
title: "Did I install the right version of Ubuntu Studio?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by AdrianStrays on 2008-05-09
So I installed Ubuntu Studio and didn't give to much thought which version I was suppose to use, i386 or the other one.  However, after randomly looking at the download page, I noted that the other option was "AMD 64" and that I have a sticker right my laptop that says "AMD 64 Athlon X2" so my questions are this.

How do I know which one I installed?
What will be the effects if I installed the wrong one?
Can I switch to the proper one without having to completely wipe my hard drive?

---

### Post by macaholic on 2008-05-09
You can tell by entering```
uname -m
```into a terminal, and if you get something in there like x86_64, then congrats, you are another brethren of the 64-bit linux clan. If you just have i386, then you are normal 32-bit linux. There are no ill effects of running a 32-bit os on a 64-bit processor, except you aren't using your processor and memory to their fullest potential.

---

### Post by tamoneya on 2008-05-09
to find out which one you have installed type```
uname -m
```If it says x84_64 you have the AMD 64 version i386 means the other one.  There are no big negative side affects if you have i386 (32 bit version installed) Here is a short explanation of the differences.  [http://ubuntu-tutorials.com/2007/11/26/32bit-vs-64bit-ubuntu-that-is-the-question/](http://ubuntu-tutorials.com/2007/11/26/32bit-vs-64bit-ubuntu-that-is-the-question/).  

As for switching I believe it is possible but I think in most cases it is easiest to reinstall.  It would require recompiling your kernel and then switching all of you packages which wouldnt be fun.

---

### Post by macaholic on 2008-05-09
> **tamoneya said:**
> 
As for switching I believe it is possible but I think in most cases it is easiest to reinstall.  It would require recompiling your kernel and then switching all of you packages which wouldnt be fun.
Lol we posted almost the same thing at the same time. Anyway you are right, I would not suggest trying to switch AT ALL, unless you know exactly what you are doing, even then I don't understand what the point of switching is. If there is any vital info you need, 64-bit and 32-bit use the same files and can use the same home directory.

---

### Post by tamoneya on 2008-05-09
> **macaholic said:**
> Lol we posted almost the same thing at the same time. Anyway you are right, I would not suggest trying to switch AT ALL, unless you know exactly what you are doing, even then I don't understand what the point of switching is. If there is any vital info you need, 64-bit and 32-bit use the same files and can use the same home directory.

Yeah I think we did a good job covering all the important facts.

I am pretty familiar with ubuntu and I still wouldnt do it myself.  Installing is MUCH easier than changing the architecture.  You are really just asking for trouble if you try it.

---

