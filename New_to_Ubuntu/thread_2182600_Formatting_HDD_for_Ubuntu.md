---
title: "Formatting HDD for Ubuntu"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by Paul_Stehle on 2013-10-21
Hi, New to all this:  I've got a PC running XP on which I'm trying to install Ubuntu (12.04.2LTS).  The install won't commence because the drive isn't formatted properly.  Is there a means to format it using the "try alongside windows" version running from the CD?  I can't start XP because it's infected with a nasty virus, and I have no other desktop available to move the drive to in order to format it via Windows.  Thanks in advance!

---

### Post by hammodi2 on 2013-10-21
run windows xp. go to control panel. then administrative tools then to computer  management then to storage then to disk management. wait few seconds and you will get a new window. on the bottom there is a place where it says  Disk0 or whatever disk it is. check how much free space you have, shrink that hdd. and create another partition. i recommend at least 10-12 GB for Ubuntu. then boot ubuntu and install it on that partition.

---

### Post by Impavidus on 2013-10-21
Do you have four primary partitions? Gparted (included in the live session) can tell you. It will also allow you to change the partitions of the drive, but it won't shrink your Windows partition if it's damaged.

---

### Post by Paul_Stehle on 2013-10-21
i can't run windows, as i said there's a nasty virus on it.  there are no files on the HDD that i need to preserve, just looking for a way of formatting it without starting XP.  thanks!

---

### Post by hammodi2 on 2013-10-21
you can do that with the windows xp. or any windows installation disk. just run it. do not install it. only reach the partitioning part. then do whatever you want with it.

---

### Post by newb85 on 2013-10-21
You don't need to format the drive from Windows before installing Ubuntu.  Actually, you can't.  Windows doesn't recognize or create the journaling filesystems Ubuntu uses.  If you boot from the Live DVD or USB and select Install Alongside Windows, proper formatting should be handled automatically by GParted (the default partition editor for Ubuntu).

---

### Post by ant2 on 2013-10-21
What is your exact intention. You say 'try alongside Windows' do you mean 'install alongside Windows'. Do you intend to try to fix your Windows XP installation and dual boot Windows with Ubuntu or do you simply wish to start fresh with a Ubuntu installation and **delete Windows** completely?

---

### Post by Paul_Stehle on 2013-10-21
I want to install Ubuntu and don't want Windows on the PC any more.  When I start the installer, the top box "has at least 4.3gb of space..." is x'd out.  It won't go any further without that, and I can't run XP any more.  It used to work, but a virus would pop up, now it just says "non system disk or disk error" when I let it try to start XP.

---

### Post by ant2 on 2013-10-21
Can you not (as @newb85 suggests) try installing from the live CD using Gparted, simply install to entire disk. Is this not working?

---

### Post by Paul_Stehle on 2013-10-21
Nope, there's two boxes it wants checked, one that says "connected to the internet", which has a green check.  The 2nd box says "has at least 4.3gb disk space..." and that one has an X.   I don't mind replacing the drive if that will help, the one in it now is only a 320gb.

---

### Post by ant2 on 2013-10-21
Try formatting the disk using Gparted from within the live session, therefore creating enough room to install by deleting **everything** currently on the drive, and then running the installer.

---

### Post by hammodi2 on 2013-10-21
i recommend you to disconnect it from the internet. dont install updates yet. also. dont check any boxes during the next a cpl of steps.

---

### Post by Paul_Stehle on 2013-10-21
sudo gparted results in: :unable to open /dev/sr0 read-write (read-only file system).  /dev/sr0 has been opened read-only.  says that twice, then "Can't have a partition outside the disk!"

---

### Post by Paul_Stehle on 2013-10-21
sudo gparted results in: :unable to open /dev/sr0 read-write (read-only file system).  /dev/sr0 has been opened read-only.  says that twice, then "Can't have a partition outside the disk!"

---

### Post by broadcast23 on 2013-10-21
sr/0 is the cdrom drive check the cable connection to you hard drive, or maybe it has failed

---

### Post by Mstersarg61 on 2013-10-21
Just wondering, can you get to the BIOS and see if the drive is recognized?

---

