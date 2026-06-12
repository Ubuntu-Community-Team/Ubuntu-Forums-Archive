---
title: "Install on older Pentium PC"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by Ham13 on 2013-01-11
Hello All,
 
New to Linux but some background with Unix many moons ago. I have an older Pentium PC 600 MHz, 128 M memry and 12 Gb hard drive. It is running Windows 2000 Professional. Originaly it was a linux machine. Before I could load Windows I had to restore the MBR with a piece of software from the net. I would like to install Ubuntu on this machine to use it as a test machine. There are several Linux apps I'd like to test.
I'd also like to preserve at least the Windows OS files if possible. What version of Ubuntu should I install and is a dual boot system practical with this older system?
 
If Ubuntu answers my need I would want to put it on a more modern HP Pentium III i gig/3 gig machine. That one is also running Windows 2000.
 
all advice will be appreciated.
 
Thanks,
Marty:D

---

### Post by oldrocker99 on 2013-01-11
If the PC boots with any other OS, when you install *buntu, it will detect that OS, and you'll be presented with the option to install *buntu side-by-side, with a boot option, or to format the whole disk, etc. Obviously, if you install side-by-side, all the files you want to keep will be untouched, and can easily be accessed from within your Linux box, since it can easily read, write, etc. to files on a NTFS partition.

Boot from your choice of live disk (given your machine, I'd personally suggest Lubuntu) and hack away!)):P

---

### Post by deadflowr on 2013-01-11
Ubuntu is a little heavy for the RAM you've listed.
Instead I would point you to these others:

[Bodhi Linux]("http://www.bodhilinux.com/")

[Lubuntu]("http://lubuntu.net/")

[Xubuntu]("http://xubuntu.org/")

Bodhi is very lite.

---

### Post by qyot27 on 2013-01-11
> **Ham13 said:**
> I have an older Pentium PC 600 MHz, 128 M memry and 12 Gb hard drive.
...
I'd also like to preserve at least the Windows OS files if possible. What version of Ubuntu should I install and is a dual boot system practical with this older system?
Spec-wise, you'd likely be needing to look at Lubuntu.  The HDD size is the trickier part.  Dual-booting it would possibly be a very tight fit space-wise, but it's possible.

> If Ubuntu answers my need I would want to put it on a more modern HP Pentium III i gig/3 gig machine. That one is also running Windows 2000.
This is something I have more experience with.  My main computer uses a 1GHz Celeron Coppermine - which means it's a stripped-down Pentium III.  512 MBs of PC-133 SDRAM in addition.  I run both XP and Ubuntu 12.10 on it with zero issues (like the Lubuntu example, I primarily use LXDE when under Ubuntu, but so long as you have a halfway-decent graphics card you can also run Unity - I have a GeForce 6200 installed, so after initial install I can move around well enough to get the basic setup done before I move fully over to LXDE).

---

### Post by snowpine on 2013-01-11
I recommend you properly recycle your Windows 2000 machine and upgrade your hardware.

Here are the hardware requirements for Ubuntu: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Here is a $25 Linux computer: [http://www.raspberrypi.org/](http://www.raspberrypi.org/)

---

### Post by grahammechanical on 2013-01-11
Has anybody mentioned this?

> 12 Gb hard drive.

Ubuntu will install into about 5GB but I doubt if 12GB would be enough for a dual boot. You just might get by. But you will not have much space for documents.

Regards.

---

### Post by mysteriousdarren on 2013-01-11
+1 for Lubuntu, but I would go with Puppy Linux or a lighter OS due to the 12GB hard drive. Puppy can have debian packages installed that are the basis for Ubuntu. I highly recommend that as a second choice to Lubuntu.

---

### Post by audiomick on 2013-01-11
I'll mention the hard drive again. Then I'll mention the RAM.

12GB will be very tight. A second drive would be more than a good idea.

128MB is practically no RAM these days. You would most likely be able to run Lubuntu on there, but if you can get some more RAM in there it would help.

---

### Post by tlhIngan on 2013-01-11
My Lubuntu install is under 3 GB, so space is not the issue.
RAM is.
Lubuntu wouldn't install properly on my 256 MB machine until I pooled all the RAM in the house together. I understand Kubuntu and Xubuntu are a little heavier still. Your HP PIII will be perfect for this, but for your older machine, look for something lighter.
I don't know about Puppy Linux or Bodhi Linux, you may want to look into those.

---

### Post by mörgæs on 2013-01-12
Let go of this one and buy some used (3-4-5 years old) gear. It will cost you a very modest amount.

If you happen to get an operative system running, what about a browser and a media player? With 128 MB you will only get lags.

If people in general want to play with light distros here are some options:
[http://ubuntuforums.org/showthread.php?t=1582027](http://ubuntuforums.org/showthread.php?t=1582027)

---

### Post by codingman on 2013-01-12
Slitaz is an option, but I certainly suggest upgrading your RAM and HDD if you are going to use Lubuntu.

---

### Post by deadflowr on 2013-01-12
Adding to my earlier advice, you can upgrade the hard drive and just turn it into a basic home file server.
Then use it to backup your other systems.

---

### Post by Ham13 on 2013-01-12
Thanks for the advice. I think I'll  install Ubuntu on the larger PC. I still want to do a dual boot though. My understanding is that the install routine will see an ntfs partition and automaticaly default to a dual boot install. Thus preserving the existing Widows OS and file system without any manual partitioning of the HD with fdisk.
 
Please tell me if this is an incorrect assumption. The manual indicates that this is the case, I think, but I'm not clear on the proper way to get to a dual boot system.
 
Thanks for your continued help. It is appreciated.
 
Marty

---

### Post by audiomick on 2013-01-12
The install routine will, all things being equal, see that there is an Operating System installed. It will offer you a couple of choices including "use the whole disk" and "install beside" which is obviously enough the one you want for a dual boot.

There is also the option "something else" which will bring you to the manual partitioning step. If you, for instance, want to put your /home directory on a separate partition, or if you want to determine partition sizes yourself, this is where you want to go.

---

### Post by mörgæs on 2013-01-13
> **Ham13 said:**
> I think I'll  install Ubuntu on the larger PC.

I would recommend Lubuntu. You could try both of them in a live boot to see the difference.

---

