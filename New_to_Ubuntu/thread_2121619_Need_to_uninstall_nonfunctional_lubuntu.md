---
title: "Need to uninstall nonfunctional lubuntu"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by MandelaPhilo on 2013-03-02
So, I installed lubuntu on an old PC (HP 8500, Piii, 450Mhz/256MB Ram) and it doesn't seem to work (I explored the issue here: [http://ubuntuforums.org/showthread.php?t=2121420&p=12536942#post12536942](http://ubuntuforums.org/showthread.php?t=2121420&p=12536942#post12536942)) so it's been suggested that I switch to Puppy Linux because the computer might not be able to support lubuntu (particularly PAE).  Before I install it, however, I would like to uninstall lubuntu.  Since it's nonfunctional, I can't get into it to uninstall from the inside.  How would I go about uninstalling it from the boot menu or through Windows 2000 (it's dual booted).

Thanks for your help and support.

-Eric

---

### Post by cortman on 2013-03-02
You don't need to uninstall Lubuntu, when you install Puppy select the Lubuntu partitions and it'll format them and install over it.

---

### Post by sudodus on 2013-03-02
> **MandelaPhilo said:**
> So, I installed lubuntu on an old PC (HP 8500, Piii, 450Mhz/256MB Ram) and it doesn't seem to work (I explored the issue here: [http://ubuntuforums.org/showthread.php?t=2121420&p=12536942#post12536942](http://ubuntuforums.org/showthread.php?t=2121420&p=12536942#post12536942)) so it's been suggested that I switch to Puppy Linux because the computer might not be able to support lubuntu (particularly PAE).  Before I install it, however, I would like to uninstall lubuntu.  Since it's nonfunctional, I can't get into it to uninstall from the inside.  How would I go about uninstalling it from the boot menu or through Windows 2000 (it's dual booted).

Thanks for your help and support.

-Eric
I suggest that you start by downloading iso files for some linux distros, that you want to try, and Puppy linux is one of them. You can wipe the internal drive when booted from the installation media (in a live session of Puppy).

I use Lubuntu 12.04 on an IBM Thinkpad T42 and it works well. To install it with so little RAM as you have, download the alternate iso file. You can reuse the same partition during the installation process, so no need to other software to wipe it.

[http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-alternate-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-alternate-i386.iso)

And you will probably get several other tips what to install from other guys at the Ubuntu Forums.

Good luck :-)

---

### Post by mörgæs on 2013-03-03
Have added a comment in the other thread regarding the PAE misunderstanding.

---

### Post by sudodus on 2013-03-03
You might want some other alternatives to Puppy and Lubuntu

[http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552](http://www.techradar.com/news/software/operating-systems/8-of-the-best-tiny-linux-distros-683552)

[http://en.wikipedia.org/wiki/Lightweight_Linux_distribution](http://en.wikipedia.org/wiki/Lightweight_Linux_distribution)

[http://www.osnews.com/story/26087/Four_Lightweight_Distros_Compared](http://www.osnews.com/story/26087/Four_Lightweight_Distros_Compared)

But I repeat that Puppy is recommended particularly for old hardware:
> Puppy Linux 5 includes a "retro release" called Wary, specifically designed for older hardware with an older kernel. Wary runs on topped out P-II's or better. It is a good choice for aging hardware because it has a large active community actually using old machines.

***Edit**: I should also add that I have succeeded to run **Knoppix** on a 400 MHz PC. On that particular one, a Compaq Presario 5640, with some extra RAM, Knoppix outperformed Puppy Linux, although Knoppix is not regarded as a tiny linux distro.*

---

