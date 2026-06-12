---
title: "Linux Programming"
date: 2009-09-26
forum: Programming Talk
---

### Post by swappo1 on 2009-09-26
I have a spare hard drive.  If I swap hard drives with the spare and I work on learning linux programming, am I in danger of doing any damage to my system?  Obviously my main drive won't be hooked up therfore it will be safe, but are my devices at risk?  I have enough trouble with my video card and getting it to work right as it is that I don't want to cause any problems.

---

### Post by Ferrat on 2009-09-26
There is no risk :)

---

### Post by otetiani on 2009-09-26
I'm not a fan of frequently removing hardware and replacing it.  It is always possible that by removing your main HD repeatedly you accidentally damage it by dropping it or static discharge.

As far as learning Linux I would suggest making a small partition and dual booting.  This gives you a full version and as long as you don't touch the other partition(s) you won't affect windows/OS X.

Another alternative is to use a thumbdrive version.  I have not done this yet, maybe someone can elaborate...

I can however say that using an online Ubuntu guide or a book like "A Practical Guide to Ubuntu Linux" by Mark Sobell (my favorite for a hardcopy learning tool) will help guide you toward learning much more than shooting in the dark like I did for the first 2 years.

When you start to learn NEVER use anything but the command line!  The newer versions of Ubuntu are so easy to use by "clicking" that you can accomplish a great deal now without touching the terminal - don't get lured by laziness, learn first, then click!

Good luck

---

### Post by Nevon on 2009-09-27
> **otetiani said:**
> When you start to learn NEVER use anything but the command line!  The newer versions of Ubuntu are so easy to use by "clicking" that you can accomplish a great deal now without touching the terminal - don't get lured by laziness, learn first, then click!

Good luck
Or do the complete opposite, and first learn by clicking, then learn the command line way when you want to accomplish tasks faster, and potentially with more customization.

---

### Post by Zugzwang on 2009-09-27
> **otetiani said:**
> When you start to learn NEVER use anything but the command line!  The newer versions of Ubuntu are so easy to use by "clicking" that you can accomplish a great deal now without touching the terminal - don't get lured by laziness, learn first, then click!


> **Nevon said:**
> Or do the complete opposite, and first learn by clicking, then learn the command line way when you want to accomplish tasks faster, and potentially with more customization.

@OP: Look at [this post]("http://ubuntuforums.org/showthread.php?t=1258665") to see why you will always see discussions/advices like this all over this forum. The post also contains some not-outdated information to get you started.

---

### Post by Cybergod on 2009-09-28
> **swappo1 said:**
> I have a spare hard drive.  If I swap hard drives with the spare and I work on learning linux programming, am I in danger of doing any damage to my system?  Obviously my main drive won't be hooked up therfore it will be safe, but are my devices at risk?  I have enough trouble with my video card and getting it to work right as it is that I don't want to cause any problems.

Just install Linux on a virtual machine.

---

### Post by The Cog on 2009-09-28
> **Cybergod said:**
> Just install Linux on a virtual machine.
+1
Provided you have the spare space on your main disk, this is indeed the easiest, most convenient and safest way.

---

### Post by nvteighen on 2009-09-28
Actually, unless you start fiddling with unistd.h, and the sys/ defined functions, you can do little harm to your system if you run your program as a regular user (i.e. never as root), and in a safe "environment" (in a specific directory where you place test files and such...).

The worst you can do at a beginner stage is to blank a file when trying to open it for writing. But for that you need write permissions and to specify the path.

I wouldn't worry that much, really: your programming activity shouldn't damage your system if you know what you do.

---

### Post by Cybergod on 2009-09-28
> **The Cog said:**
> +1
Provided you have the spare space on your main disk, this is indeed the easiest, most convenient and safest way.

I'm assuming he has the space because he has a second drive.

---

### Post by The Cog on 2009-09-28
> **Cybergod said:**
> I'm assuming he has the space because he has a second drive.

Doh!

---

