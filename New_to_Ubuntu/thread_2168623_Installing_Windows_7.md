---
title: "Installing Windows 7"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by geronl on 2013-08-18
I have Ubuntu Linux and I want to install Windows 7. I thought the Windows installation disc would reformat the HDD for me but it did not and so I could not install WIndows 7.

---

### Post by ahmad3 on 2013-08-18
did u make it in install windows?

---

### Post by geronl on 2013-08-18
It said the HDD was not formatted and it had no option to format it.

---

### Post by ahmad3 on 2013-08-18
to install windows you need to go to tools in the start befoe going to install stuff you should see tools in the bottom corner i dont know what corner but its one of the bottom ones choose disk managment or something like that and boom format stuff

---

### Post by uRock on 2013-08-18
You will need to create and use an Ubuntu CD or USB and use GParted to create an NTFS partition. The Windows 7 installer is unable to see the Linux partitions. GParted is pretty simple to use and is listed under System tools on the live CD/USB, though it may be labeled "Partition Editor".

You will need to reinstall the grub boot loader after installing Windows in order to access ubuntu. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ahmad3 on 2013-08-18
wow totally forgot it was ubuntu's CD that had that feature sorry about that

---

### Post by geronl on 2013-08-18
I can't use GParted while running Ubuntu from the harddrive?

---

### Post by sandyd on 2013-08-18
> **geronl said:**
> I can't use GParted while running Ubuntu from the harddrive?

Gparted does not edit partitions that are mounted (i.e. root partition, home partition). By running from a livecd, those partitions are not in use, and can be edited

---

### Post by geronl on 2013-08-18
OK, I did it anyway. Can it reformat the main partition to use NTFS?  It seems like it can. Do I simply overwrite the partition using Linux and use that for Windows 7? I did already add a gigabyte to the second partition, I guess I can reinstall Ubuntu on that later, right?

---

### Post by geronl on 2013-08-18
Let me clearer, I am running Knoppix off the disc. I added some space to the second partition, which should be enough. I guess I could add more since I am going to wipe the first one anyway. So, then I can reformat the linux boot drive partition and install Windows 7?   Okay, so how would I get to load the Linux partition later? Use F8?

---

### Post by geronl on 2013-08-18
LOL.

I booted up a Knoppix disc and used GParted to partition the HDD, or actually to increase the space of the other partition (Linux Swap or something) to 30GB which is about what I am using, this would leave around 199 GB for the Windows. Then I told GParted to reformat the boot drive or whatever its called to NTFS. It turned light blue. I thought I had done it, I was finished and then the Windows 7 installation disc started asking me for drivers. huh?? Should it be doing that?

Apparently I didn't see the "little" button that tells GParted to actually do what I just told it to do. I thought it just did it.

Does this make me G-Tarded??

I guess I could call it a dry run. But should the Windows disc be asking me for drivers? Aren't they supposed to be ***on*** the installation disk??

---

### Post by Mark Phelps on 2013-08-19
Unless you have a rare disk controller situation (RAID or specialized controller), the Win7 install DVD should include all the disk controllers needed.

It's standard for the installer to OFFER you the chance to install drivers, but it should not be hanging on that.

Does it say which drivers it wants?

---

