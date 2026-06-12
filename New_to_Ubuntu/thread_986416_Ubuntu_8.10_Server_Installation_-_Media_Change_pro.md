---
title: "Ubuntu 8.10 Server Installation - Media Change problem"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Rusty0918 on 2008-11-18
In the midst of installing Unbuntu Server 8.10, when its doing the base system install, I get this error:

Please insert the disc labeled: 'Ubuntu-Server 8.10 -Intrepid Ibex8 Release i386 (20081028.1)' and press enter. I'm running this off a burned CD-R with the image on it.

My system is an Intel Core 2 Quad Q6600 with 2 GB of RAM. I have three hard drives (I have no problem with the partition stuff). It's when I install the base system this error is thrown. Do I need another CD? Did I not burn it properly?

---

### Post by mikewhatever on 2008-11-18
It wouldn't hurt trying another cd. You may have done the burning properly, but nothing is bullet proof. The cd may also be damaged or such.

---

### Post by Rusty0918 on 2008-11-18
I tried that and it didn't work.

---

### Post by nowhere@cox.net on 2009-01-09
Anybody fix this? It's happening to me now. I have used this CD on two other systems and now it is doing this exact same thing to me. Also there is another thread with it happening to at least 2 other people using the alternative CD...

Help please...

---

### Post by rvarnam on 2009-01-21
I'm having the same problem with Ubuntu 8.10 desktop (alternate) CD, on a Sony Vaio TT1 notebook. This install disc works fine on serveral other machines. I've tried reburning it, and have restarted numerous times.

I get to "Install base system", and it halts saying "Please insert the disc labelled 'Ubuntu 8.10 _Intrepid Ibex_ - release i386 (20081028) in the drive '/cdrom/' and press enter"

Any solutions very welcome!

---

### Post by cloudedice on 2009-01-22
Based on the discussion around [Bug #270461]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/270461") and adding in my own experience, it appears to be the fault of an NEC DVD-RW drive.

Try installing using another CD/DVD drive.

-ice

---

### Post by adriandel713 on 2009-04-05
I'm how this worked or what, but what I did is simultaneously run a live CD, and I had a USB-bootable ISO plugged in at the same time. Since my computer is somewhat old, it only had the USB-FDD boot option, so I went ahead and retried the install using the LiveCD. When it got to the installation part, it lagged for like 30 secs, I was thinking it was about to get stuck again when it finished the install! awesomeness lol

I was installing Ubuntu 8.10 I386 on a HP pavilion 514c. 

For those that don't know, here is a link on how you create a bootable USB. [http://www.associatedcontent.com/article/1104496/how_to_make_a_linux_livecd_iso_boot.html?cat=59](http://www.associatedcontent.com/article/1104496/how_to_make_a_linux_livecd_iso_boot.html?cat=59)

wish the best!

---

