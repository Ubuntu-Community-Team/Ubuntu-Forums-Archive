---
title: "[SOLVED] how can i find out what i am running?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by misswham on 2008-11-06
32 bit or 64 bit?  I am a novice to this.  I havent a clue what either means.

---

### Post by Idefix82 on 2008-11-06
If you type in the terminal
```
uname -a
```
and paste the output here, we will be able to tell you.

The difference is in the address range that the system can access. 32bit systems can natively only use about 3.2 GB RAM while the restriction for 64 bit sytems is so high that it's pretty much negligeable.

---

### Post by misswham on 2008-11-06
Linux ree-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

---

### Post by Idefix82 on 2008-11-06
You are running the 32 bit version of Ubuntu. The "i686" bit says that because i686 is a certain 32 bit processor architecture. If you want to install the 64 bit system you need to check whether your processor is 64 or 32 bit. You can go to the System Monitor and see what processor you have in your computer. Then you can google for it or post its name here.
A 64 bit system is well worth it in terms of speed if you have at least 3.5 - 4 GB RAM. If you have less than 3 then it's probably not really worth it. With anything inbetween it is your decision but you will probably not see a great difference.

---

### Post by jenkinbr on 2008-11-06
> **Idefix82 said:**
> If you type in the terminal
```
uname -a
```
and paste the output here, we will be able to tell you.


I've been wondering how to do this as well so I can tell users how to determine their system architecture when duplicating an online repository for use offline.  My current method was to:
```
grep "Architecture: " /var/lib/dpkg/status 
```
It generates a lot of output and looked ugly, but it works.
> **Idefix82 said:**
> The difference is in the address range that the system can access. 32bit systems can natively only use about 3.2 GB RAM while the restriction for 64 bit sytems is so high that it's pretty much negligeable.

I did some rough calculations on this a while back, and the amount of RAM 64bit can support was absurdly high.

---

