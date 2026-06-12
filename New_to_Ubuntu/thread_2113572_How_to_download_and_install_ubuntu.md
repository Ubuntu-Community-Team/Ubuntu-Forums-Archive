---
title: "How to download and install ubuntu?"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by mdrowe on 2013-02-07
OK.  I paid $16 and downloaded Ubuntu 12.10 to put on a disk.  But my CD  is too small for it (no DVD).  I moved it to a thumb drive, but can figure out how to get my computer to find it to boot.  I downloaded the Windows installer (no $16 this time) and tried to run it, but it says I don't have enough disk space.  That, of course, is part of why I am trying to install Ubuntu and uninstall Vista.

So now I am out $16 with no Ubuntu and no obvious way to get it to boot.  And my hard drive is even fuller.  What do I do?

---

### Post by mdrowe on 2013-02-07
That should read "I can't figure out....."

---

### Post by steeldriver on 2013-02-07
Just moving the downloaded ISO file to a thumb drive doesn't make it bootable - you need to use something like unetbootin

[http://sourceforge.net/projects/unetbootin/](http://sourceforge.net/projects/unetbootin/)

---

### Post by Frogs Hair on 2013-02-07
Ubuntu has an optional donation on the official site and is free unless you chose to donate. If you select take me to download the download will begin free of charge.    

The link may help with the USB.  [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

---

### Post by ubuntu27 on 2013-02-07
How to burn an ISO file to DVD:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by mdrowe on 2013-02-07
But as I said, I don't have a DVD drive and a CD is apparently not big enough.

---

### Post by wildmanne39 on 2013-02-07
Hi, burn the image to an usb stick if your computer can boot from a usb stick.
Thanks

---

### Post by sudodus on 2013-02-07
> **steeldriver said:**
> Just moving the downloaded ISO file to a thumb drive doesn't make it bootable - you need to use something like unetbootin

[http://sourceforge.net/projects/unetbootin/](http://sourceforge.net/projects/unetbootin/)

+1

There are many ways to make USB boot drives. I have good results with Unetbootin, and would recommend it too.

Good luck :-)

---

### Post by gifford on 2013-02-07
You could download 12.04 LTS and it will fit on a CD.

---

### Post by bogdarnet on 2013-02-07
If you really need a CD, you can do a minimal install:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

(The USB is probably a better solution though.)

---

### Post by wildmanne39 on 2013-02-07
Changed title to be more descriptive.

---

### Post by mdrowe on 2013-02-07
How do I make my machine look for the USB drive?  It only looks at the CD drive.  Windows Help is not at all helpful on this.  

Also, all I did was copy the downloaded files to a thumbdrive. Are they bootable as-is? Will they install as-is?

---

### Post by wildmanne39 on 2013-02-07
Hi, newer computers have a boot menu when you turn them on just look to see what key to hit to enter it then you can select boot from usb stick, or go into setup when the computer turns on and change the boot order.

No you have to burn the image to disk or usb stick.
Thanks

---

### Post by mdrowe on 2013-02-07
Thanks Wild Man.  That's the kind of help I needed.  

I don't understand why it is not easy just to follow the download instructions and they work.  There surely must be a lot of dumb old farts like me who just want to click some buttons without much understanding.

---

### Post by wildmanne39 on 2013-02-07
Your welcome! It is a lot easier now then it use to be.

---

### Post by MadmanRB on 2013-02-07
With trying linux its not as easy a copy and pasting an image to a disc, its a tad morer complicated then that but not so impossibly complicated.
You see the format of the USB or disk must be carried in a certain way to be read by the BIOS or motherboard.
A raw image wont do, you need to make it readable for your computer to understand it.
The tool I use on windows is lili usb, a wonderful usb writing tool that does wonders even more so than unetbootin as it supports far more linux variants.
Or for disk image writing I use InfraRecorder

---

### Post by wildmanne39 on 2013-02-07
+1 for InfraRecorder and there should be directions on the download page for installing and using it.

---

### Post by mdrowe on 2013-02-07
It seems really stupid to me that the downloaded file can't be opened in Windows, with instructions on what to do.  I can't even read the contents.  At a minimum, there should be some kind of readme file on how to make it work once it is downloaded.

Do Linux aficionados want to remain an exclusive club ("I'm in the Ingroup.  Na Na Naa!")?  Or do they want to spread the word?

---

### Post by wildmanne39 on 2013-02-07
Hi, there are instructions for installing ubuntu on the download page.
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

It is not ubuntu's fault the windows can not read ubuntu files, windows does not want to make it easy to leave them.

---

### Post by mdrowe on 2013-02-07
That's great.  Except the Pendrive installer can't find the Ubuntu file that I downloaded as instructed and is sitting in plain site on my desktop.

---

### Post by sudodus on 2013-02-08
> **mdrowe said:**
> That's great.  Except the Pendrive installer can't find the Ubuntu file that I downloaded as instructed and is sitting in plain site on my desktop.

1. Boot from USB

You have received a lot of advice and tips about several tools or 'installers' to make a bootable USB drive from your downloaded iso file.

Which installer are you trying to use? If you tell us, we can focus on that one (or the guy who suggested it and knows it well, can describe what to do).

2. Boot from CD

You have also been adviced to download other iso files (versions with Ubuntu), that will fit into a CD disk. Have you tried that? I think it is a good idea to try 12.04 LTS instead of 12.10 because it fits into a CD, because it is a version with long time support, and because it is better debugged now, so quite stable.
--
*Edit*: And it's free software, you can download as many iso files as you like and test them without paying anything.

---

