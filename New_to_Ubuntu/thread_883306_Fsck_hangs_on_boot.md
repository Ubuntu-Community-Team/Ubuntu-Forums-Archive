---
title: "Fsck hangs on boot"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by dchey on 2008-08-07
I am running Ubuntu 7.10. I am running a dual boot with vista. Ubuntu is on a 500 gb sata and vista is on a 40gb ide. My system ran great until the new run of updates started approx 1 1/2 to 2 months ago. My system runs until it has reached 25 boot cycles then on the next boot only the first boot screen ( with the logo and bar) is shown then the cursor goes to the upper left corner of a black screen and hangs. I have left it in that position for up to an hour. CTL-ALT-DEL has no effect nor does Control-D. The system must be powered off and rebooted into recovery mode. Fsck will then run and resume until it has booted 25 times then repeat of the above. Does anyone have similar problems and hopefully a solution or two.

---

### Post by Locutus_of_Borg on 2008-08-07
"not" recommended fix:
```
sudo nano /etc/fstab
```
change the numbers at the end of the line that has the mount point / both to 0
now it will never fsck unless you implicitly tell it to run fsck by issuing ```
sudo touch /forcefsk && sudo telinit 6
``` which will reboot and fsck

probably what you should do though is:
```
nano /boot/grub/menu.list (or grub.conf)
```
and delete from the kernel line at the end, the words "quiet splash"
now when you reboot, you will be able to see messages and maybe diagnose where it stalls

---

### Post by Yannick Le Saint kyncani on 2008-08-07
hi dchey, I would fsck from a licevd with verbose messages and see what happens.

---

### Post by dchey on 2008-08-07
> **Locutus_of_Borg said:**
> "not" recommended fix:
```
sudo nano /etc/fstab
```
change the numbers at the end of the line that has the mount point / both to 0
now it will never fsck unless you implicitly tell it to run fsck by issuing ```
sudo touch /forcefsk && sudo telinit 6
``` which will reboot and fsck

probably what you should do though is:
```
nano /boot/grub/menu.list (or grub.conf)
```
and delete from the kernel line at the end, the words "quiet splash"
now when you reboot, you will be able to see messages and maybe diagnose where it stalls
 Tahnk you for your quick reply will give a try and follow up.
dchey

I did try your option number three. It did not work on my system. I put an email into Launchpad also, and Marcobra had a repoce that did cure my problem.

** marcobra said 23 hours ago:** 

The system may be trying to perform the cyclic hard disk check and there is a message that you don't see.
Please remove the splash and quiet boot parameters to see more informative messages.
----------------------------
How to get more messages at Ubuntu startup

Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo gedit /boot/grub/menu.lst

give your user password when requested, you don't see nothing when you type it, then press enter.

Search the row

# defoptions=........ your options

and remove the "quiet" and "splash" parameter

save and exit

then type:

sudo update-grub

Reboot your pc and you will get more warning and messages at startup so you can investigate your slow boot issue.

--------------------

You can get even more messages by edit the /etc/default/rcS file

Please open a Terminal from the menu Applications->Accessories->Terminal and type:

sudo gedit /etc/default/rcS

and change the row

VERBOSE=no

to

VERBOSE=yes

Hope this helps

---

### Post by Victormd on 2008-08-07
This happened to me and I had to run it from the LiveCD. After that, all worked fine!

---

### Post by dchey on 2008-08-09
> **Victormd said:**
> This happened to me and I had to run it from the LiveCD. After that, all worked fine!
 I did atempt to run e2fdsk from the livecd however I am unable to. I ran umount /dev/sda and receive a message that the device is not mounted. when I atempt e2fsck /dev/sda the response is that the drive is locked. How were you able to do this?
dchey

---

### Post by Adramelech on 2008-08-09
It happened to me also, the problem was that fschk tried to check a partition twice. After the intial check the partition was mounted, and the second check failed because it cant check a mounted partition.

It is a fschk bug as i found on internet, it cant parse correctly the final argument of fstab so i have to disable the startup check.

---

### Post by Victormd on 2008-08-09
> **dchey said:**
> I did atempt to run e2fdsk from the livecd however I am unable to. I ran umount /dev/sda and receive a message that the device is not mounted. when I atempt e2fsck /dev/sda the response is that the drive is locked. How were you able to do this?
dchey

If you would like to unmount a drive, then you need to fix your unmount command it seems like you're missing an argument.
Run this:
```
sudo fdisk -l
```
to check which drives are mounted, then run the unmount command using the output from fdisk command:
It should be
```
 unmount /dev/sda1
```
(or sda2, sda3...)

Then, run e2fsck:
```
e2fsck /dev/sda1
```
(or sda2, sda3...)

Also, I don't remember if I ran as a SUDO command or not (i.e., sudo e2fsck /dev/sda1), so if you can't with the above command, run using SUDO.

---

### Post by Victormd on 2008-08-09
> **Adramelech said:**
> It is a fschk bug as i found on internet, it cant parse correctly the final argument of fstab so i have to disable the startup check.

Yeah, there is a bug, but running from the LiveCD solves this problem... and it's a good idea no let it run the check every now and then.

---

### Post by cariboo on 2008-08-09
Victormd you better check your sources, if you run fsck or e2fsck on a mount partition you run the risk of destroying valuable data. fsck will even ask you if you are sure you want to run it on a mounted partition. See this thread:

[http://ubuntuforums.org/showthread.php?t=437601](http://ubuntuforums.org/showthread.php?t=437601)

Jim

---

### Post by Victormd on 2008-08-09
You're right... after reading the link you posted, I remember running into that message (I did this a long time ago). Thanks for pointing that out, I fixed my previous post!

---

