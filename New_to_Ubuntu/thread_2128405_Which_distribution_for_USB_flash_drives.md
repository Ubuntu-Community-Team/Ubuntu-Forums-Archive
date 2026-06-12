---
title: "Which distribution for USB flash drives?"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by susanne260 on 2013-03-23
I have an old Thinkpad T61 laptop that I mostly use for writing documents.

I'd like to remove the hard drive and run some lightweight GNU/Linux distribution from [a tiny USB flash drive](http://www.intenso.de/produkte_en.php?kategorie=23&&produkt=1291709095). I don't need an HDD or SSD because I'm not going to have any big files on it.

Is there a distribution created for this purpose? I mean, something that doesn't cause a lot of disk writes and is optimized for running from a USB flash drive? It should use the RAM as much as possible and write to the disk as little as possible. It also needs to have a GUI.

Or is it better to just go with something like Xubuntu or Lubuntu and try adding things like &#8220;relatime&#8221; to fstab?

And how would I actually install it to the USB drive? Do I install it just like I install distros to a regular HDD? Or is it better to use something like unetbootin with the persistance option?

Also, which filesystem is the best for USB flash drives?

---

### Post by Isamu715 on 2013-03-23
[KNOPPIX]("http://www.knopper.net/knoppix/index-en.html") is a distribution made specifically for LiveCD/DVD/USB usage. It has a lightweght GUI environment and an "Install on a flash drive" option in menu with a dedicated flash drive installer which takes care of the process.

---

### Post by grahammechanical on 2013-03-23
Do not forget to do the install with "persistence." Otherwise the USB stick would be just like a CD/DVD version of Ubuntu.

[http://www.pendrivelinux.com/what-is-persistent-linux/](http://www.pendrivelinux.com/what-is-persistent-linux/)

Yesterday I used Startup Disk Creator to put Ubuntu Kylin on a 16GB USB stick and I could set the persistence file up to 4GB big. Smaller sizes of USB stick will give you a smaller persistence file and it is there that documents and settings will be stored.

Other Linux distributions might give you more space, comparatively speaking. If using Startup Disk Creator you just point it the ISO file that you want to create the USB stick from. You can experiment with different distributions. All you need is to download the ISO image. I found Startup Disk Creator simple to use.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Notice the How Much slider under Stored in Reserved Extra space.

Regards.

---

### Post by oldfred on 2013-03-23
When you say tiny flash drive, how small?

If 8GB or more you can do a full install, otherwise you have to use the live installer version but add persistence to have some storage space.

 HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
      
 Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)


 HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

---

### Post by ManamiVixen on 2013-03-23
Puppy Linux does wonders on old hardware and is designed specifically for USB's or CD.

---

### Post by gordintoronto on 2013-03-23
According to this somewhat dated, but still relevant, writeup:
[http://linux.koolsolutions.com/2009/01/26/installing-linux-on-usb-part-1-difference-between-usb-hard-drive-and-usb-flash-or-jump-or-thumb-drive/](http://linux.koolsolutions.com/2009/01/26/installing-linux-on-usb-part-1-difference-between-usb-hard-drive-and-usb-flash-or-jump-or-thumb-drive/)

ext2 and relatime are good options!

I think the choice among Ubuntu/Lubuntu/Xubuntu/Mint depend on CPU speed and personal preference, as long as the computer has 2 GB of memory.

I would not install to a flash drive smaller than 8 GB, and if I was going to use it ongoing, I would choose at least 16 GB -- which will put you back around $10 these days!

---

### Post by KdotJ on 2013-03-23
I'm a huge fan of CrunchBang ([http://crunchbang.org/](http://crunchbang.org/)) which is basically Debian with a very lightweight desktop (it uses OpenBox). It's a great distro to run from a USB and idles at very low memory.

---

### Post by H9D1uAehOP on 2013-03-23
What about Slitaz? It isn't Debian or Ubuntu based but it's a great distro. Or if you have a 16GB or bigger USB flash drive you can do a full install with Ubuntu, Xubuntu, Lubuntu, etc.

---

### Post by susanne260 on 2013-03-25
Thanks to everyone for replying. I tried out all the distros mentioned in this thread and decided to go with Ubuntu 12.04.2 LTS with the persistence option at the moment. Puppy and Knoppix looked like better choices, but I don't have time to customize them my needs right now. Although I especially liked the following line from Puppy's Wikipedia page:

> Puppy also features sophisticated write-caching system designed to extend the life of USB flash drives that Puppy Linux runs from.

But I guess that it may not be as important, because USB sticks are so cheap nowadays.

 oldfred: by "a tiny usb flash drive" I was referring to the physical size of the drive. :)

---

