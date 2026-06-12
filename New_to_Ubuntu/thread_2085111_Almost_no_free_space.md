---
title: "Almost no free space"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by Barbarozza on 2012-11-17
Hi guys!

I am a former windows user, and linux is brand new to me. I recently installed Ubuntu on my laptop, alongside Windows (Dual boot, with Windows and Ubuntu on separate drives, and yes, it is a wubi install)

Anyways, I am having some trouble with the amount of space I am allowed to use. It is a wubi install, and I think I chose the 15 Gb options when I installed it. Nevertheless I am now having very little free space where my /home folder is located, and all the space is located in some "folder" named /host...

So, my question is if there is any way to move the space from /host to /home, or in anyway make the space in /host usable.

Some help is much appreciated:)

Here's what comes up when I type df -h:

Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      9.3G  8.8G  515M  95% /
udev            3.7G  4.0K  3.7G   1% /dev
tmpfs           1.5G  904K  1.5G   1% /run
none            5.0M   24K  5.0M   1% /run/lock
none            3.7G  392K  3.7G   1% /run/shm
/dev/sda1        15G  9.9G  5.1G  67% /host
/dev/sdb2       447G   86G  362G  20% /media/Windows7_OS_
/dev/sdb1       1.5G  363M  1.2G  25% /media/SYSTEM_DRV

---

### Post by Mark Phelps on 2012-11-17
Basically -- no.

The /host folder is where your Windows filesystem is mounted automatically in a Wubi install.

You said you have separate "drives" -- but that is the term that MS uses for "partitions" -- which are allocated spaces on the SAME physical drive.

Either way, you can't migrate space from Windows to Ubuntu or vice-versa.

If you look in the Wubi guide (linked below), there is a way to increase the size of the virtual space allocated to Ubuntu -- if there is actual free space on the drive:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by Bartender on 2012-11-17
If it's a wubi install, it's not dual-boot.  "Dual-boot" means that the PC is capable of booting into two different OS'es.  Yours boots into Windows.

If you're not thrilled about getting rid of the wubi install and trying to preform a true dual-boot (or perhaps virtualization?) I don't think there are too many non-geeky options other than getting yourself an external drive and keeping the data in your wubi /home carved down to the minimum.

---

### Post by newb85 on 2012-11-17
Indeed.  Wubi is basically a Virtual Machine designed to run Ubuntu.  It can be fairly seamless and feel like a dual-boot setup because it bypasses the Windows GUI environment, but it still runs on Windows, and it is still installed within your Windows partition.

Edit: I haven't tried it myself, but apparently there's a method for migrating a Wubi install onto its own partition so that you do have a true dual-boot setup.

[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Definitely read the entire page before diving in.  Definitely back up your important files before diving in.  And, it's probably wise to wait for someone who's used that method to chime in with advice from experience.

---

### Post by Paqman on 2012-11-17
> **Bartender said:**
> If it's a wubi install, it's not dual-boot.  "Dual-boot" means that the PC is capable of booting into two different OS'es.  Yours boots into Windows.


> **newb85 said:**
> Indeed.  Wubi is basically a Virtual Machine designed to run Ubuntu.  It can be fairly seamless and feel like a dual-boot setup because it bypasses the Windows GUI environment, but it still runs on Windows, and it is still installed within your Windows partition.


Neither of these is correct. Wubi is a type of dual-boot. When it boots it briefly uses the Windows bootloader, but after that no parts of Windows are running. It boots into and runs Ubuntu just like a traditional install, it's just done from a loopmounted virtual partition instead of a proper partition.

Wubi is not a virtual machine or an emulator, or anything like that.

Barbarozza, there is a guide about Wubi [here]("https://wiki.ubuntu.com/WubiGuide"). It's theoretically possible to expand a Wubi system, but it may be a better solution long-term to reinstall to a proper partition (ie: not using Wubi) that you assign plenty of space to.

---

### Post by Barbarozza on 2012-11-17
Thanks for the replies guys! I really appreciate it, and I will definitely take a closer look at the wubi guide.

I think Paqman is correct though, as I am able to boot into two different OS'. 

When I said that I have installed Ubuntu on a different drive, is was because I installed Ubuntu on a 16 Gig SSD, while Windows is installed on my 450 Gig HDD.

All I want is to designate the whole 16 gig of my SSD to Ubuntu, and this can't possibly be so difficult!

---

### Post by newb85 on 2012-11-17
Wubi *does* differ from a VM in that the hardware is not emulated.  However, in addition to using the Windows bootloader, Wubi also uses Windows to emulate the filesystem, which is kind of a big deal.

---

### Post by Paqman on 2012-11-17
> **newb85 said:**
> Wubi also uses Windows to emulate the filesystem, which is kind of a big deal.

It resides on a partition which has a Windows filesystem, but that doesn't require any part of Windows to be running. Linux can read and write to NTFS, and the filesystem inside the virtual partition is a normal Linux EXT one.

---

### Post by newb85 on 2012-11-17
Sorry.  Bit off more than I can chew.  I clearly don't have the technical knowledge to participate in a discussion on Wubi.

I will concede that my initial statement that Wubi is "basically a VM" was incorrect and withdraw from this thread.

---

### Post by Bartender on 2012-11-18
> **Barbarozza said:**
> When I said that I have installed Ubuntu on a different drive, is was because I installed Ubuntu on a 16 Gig SSD, while Windows is installed on my 450 Gig HDD.

All I want is to designate the whole 16 gig of my SSD to Ubuntu, and this can't possibly be so difficult!

OK, I'll admit that I don't know much about wubi.  But now I'm really mixed up.  Ubuntu is on a tiny SSD, and Windows is on a big HDD, and this is a wubi setup?  I didn't know such a thing was possible.

16GB for an entire Linux install is pretty cramped.  I'm at 5.2GB on a brand new Ubuntu 12.04 install which is only a coupla of days ago.  Have added GIMP and ubuntu restricted-extras, and that's about it.

Unless I'm missing something here, why not do a "traditional" dual-boot?  You've got 2 drives.  

Seems to me that the thing to do is completely wipe wubi from the Windows drive.  So it's back the way it was before.  Then create a bootable Ubuntu install CD and install Ubuntu to the 16GB SSD.  Tell it to wipe the drive, then install.  

Several years ago you had to point GRUB in the right direction so that Windows and Linux would dual-boot.  Lately, the installer doesn't even ask about where to put GRUB.  When I dual-booted a couple of days ago it figured out on its own that there was a Windows partition and set things up correctly.  But that was with one drive, not two, so you might want to ask about that.  I *think* the installer would know what to do with a two-drive setup but not sure.  I dual-booted to 2 drives years ago and it was easy.  GRUB is certainly capable, I just don't know if there's any operator input required nowadays.  

You said you'd set aside 15Gb for the wubi install, so I don't know how you're gaining much by going to a 16 GB SSD.  Wait a minute.  With a "genuine" dual boot, you'd be able to mount the ntfs partition (Windows) and move data there.  What would be sweet is to create a partition on the Windows drive that's separate from the Windows OS itself (C: Drive) so that you're reducing the chances of dropping a bunch of pictures by accident into a Windows system32 folder...

Can you install gparted to your wubi and take a screenshot of each drive?  That would be interesting to see.

EDIT: A traditional dual-boot means GRUB gets in there and tweaks the Windows MBR.  That means the two OS'es are wedded at the hip, so to speak.  If you remove Ubuntu down the road, you'll have to repair the Windows MBR.  There's another way.

Does your PC have a "quick boot" function?  You know, you jab a button as the PC is booting up and you get a window that asks where you want to boot from.  If you do, and *if it recognizes both drives*, another option would be to install Ubuntu to the 16GB SSD with the Windows HDD unplugged so the installer doesn't see it.  You end up with Windows, untouched by the Ubuntu install, on one drive.  Ubuntu is installed to the other drive.  Neither OS has messed with the other.  Then you use the "quick boot" function to choose whether you want to boot Windows or Ubuntu.

I emphasized "if it recognizes both drives" because I recently came across a corporate HP that had a weird BIOS.  With two drives plugged in, "quick boot" ignored the second drive no matter where I put it on the SATA ports.  I'm assuming that's rare.

---

