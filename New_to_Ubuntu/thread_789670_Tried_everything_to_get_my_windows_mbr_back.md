---
title: "Tried everything to get my windows mbr back"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by hockeyfighter09 on 2008-05-10
Ive tried everything. Super Grub, Ubuntu Live CD everything.  But the simple solution doenst work for me.  That is using the windows xp and the fixmbr command.  I have a Dell xps 600 desktop and when I try to boot from the windows dvd it only boots from the cd drive not the dvd one.  So I cant figure out how to make the dvd boot so I can get into the disk and fix the mbr.  Any suggestions?

---

### Post by grannyw on 2008-05-10
Have you tried to change the boot configuration in bios?

---

### Post by hockeyfighter09 on 2008-05-10
I havent tried in fear I might screw up something royally.  But I have gone into the system setup option that appears on dells and it only gives me the option to choose the cdrom drive.

---

### Post by hockeyfighter09 on 2008-05-10
I am going to try to install ubuntu again just so I can get back into windows and then work from there. But please keep the suggestions coming.

---

### Post by ugm6hr on 2008-05-10
Have you tried this: [http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

### Post by noynac on 2008-05-10
> **hockeyfighter09 said:**
> I am going to try to install ubuntu again just so I can get back into windows and then work from there. But please keep the suggestions coming.

I used an old DOS disk and the fdisk /mbr command:

[http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013)

---

### Post by aussiedini on 2008-05-10
Boot off your windows disc, then R for recovery when it gives you optoins. The select the windows folder by typing the number next to the options. Then your admin password and you are in. Type FIXMBR, then Y to the question and reboot. This should reset your MBR to windows default.

---

### Post by kansasnoob on 2008-05-10
If Ausiedini's suggestion doesn't work (it should) the next thing I'd do is boot your Ubuntu Live CD (I suspect you have since you're in this spot) and access Gparted, AKA Partition Editor, to see what your drive looks like.

I spent several hours once trying to access a partition that I'd deleted by OOPS!

---

