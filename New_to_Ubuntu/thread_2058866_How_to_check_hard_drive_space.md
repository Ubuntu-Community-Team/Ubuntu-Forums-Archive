---
title: "How to check hard drive space"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by geronl on 2012-09-16
I know this is really basic, but I don't know the first thing about using command lines.

How do I find out how much hard drive space is being used and how much is free?

Without checking the Bios

---

### Post by GreatDanton on 2012-09-16
Open up dash, type system monitor and go under File Systems.

Hope this helps. 

Regards.

---

### Post by GreatDanton on 2012-09-16
Another solution is to open up Gparted (you will have to install it manually).

---

### Post by Bashing-om on 2012-09-16
Some command line tools:
```

df -h
free
du -h /home | sort -nf | less

```
substitute the argument "/home" for any other directory of interest.

My little attempt to assist <==BDQ

---

### Post by jrog on 2012-09-16
> **Bashing-om said:**
> Some command line tools:
```

df -h
free
du -h /home | sort -nf | less

```substitute the argument "/home" for any other directory of interest.

My little attempt to assist <==BDQ
'free' has to do with RAM (and swap usage), but it's useful nevertheless!

---

### Post by geronl on 2012-09-18
> **jrog said:**
> 'free' has to do with RAM (and swap usage), but it's useful nevertheless!

Thanks Guys!):P

---

### Post by deadflowr on 2012-09-18
> **jrog said:**
> 'free' has to do with RAM (and swap usage), but it's useful nevertheless!

Free can mean either RAM/(swap) or storage capacity.
Two ways to find either one, is like earlier open system monitor and select the resource tab, to view RAM and swap current usage.
An easy way to look at your free disk space is to open the home folder, go to the menu item view, drop down and select statusbar. Or if on 12.04, click on the alt button and type statusbar and hit enter. At the bottom of the home folder window a panel will appear with the current free space on your mounted partition.

---

### Post by khangtruong on 2012-09-18
I use Disk Usage Analyzer, should I use these other programs instead?

---

### Post by deadflowr on 2012-09-18
> **khangtruong said:**
> I use Disk Usage Analyzer, should I use these other programs instead?

Disk Usage Analyzer is a great tool in finding out where all used space is. Not very good at showing free space.

But knowing which areas are consuming larger than expected space, can help figure out if something is wrong with your system. Like if some program you run keeps running an error, it will probably expand the size of /var/log to an easily noticeable level, from which you can read the massive error log and from there get help with basic understanding of what's going on outright. So Disk Usage Analyzer can be a useful tool in that respect.

---

### Post by pmon on 2012-09-18
A command I use to analyse where space is being used is ```
du -sk * | sort -n
``` which will report, in size order, where the highest usage is in the directory it's run from.

---

### Post by jcka005 on 2012-09-19
> **pmon said:**
> A command I use to analyse where space is being used is ```
du -sk * | sort -n
``` which will report, in size order, where the highest usage is in the directory it's run from.

 ***hello..does this work with ubuntu 11.04?? thankyou..

---

### Post by jcka005 on 2012-09-19
> **pmon said:**
> A command I use to analyse where space is being used is ```
du -sk * | sort -n
``` which will report, in size order, where the highest usage is in the directory it's run from.

 ***hello..does this work with ubuntu 11.04?? thankyou..

---

### Post by reptilez on 2012-09-19
It does work on 12.10. ;)

Edit: If I run this from my home-folder (du -sk * | sort -n) (In terminal), is there a way to make it show hidden folders/files ?

---

### Post by pmon on 2012-09-19
Here's a decent looking list of options in addition to the example I provided.

[http://smartproteam.com/linux-command-du-disk-usage/](http://smartproteam.com/linux-command-du-disk-usage/)

AFAIK, with the options I use that command should work in most Linux distros and Unix too!

---

