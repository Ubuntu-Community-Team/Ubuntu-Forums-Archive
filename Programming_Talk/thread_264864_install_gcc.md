---
title: "install gcc"
date: 2006-09-25
forum: Programming Talk
---

### Post by nighthawk06 on 2006-09-25
Hi,.

I am a beginner in ubuntu and linux.
How do I install the gcc,. what libraries do I need in order to it to work?
I got the gcc-3.3-base and the gcc-4.0-base is that enough?

---

### Post by 23meg on 2006-09-25
```
sudo apt-get install build-essential
```

---

### Post by nighthawk06 on 2006-09-25
Hi,

I did that the 
sudo apt-get install build-essential

Yet it installed a whole bunch of apps that updated my kernel as well to 2.6.15-27-386 
To make a long story short, I didn't succeed with rebooting the system afterwards.
Nevertheless, it kept my old kernel as well, so I could boot from it.

If you want you can check the previous post I did about that subject:
[http://www.ubuntuforums.org/showthread.php?t=264759](http://www.ubuntuforums.org/showthread.php?t=264759)

now the problem is that I do not know whether the new installment of the build-essential elements ran over the old gcc that was installed on the old kernel.

---

### Post by amo-ej1 on 2006-09-26
it looks like your system merely updated itself ? (and there was e new kernel release in the 6.06 recently).

Open a console, enter gcc press enter and see if it gets found ;-) if you didn't abort your last upgrade (which i assumed you didn't) that should work ...

if it doesn't work, try to struggle with apt and retry to apt-get update and apt-get install build-essentials

---

