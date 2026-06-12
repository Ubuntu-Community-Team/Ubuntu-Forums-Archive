---
title: "Best .ISO burning program"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by firefox834 on 2011-10-19
I have tried Brasero,K3B, and numerous other software with no success....I need to boot in windows7 to do my media stuff, its trouble free, why is ubuntu so temperamental with stuff like burning and playing games ????????

---

### Post by TeoBigusGeekus on 2011-10-19
To burn an iso dvd:
```
growisofs -dvd-compat -Z /dev/dvd=/path/imagename.iso
```
Replace /dev/dvd with whatever appropriate (/dev/dvdrw, /dev/sr0, etc.)
To burn an iso cd:
```
wodim -v dev=/dev/cd /path/imagename.iso
```
Again replace /dev/cd with whatever appropriate (/dev/cdrw, /dev/sr0, etc.)

---

### Post by haqking on 2011-10-19
> **firefox834 said:**
> I have tried Brasero,K3B, and numerous other software with no success....I need to boot in windows7 to do my media stuff, its trouble free, why is ubuntu so temperamental with stuff like burning and playing games ????????

It would help if you mention why or how it is not working.

As for temperamental because you are having issues does not mean  it is temperamental merely you are having issues for whatever reason, if you post the reasons then maybe we can help.

K3B works great for me and always has, brasero not so much but lots of other people get on well with it.

At least they are all free, in windows you need to pay alot of the time for software and if it was temperamental then you might of wasted your money ;-)

as for Games, if they are linux games then post the issues probably best in the gaming and leisure forum, if they are not Linux games and you are trying to get them to run under Linux using Wine etc then that is an obvious answer in that the game wasnt written for Linux.

---

### Post by Dry Lips on 2011-10-19
I'm not quite sure what the problem is? Do you need help with finding a 
good ISO-burning program, or help with setting up a dual boot system?

When it comes to burning programs, I personally prefer "*GnomeBaker CD/DVD Writer*".
(It can be downloaded from the Ubuntu Software Centre).

---

### Post by haqking on 2011-10-19
> **Dry Lips said:**
> I'm not quite sure what the problem is? Do you need help with finding a 
good ISO-burning program, or help with setting up a dual boot system?

When it comes to burning programs, I personally prefer "*GnomeBaker CD/DVD Writer*".
(It can be downloaded from the Ubuntu Software Centre).

I think the OP meant by the "have to boot into windows" meaning he has to do that to burn his CD/DVD etc because it is not working for him in Windows.

---

### Post by firefox834 on 2011-11-25
Problem is solved now i have returned to windows 7 and got rid of Ubuntu, now I can burn,convert and play games with ease

---

### Post by haqking on 2011-11-26
> **firefox834 said:**
> Problem is solved now i have returned to windows 7 and got rid of Ubuntu, now I can burn,convert and play games with ease

Use what works for ya or that you can make work ;-)

Peace

---

