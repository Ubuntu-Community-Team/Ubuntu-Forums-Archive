---
title: "Grub Load Error 21"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Ravenark on 2008-07-08
Hey guys, I'm brand new to ubuntu and was wondering if you could help me out with a problem I'm having.

I recently installed ubuntu hardy heron onto my external hard drive, and now everytime I boot up my computer it has a Grub Load Error 21 unless the external hard drive is plugged into the computer.

Did i screw something up?  And can I fix this? =/

Thanks,
Ravenark

---

### Post by ChameleonDave on 2008-07-08
Adding drives to a system can confuse it by changing the identifiers it uses to distinguish between them.

You can probably fix this by entering your motherboard's BIOS configuration at start-up and making sure that your main hard drives are always given priority over USB devices.

To fix it from within Ubuntu, you will have to go to the command-line terminal and input the following commands.  Then, paste the output of them here, so that we can see what to do.

```

cat /etc/fstab
sudo blkid

```

P.S. Sorry, I misread you.  I thought you said it didn't work unless you didn't have the external drive in, rather than it didn't work unless you did have the external drive in.

You can only fix this from the BIOS, or make sure that your external drive is not plugged in at start-up.

---

### Post by logos34 on 2008-07-09
I think what happened is that when you installed ubuntu, the installer wrote Grub to '(hd0)' -- in this case your internal drive.  That's the default unless you tell it otherwise.  So grub gets put on the internal, but it still needs to pull up the menu.lst at boot, which is located on the USB drive.  If it's not plugged in grub can't find it.

A very common problem.

Restore the windows boot loader with Super Grub Disk or windows install cd (recovery console>fixmbr).

Then [write grub to the MBR of the external drive]("http://ubuntuforums.org/showthread.php?t=224351"), and edit /boot/grub/menu.lst to reflect the change.

> sudo grub

> find /boot/grub/stage1
> root (hd1,?) 
> setup (hd**1**) 
> quitReboot and enter the Bios...set USB drive first in boot order.  On the grub screen select ubuntu and press 'e' to edit, 'e' again on 'root' line and change from (hd1,?) to (hd**0**,?).  [*The reason being that as soon as your set the external as the boot drive, it it seen as '(hd0)'.]   Press 'enter' and 'b' to boot.  Once inside linux make the change permanent:

gksudo gedit /boot/grub/menu.lst

Change 'groot' and 'root' lines to match.  (hd**0**,?)

When the drive is plugged in, the machine will boot grub.  If not, it will boot windows. (you can even add a windows entry to grub to allow you to choose it from the menu.)

---

