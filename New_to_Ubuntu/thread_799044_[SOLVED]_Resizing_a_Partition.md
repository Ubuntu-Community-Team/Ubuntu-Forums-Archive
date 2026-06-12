---
title: "[SOLVED] Resizing a Partition"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by SIXAXIS on 2008-05-18
Well, here I am again. This time, I'm trying to resize my Ubuntu partition because Windows is my main OS and I think it needs a little more space (because of all the media that I have in Windows). When I boot from the Live CD, and I open GParted, I resize my Ubuntu partition (hda1) to 40GB. I press apply, all goes well until the last procedure, actually resizing. After looking at the details of the error (which I have below), it says "Please run e2fsck -f /dev/hda1 before". I did that in a Terminal window. It was successful, but I had to do it as root. Maybe that's why there was an error. Anyways, after I did that, I tried again and I have the same error (even with the Terminal window still open). What should I do to resize my Ubuntu partition?

[Here](http://www.freewebs.com/speedycomputer/Shrink%20Partition.png) is the screenshot I took.

---

### Post by shifty_powers on 2008-05-18
have yuo tried tha actually gparted livecd? sounds like you are using the ubunut live cd.

just google gparted livecd ;)

---

### Post by SIXAXIS on 2008-05-18
Will that be any different? Also, is it a GUI or is it a CLI? I don't mind the Terminal or Command Prompt, but I don't like CLI only. It scares me....

---

### Post by shifty_powers on 2008-05-18
heh, yeah the cli is scary.

it's a gui, and it won't mount anything ;)

try it and find out :D

---

### Post by NightwishFan on 2008-05-18
Gparted live cd is graphical with fluxbox.

---

### Post by SIXAXIS on 2008-05-18
So I did that and it was successul, but now I want to add that free space to the Windows partition. How do I do that?

In Windows, this is what it looks like in Manage:

[39.52GB - Ubuntu] [33.12 - Free Space] [612MB - Swap] [75.81GB - Windows]

---

### Post by aroch1 on 2008-05-18
You should be able to do that by resizing/moving the windows partition with the gparted live cd as well.

---

### Post by SIXAXIS on 2008-05-18
I did that and it worked. But when I try booting into Windows from GRUB, it gives me Error 13 and something about an executable that can't be run (or something of that sort). I will try the Vista install DVD to repair it.

---

### Post by SIXAXIS on 2008-05-19
This is what I did. After trying the Vista DVD (which didn't even see Windows installed on ANY partition), I went back into Ubuntu and found that the GRUB bootloader was trying to load from the wrong partition (because I moved the location of the partitions). After I changed that, Windows gave me an error of a missing file that's needed to boot. It gave me step-by-step instructions on how to fix it. I followed the instructions (which were just to run the startup repair utility on the Vista DVD) and it fixed Vista. After booting up Vista though, I had to restart because it had to reinstall the drivers for the "new" HDD.

---

