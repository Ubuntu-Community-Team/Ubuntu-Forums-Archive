---
title: "Grub pProblem with upgrade from Gutsy to Hardy"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by matrixunloaded on 2008-06-19
I am a complete Newbie.

I have Grub set up with choice 1 (default to Win XP). Gutsy 7.10 with kernel 2.6.22 was 2nd and 3rd.

During Hardy upgrade, I chose keep local menu options.  As a result, I had the same menu although I had Hardy running.  Even nVidia drivers.  

What I didn't realize was that I was still loading 2.6.22 instead of 2.6.24.

Sometime later when using update manager, I think it updated Grub and I again chose local options.  After the update I lost screen resolution except for 600 x 800. 

After a day of uninstalling and reinstalling nVidia drivers, I finally noticed that the menu still reflected 7.10 and kernel 2.6.22.

I edited menu.lst to reflect 2.6.24, but botched the job -- I left the reference to 7.10.

Now I can only boot into Win XP, Grub saying the other choices  are not available.

How can I fix this other than a clean install of Hardy?  I have a lot of data I do not wish to lose.  Thanks!

---

### Post by mikeyphi on 2008-06-19
Try to run the command "update-grub"

If the grub screen gives access to a recovery mode - boot into that;
if not - use the LiveCD to get access to your system.

---

### Post by matrixunloaded on 2008-06-19
Using Super Grub I was able to boot using the backup of menu.lst.

I am also able to use gedit to try to edit menu.lst in /boot/grub, but when I try to save it there I get a message that I do not have the permission to save there. I can save it as menu.lst.doc to my Desktop, however.

Three questions:

1. How do I save the edited menu.lst to /boot/grub?
2. Do I keep the same UUID for 8.04 as it is in 7.10 (abbreviated as {UUID} in question 3 below)?
3. Are these the right changes for the Hardy section of menu.lst (following the XP section and chainloader +1):

title   Ubuntu 8.04, kernel 2.6.24-18-generic
root    (hd0,0)
init    /boot/vmlinuz-2.6.24-18-generic root=UUID={UUID} ro quiet splash 
/boot/initrd.img-2.6.24-18-generic

with similar changes for the recovery mode section?


Thanks for any help.  I fear I am over my head!

Matrixunloaded

---

### Post by mikeyphi on 2008-06-20
> **matrixunloaded said:**
> Using Super Grub I was able to boot using the backup of menu.lst.

I am also able to use gedit to try to edit menu.lst in /boot/grub, but when I try to save it there I get a message that I do not have the permission to save there. I can save it as menu.lst.doc to my Desktop, however.

Three questions:

1. How do I save the edited menu.lst to /boot/grub?
2. Do I keep the same UUID for 8.04 as it is in 7.10 (abbreviated as {UUID} in question 3 below)?
3. Are these the right changes for the Hardy section of menu.lst (following the XP section and chainloader +1):

title   Ubuntu 8.04, kernel 2.6.24-18-generic
root    (hd0,0)
init    /boot/vmlinuz-2.6.24-18-generic root=UUID={UUID} ro quiet splash 
/boot/initrd.img-2.6.24-18-generic

with similar changes for the recovery mode section?


Thanks for any help.  I fear I am over my head!

Matrixunloaded


1. Open a terminal,  enter gksudo (return) enter gedit /boot/grub/menu.lst  (return)
Following amendment of the file use the drop-down menu option File/Save to save the new file
2. UUID relates to the partition - if it's the same one as 7.10 was on then that's OK!
3. Looks OK - here's part of mine:
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f860e595-c1ea-40bc-b7a4-bfccf94152ea ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f860e595-c1ea-40bc-b7a4-bfccf94152ea ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

Your (hd2,0) and UUID will be different, kernel depends on updates

---

### Post by matrixunloaded on 2008-06-20
Thanks!  Your instructions worked like a charm.  Afterwards, I needed to run dpkg --configure -a, then finished updates, and now everything in Hardy 8.04 is working with the 2.6.24-19 kernel.

With such great support from the Ubuntu Community, I may soon get rid of my dual boot Win XP/Ubuntu configuration.  You would never get this kind of support for Windoze (even paying an arm and a leg) that is given by everyone here so freely!  It is a breath of fresh air.

Thanks again!!!

---

### Post by drs305 on 2008-06-20
For editing the grub menu for changing which OS to boot, which kernels to display, menu display timing, etc, I highly recommend StartUp-Manager. It doesn't work when a grub menu is lost or hard drives are changed, but for everyday editing it is great. It prevents many of the miscues of trying to edit the menu.lst manually.

[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

