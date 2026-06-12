---
title: "Xubuntu installed via Vista - A real install?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Valve on 2008-06-19
Forgive me if I sound a bit dim, but I used the Xubuntu cd to 'install' Xubuntu via Vista and to have the option of booting into either OS. All well and good. Vista boots fine after choosing (or as the default if I take no action), Xubuntu also boots fine, but always gives a warning notice that the disk is not properly partitioned and that I should do this. Afterwards Xubuntu is ready to roll as normal.

Phew! My question is: is this install a correct (or normal) install, or just a test install. It seems to me to have partitioned 10gb (+) for Xubuntu, (small really considering my HDD is 300gb), 
I noticed also that on this boot (10 mins ago) it wouldn't boot straight into Xubuntu, I had to go through F12 and choose the OS manually.

Have I done something wrong? A little guidance would be helpful. I've read through the help guides, but no luck.

---

### Post by avtolle on 2008-06-19
I presume you installed using the Wubi installer. It is a "real" install, subject to the following: one, if Vista shoots craps, you have lost your ability to boot into Xubuntu, as the option to do so appears on the Vista Longhorn bootloader; two, it does not exist on a separate partition on the HDD, but rather within the Vista partition as a "folder"; and three, due to something I don't recall nor understand, access to the HDD is a bit slower than if it was a "real" install into its own separate partition. 

I installed Ubuntu 8.04 under Vista with this method while 8.04 was in Beta, just to try it out. I've had no problems with it, and have kept it updated, etc., just as I would a "real" install. 

When you installed, there was an option as to how large a virtual disk one could have for the *buntu install, I selected 15 GB (which, IIRC, was the recommended size). Not sure how Wubi handles this with Xubuntu. I've not had to do the F12 thing. Have you looked on the Wubi Forum for any threads for similar issues? I cannot recall seeing any, but I don't visit there every day.

---

### Post by tjwoosta on 2008-06-19
im a bit confused as to what you may have doe but this is the install process

1. burn the ubuntu .iso to a cd

2. reboot computer, and set bios to boot from cd

3. boot the cd 

4. folow the simple steps to install

5. when prompted where to install GRUB choose MBR (Master Boot Record) -this will overwrite the vista bootloader, but dont be concerned because you can boot into vista or Ubuntu from Grub

EDIT: o, ok  i see now  WUBI (that makes since now that i read it again)

---

### Post by avtolle on 2008-06-19
@OP: Just had a thought; did you defrag your HDD before doing the Wubi install? This may be a reason for the smaller default size of the virtual drive.

---

### Post by Valve on 2008-06-19
Thanks folks, I burned the .iso onto a cd, but I installed it whilst Vista was running (that's what the Xubuntu guide claimed I could do).
I need to read more about WUBI I suppose.

---

### Post by Duck2006 on 2008-06-19
Some reading on Wubi

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://ubuntuforums.org/showthread.php?t=594637](http://ubuntuforums.org/showthread.php?t=594637)

---

