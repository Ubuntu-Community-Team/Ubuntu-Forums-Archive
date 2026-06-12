---
title: "dual boot install gone badly wrong"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by warren13 on 2013-02-25
I dual boot LINUX and win seven. Recently I formatted my LINUX partition from within ms so I could install Ubuntu. I installed from the live CD and rebooted only to find no Ubuntu but grub listed my previous LINUX which of course didn't boot. Windows booted fine, so I formatted the LINUX partition again thinking to reinstall. I also deleted a 500 mb partition thinking it was grub and hoping Ubuntu would reinstall it correctly. I rebooted only to find the grub rescue on my screen and it says unknown file system. Not only that but the computer goes directly to grub rescue and will not use the CD or usb. Changes in B ios setup makes no difference. If I could use the CD drive this would be an easy fix. I tried ls and got hdo, hdo, msdos2 and hdo,msdos1. I tried set root and set prefix for each one then ismod normal but it always says unknown file system. Please help!

---

### Post by Enigmapond on 2013-02-25
Try burning this to disc, booting in and it will fix your GRUB
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by warren13 on 2013-02-25
Thanks Enigmapond. That looks good except that my laptop goes directly to grub rescue even when I make changes in the bios boot list. No CD, no usb.

---

### Post by oldfred on 2013-02-26
If you burned CD correctly as boot disk not a copy of ISO it should boot, same with flash drive. You should also have a one time boot key (f12 on my system) that will let you choose to boot CD or Flash as a one time option.

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by GregA on 2013-02-26
Just affirming Old Fred's reply.   Also, to be more certain of the current state of your PC, download & correctly burn a solid rescue CD such as "Parted Magic".

Then use Parted Magic's several utilities to scan your system and see what (if anything) remains of your files and OS's.  That way, you're no longer guessing.  You may be able to repair and/or copy your data files with the tools provided by Parted Magic.

IF you don't requre Windows, by far the easiest solution is to do a full disk install of Linux - it will install and also update the grub2 bootloader.   All my systems are now dual-boot, except my oldest laptop was also a victim of a "FUBAR" attempt to install Linux back in the day.   

But I chose to install "Kubuntu" (a win7 like linux, based on Ubuntu) on it and haven't looked back since.

good Luck!

---

### Post by Mark Phelps on 2013-02-26
If boot-repair does not work and you need to get access back to Win7, and are willing to pay a little money (seeing as how you could done this for FREE when Win7 was working) ... then read on ...

Go to the link below, purchase the disk image you want, download the ISO and burn it to CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Then, boot from that CD and run Startup Repair three times -- that's right, three times, as it often takes all three passes to get Win7 booting again.

---

### Post by warren13 on 2013-02-26
Thanks everyone for your replies. I can change the boot order on my laptop through the bios menu or by hitting the esc button on startup. Both methods fail to have an effect. Normally, it boots the CD first, but since this problem it goes directly to the grub rescue menu. I have the original windows 7 CD as well as half a dozen LINUX iso's that I have burned onto disk that always booted well before. As well I have a LINUX OS on usb stick. The laptop just goes to the rescue screen and ignores the drives.

---

### Post by BarfBag on 2013-02-26
> **warren13 said:**
> Thanks everyone for your replies. I can change the boot order on my laptop through the bios menu or by hitting the esc button on startup. Both methods fail to have an effect. Normally, it boots the CD first, but since this problem it goes directly to the grub rescue menu. I have the original windows 7 CD as well as half a dozen LINUX iso's that I have burned onto disk that always booted well before. As well I have a LINUX OS on usb stick. The laptop just goes to the rescue screen and ignores the drives.

Are you positive you are saving the changes to your BIOS before exiting?  Once the boot order is changed, there is no reason it shouldn't boot off of your disc (aside from hardware issues).

---

### Post by warren13 on 2013-02-26
I am sure.

---

### Post by GoranI on 2013-02-26
You can read this tutorial:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId16468](http://www.dedoimedo.com/computers/grub-2.html#mozTocId16468)

I remember in the past I had problem with Debian Squeezy grub menu an succesfuly edited it and added win7 to the menu.

I hope it will help you !

---

