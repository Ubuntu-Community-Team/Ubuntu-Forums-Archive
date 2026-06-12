---
title: "Installing Windows on slave drive"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by xeroguitar on 2008-11-06
Hi, 

I currently run the best OS (ubuntu 8.04) on my main drive but unfortunately, due to microsoft's (pardon my french) monopoly on everything, there are some things i need to do that require windows to run. So I thought I could get away with putting a second hard drive in my computer and installing windows on there... apparently not.

I tried Vista first and got an error (Windows is unable to find a system volume that meets it's criteria for installation) even thought through Vista's CD I formatted the hard drive to NTFS and everything. So I threw in an XP install disc.

With XP I get a message saying it needs to install startup files on my linux drive in order to install windows on my new drive and it wants me to create a partition on the linux drive for windows? is it just me or does that seem like a waste? is there any way around this? I don't need it to load any startup files... if i want to use windows ill go into bios and boot into the slave drive as i wont be using it much.

if not is it safe to partition the linux drive or will it erase some of my data? how big should i make the partition if its only a couple files?

i appreciate any ones advice!

---

### Post by H.Callahan on 2008-11-06
IIRC, Windows needs to be installed on the first bootable drive in the system.  It can not be installed on a secondary drive.

(Someone please correct me if I don't recall correctly)

---

### Post by ronnielsen1 on 2008-11-06
It can be installed on a secondary drive but you have to make it believe it's on the first drive by mapping it



> root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by alienexplorers on 2008-11-06
That is correct.  Windows does not like being on a slave drive.  It wants to be on the master drive.

---

### Post by ronnielsen1 on 2008-11-06
> With XP I get a message saying it needs to install startup files on my linux drive in order to install windows on my new drive and it wants me to create a partition on the linux drive for windows? is it just me or does that seem like a waste? is there any way around this? I don't need it to load any startup files... if i want to use windows ill go into bios and boot into the slave drive as i wont be using it much.

You could put the slave drive in as the only hard drive, install xp and then turn it back into a slave drive and add your ubuntu hard drive and reinstall grub but pay attention to my first post.

---

### Post by johntravis on 2008-11-06
I have ubuntu 8.0.4 on 1 hdd and xp (sp3) on another hdd, both hdd's installed,w/power,I choose which hdd boots by switching sata cable from xp to ubuntu or visa-versa, of course you will have to remove side cover to switch cables.

---

### Post by ronnielsen1 on 2008-11-06
> That is correct.  Windows does not like being on a slave drive.  It wants to be on the master drive.     If you google this, you might find that's not the case
[http://www.linuxforums.org/forum/installation/132079-installing-windows-2000-slave-drive.html](http://www.linuxforums.org/forum/installation/132079-installing-windows-2000-slave-drive.html)

You can also use Vista but you need EasyBCD to edit the Vista bootloader

---

### Post by caljohnsmith on 2008-11-06
> **alienexplorers said:**
> That is correct.  Windows does not like being on a slave drive.  It wants to be on the master drive.
If you have a primary NTFS or FAT partition on the master drive, I believe you can install Windows to the slave drive; Windows will just put its boot files on NTFS/FAT partition on the primary drive. Afterwards, you can then manually move Windows boot files back to the slave drive, reconfigure boot.ini if it is XP, or reconfigure BCD if it is Vista, and then you can boot Windows directly from the slave drive with Grub.

Or if you can, I agree with ronnielsen1's advice: just disconnect the master drive, set the slave drive as master, install, then switch it all back.

---

### Post by toucher5 on 2008-11-06
Another thing you could do if you don't want to go through this hassle is to use a program like Virtualbox or VMware Server inside of Ubuntu.

---

### Post by xeroguitar on 2009-03-20
hey, i know this is really late but i did take your advice and it worked great! got vista installed on the second hard drive then mapped it out. The only problem I've noticed is the clock in windows always seems to be 5 hours off no matter how many times i change it but i dont use windows enough to care.

so i know its late but thanks anyways!

---

### Post by cholericfun on 2009-03-20
The clock issue is something about Windows using Local time and Linux using UCT.
on the other hand i strongly second the VMware idea posted earlier (although VirtualBox is not without its problems). 
might be worth playing around with in case the BIOS settings get annoying
plus you get to have 2 OSs running at once...

---

