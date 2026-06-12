---
title: "cannot clear boot flag"
date: 2022-01-30
forum: New to Ubuntu
---

### Post by dented-buffalo on 2022-01-30
I still new to using Linux (I've just been diving into it).  Also, this is the first time I've posted anything to any forum.  First time EVER.  Stop me if you've heard this one (and point me in the right direction).  I have Ubuntu 20.10 (codename: groovy) installed on a 128gb Sandisk microSD in a Raspberry Pi 4b (8gb).  I want to remove Ubuntu and reformat the card.  I've tried everything that I can find of the internet:

1. Tried to clear the boot flag using gparted. No luck, wouldn't clear the flag.
2. Tried reformatting using gparted.  No luck.
3. Tried reformatting using fdisk.  No luck.
4. Tried clearing the boot flag using fdisk (command 'a').  No luck.
5. Tried reformatting using Windows 10 Disk Manager.  No luck.
6. Tried reformatting using use Windows Powershell diskpart.  No luck.
7. Tried removing Readonly attribute using Windows Powershell diskpart.  No luck.
8. Tried download sketchy partition tools.  No luck.
9. Tried putting the microSD card in my Android phone and reformatting (and put it in a camera).  No luck.
10. Tried reformatting the card on Zorin, Mint, a different installation of Ubuntu (on a virtual machine), and even whonix (on a virtual machine).  No luck.
...

I'm probable forgetting a few attempts...  I can still boot up the Ubuntu and use it.  However, I am not able to update it... weird.  Even as I type this post, I am using this troublesome Ubuntu installation to do so.  It's like a demon that cannot be killed.  If anyone can help solve this problem, they would easily be crowned the king (or queen... or something else; I'm not judging) of technological stuff.

---

### Post by Impavidus on 2022-01-31
Ubuntu 20.10 reached end of life in July 2021. That's why you can't update it and why it's good you want to get rid of it.

The boot flag is ignored by Ubuntu. It's used by the Windows bootloader and I think only on MBR partitioned drives (not sure about that), but is not used by anything related to Ubuntu.

The normal way to remove an operating system is by formatting its partition and overwriting the bootloader. Formatting the drive does both at the same time. If you can't format the sd card, there are three possibilities: you do it wrong, it's write-protected or it's broken.

When you run the operating system on the sd card, can you save files to it? And are the files still there after rebooting? Is this a full install or a live system? Does gparted give you any error messages when you try to format the sd card? Note that you can't reformat the drive with the currently running OS, so you have to take the sd card out of your raspberry pi and put it into a different computer with its own operating system with gparted. Formatting it on a phone or camera should work too.

Standard sd cards have a write protect switch, but its not on micro sd cards and I don't think there's one on the adapters used to put a micro sd card in a standard sd card reader.

---

### Post by him610 on 2022-02-01
Recommend you try with *mkusb* - how to use mkusb [https://ubuntuforums.org/showthread.php?t=1958073]("https://ubuntuforums.org/showthread.php?t=1958073")
You may need an adapter SD to USB.

---

