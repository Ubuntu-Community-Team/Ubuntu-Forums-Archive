---
title: "Zero memory.. possible partition problem?"
date: 2014-07-04
forum: New to Ubuntu
---

### Post by neonsuntan on 2014-07-04
1 - I took an old Vista laptop and fully installed Ubuntu 14.04.

2 - It ran very slowly... I tried to install zram as recommended on various other forums but I just couldn't make it work.

3 - I decided to install Puppy linux instead

4 - Puppy Linux was running from a DVD last time but today it presented a series of commands and then stalled.

5 - Ejecting the disc and turning the power off and on again I found that Ubuntu was still installed, but now a message said that there were memory problems.

[IMG]https://farm4.staticflickr.com/3908/14388045879_ff2d237f06_n.jpg[/IMG]

6 - I clicked on examine and this gave the following information

[IMG]https://farm6.staticflickr.com/5547/14573857122_863372ddf0.jpg[/IMG] [IMG]https://farm4.staticflickr.com/3885/14388027198_4eac0d9b00.jpg[/IMG]

7 - Ubuntu does run, but regularly seems to crash or hang indefinitely.

8 - Should I just reinstall from scratch?

Machine specifications

Intel Celeron M430 1.73ghz
1024 Mb DDRII RAM
INtel 943GML (Calistoga) + ICH7-M with up to 128 MB shared memory Supports INtel GMA 950
80Gb HDD SATA

Thanks in advance!

---

### Post by yancek on 2014-07-04
I'm not that familiar with Puppy or slacko but usually, what it does on shutdown is ask you if you want to save the pup.sfs file (not sure that is the correct name?).  It looks to me from what you posted like you did a frugal install of Slacko into the /boot partition which is much smaller.  You haven't posted any information on any other partitions including Ubuntu so that doesn't give much information.  If you did the frugal install, you should have put it on a larger partition.  The boot partition is full now.  If you don't have any data that is important to  you, it would probably be faster and easier to reinstall whatever you want to reinstall.

---

### Post by neonsuntan on 2014-07-04
SO can I just delete the partition and allow Ubuntu to write over it?

---

### Post by ibjsb4 on 2014-07-05
It sounds like you still have Vista installed, use vista to delete the partition.  Vista, back in its hay-day, at times had problems with the ubuntu (gparted) partition manager.

The ubuntu installer will see the free space and give you the option to install to that space.

You say that ubuntu runs slow.  It could be that Ubuntu is too resource demanding for your laptop.  There are two other flavors of ubuntu that use less resources.

The medium weight
[http://xubuntu.org/](http://xubuntu.org/)

And the lite weight
[http://lubuntu.net/](http://lubuntu.net/)

What are your laptop specs?

---

### Post by grahammechanical on 2014-07-05
The graphic card does not, in my opinion have enough of its own memory to run Ubuntu+Unity. And it is shared memory which, as I understand it, means that it is using some of the RAM which is not then available to the OS. Furthermore, if the video card is unable to run Unity 3D then Ubuntu uses as a fall back an open source video driver called llvmmpipe which tries to present an approximation of Unity 3D but the effect is very slow in comparison to newer hardware.

Regards.

---

### Post by Rob Sayer on 2014-07-07
> **neonsuntan said:**
> ... 8 - Should I just reinstall from scratch?

IMHO, yes.  It's actually sometimes the easiest way.  If you've replaced windoze with linux ("fully installed Ubuntu 14.04"?) you should look into installing with a separate /home partition, which isn't hard but admittedly will take some reading.  You don't need a really big / partition.  If you have windows or another OS as well you wouldn't have enough partitions to do this.

> Machine specifications

Intel Celeron M430 1.73ghz
1024 Mb DDRII RAM
INtel 943GML (Calistoga) + ICH7-M with up to 128 MB shared memory Supports INtel GMA 950
80Gb HDD SATA

As mentioned above, ubuntu with the Unity desktop is not a good choice with this hardware.  I tried unity on my i3 based laptop with 4Gb RAM and it was too slow.  And the Intel GMA (I forget what model) does 3D hardware acceleration reasonably well.  I'm not sure the 943 gma supports 3D acceleration at all, but if it does it's not fast from what I just looked at on the web.

The main thing is that there are other linux distros that are lighter than ubuntu, but they're not particularly noob friendly.  I wouldn't actually recommend anything but ubuntu for novices because they make the process simpler and, particularly, no one else comes close for support, which you'll quite possibly need.

Modern DEs like unity or cinnamon or other gnome 3 based desktops require hardware 3D acceleration just to run *themselves*.  On a machine with 1Gb RAM it's going to be disastrously slow unless you also have a modern video card with at least 1Gb itself.  Not a lot of people have this combination.

I'm typing on a 1Gb netbook with a dual core cpu but poor video card (cedarview).  I wouldn't dream of installing unity on it.  I've run lubuntu and xubuntu on it.  Presently it's xubuntu 14.04.  Frankly I found lubuntu 14.04 buggy but it may run a *lot* faster on your machine.

---

