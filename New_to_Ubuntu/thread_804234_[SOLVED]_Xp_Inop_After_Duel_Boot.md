---
title: "[SOLVED] Xp Inop After Duel Boot"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by lincoln32 on 2008-05-22
Do I Need To Reformat Then Load Win Xp Then Ubuntu Again Or Is There A Short Cut?

---

### Post by Efros on 2008-05-22
You need to give us a little bit more detail, before we can comment.

---

### Post by lincoln32 on 2008-05-23
ibm r40 had working xp pro and I defraged then ran gparted and split c drive
 45% ntfs 65% unused installed to largest unused and setup ubuntu hardy
with no faults but xp will not start and safe mode will not start. any shortcut to reinstall xp or do I have to format drive and start over?

---

### Post by amaroKer on 2008-05-23
Show us your partition table from GNOME Partition Editor.  If you don't have it, you can install it through **Applications** > **Add/Remove...**

The Print Screen button will take a cute screenshot.

---

### Post by bumanie on 2008-05-23
Post output of > sudo fdisk -l This can be done from within ubuntu or from the live cd.

---

### Post by Living2007 on 2008-05-23
> **lincoln32 said:**
> ibm r40 had working xp pro and I defraged then ran gparted and split c drive
 45% ntfs 65% unused installed to largest unused and setup ubuntu hardy
with no faults but xp will not start and safe mode will not start. any shortcut to reinstall xp or do I have to format drive and start over?
Maybe their is something else behind this all.
Does a Dual Boot Menu (GRUB) show when you start-up the computer?

---

### Post by lincoln32 on 2008-05-23
grub is fine Xp screen starts then blue screen fast then powers down and reboots
th blue screen is not up long enough to read faults and I left at least 14 gig in xp partion over the 14 gig used and had defraged before UBUNTU install:(

---

### Post by bumanie on 2008-05-23
Easier than a reinstall of xp would be to go into console mode and type FIXBOOT, then FIXMBR and see if that gets xp working. If it does you will have to reinstall grub via the live cd, but if you reinstall xp, you will have to do this anyway. If fixboot, fixmbr works, it will save you a lot of time. Just a thought.

---

### Post by s8kid on 2008-05-23
I am having a similar problem. My main issue is with grub though. Grub will not respond to anything that i type. It gives me three seconds to click escape to start grub instead of running straight to Ubuntu, that is when any input becomes temporarily unresponsive. Ubuntu loads up and works fine, but i cannot access xp. 
I have two hard drives and think i may have found part of the problem. The first HD is an 80 and is split 60(XP) 20(split), and a 500 split 350(Ubuntu) 150(unused). I need to access windows and don't know what to do now.

---

### Post by lincoln32 on 2008-05-23
second test found recovery panel inop and ubuntu unable to read win partition and the two linux command line above do nothing gparted shows correct size andformats so I tryed to format win install failed no readable partion found now trying to format win drive in gparted

---

### Post by Living2007 on 2008-05-25
> **lincoln32 said:**
> grub is fine Xp screen starts then blue screen fast then powers down and reboots
th blue screen is not up long enough to read faults and I left at least 14 gig in xp partion over the 14 gig used and had defraged before UBUNTU install:(
My anut had a similar problem, when she booted, the BSOD (blue screen of death) poped up and it then rebooted,

Obviously, Windows has a virus and Windows needs to be re-installed

---

### Post by lincoln32 on 2008-05-26
thanks i dowd loaded a test dish for the hard drive and found bad sectors
repaired and reloaded ok at this time thanks

---

### Post by Efros on 2008-05-27
I would keep a close watch on that HD and make sure you have a backup of any data on it.

---

