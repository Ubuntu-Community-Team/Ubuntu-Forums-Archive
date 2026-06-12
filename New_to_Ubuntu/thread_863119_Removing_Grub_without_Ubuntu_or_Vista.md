---
title: "Removing Grub without Ubuntu or Vista"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by zzytds on 2008-07-18
Hi!
My problem is about Grub. Last night, I've removed the partition which contains Ubuntu and extended my Vista partition, so that after restarting my computer an error occured about Grub. Now how can i remove Grub? Can i do it with a Ubuntu CD.
Note: My computer doesn't boot.

---

### Post by Canis familiaris on 2008-07-18
The easiest but the most expensive (expensive in the sense that you have to burn a blank CD, duh!), you can burn a Super GRUB Disk (search for it in Google ;) )

However you could also use Windows 98 and Windows XP installer CD
Get Windows 98 boot disk and in the DOS environment: FDISK /MBR
In WinXP installer CD: Go to recovery console and type command: FIXBOOT

---

### Post by philinux on 2008-07-18
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Or use your windows disk.

---

### Post by steve-shinn on 2008-07-18
Or try sirrrell's method in this link :-

[http://neosmart.net/forums/showthread.php?t=931](http://neosmart.net/forums/showthread.php?t=931)

Assuming of course that you have the Visat CD

---

### Post by coffeecat on 2008-07-18
> **Anurag_panda said:**
> You can also use Ubuntu installation CD too:

In the live environment.
Open a terminal window or switch to a tty (Crtl+Alt+F1).
Type &#8220;grub&#8221;
Type &#8220;root (hd0,6)&#8221;, or whatever your Hard Disk + boot partition numbers are.
Type &#8220;setup (hd0)&#8221;, ot whatever your harddisk nr is.
Quit grub by typing &#8220;quit&#8221;.
Reboot.

Excellent instructions for repairing grub, but - ahem - he's removed his Ubuntu partition. This will not work for him.

> **Anurag_panda said:**
> However you could also use Windows 98 and Windows XP installer CD
Get Windows 98 boot disk and in the DOS environment: FDISK /MBR
In WinXP installer CD: Go to recovery console and type command: FIXBOOT

I'm sure you're right about FIXBOOT, but with the Windows XP disc isn't it usual to reinstall the mbr with FIXMBR?

**zzytds**, the problem is that the mbr (master boot record) was overwritten by stage 1 of Grub, which is fine when you are booting into Linux or multi-booting, but no good if you have a Windows single-boot. You need to reinstall the Windows mbr. Most ( :wink: ) of Anurag_panda's suggestions are good, but if by chance they don't work or you haven't access to a Windows install disc, search the forum or google for 'repair Vista bootloader, 'reinstall Vista mbr' or some such.

Good luck.

---

### Post by NewDisciple on 2008-07-18
Here's an easy method I just recently used on the wife's computer.  This is from: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

How to fix your Windows MBR with an Ubuntu liveCD

Something happen to a windows Master Boot Record (MBR) that you’re responsible for? Want a very quick, very easy way to restore it with nothing but your craft, native intelligence and a liveCD?

Be cautious here - you’re working with your disks in a very direct manner.  If you don’t have everything backed up or are unsure of anything, you may want to wait until you have a standard Windows CD/DVD.

Boot into your Ubuntu LiveCD on the offending machine. Once Ubuntu starts up, go to System -> Administration -> Software Sources and enable (by checking it off) the Universal repository.

Now, open a terminal session (Applications -> Accessories -> Terminal) and type the following:

    sudo apt-get install ms-sys

ms-sys is a program used to write Microsoft compatible boot records.

Now you’ll need to figure out what partition is the one hosting your Windows operating system. Back in the command line, type:

    sudo fdisk -l

That will list the available partitions. You’re looking for a partition that says something like

    /dev/sda1 1 9327 74919096 83 NTFS

The two important bits are the ‘/dev/sda1‘ which is the partition itself and the ‘NTFS‘ which tells us it’s a Windows formatted partition.  So your Windows partition exists on your drive sda and it’s partition 1. The MBR for drive sda (assuming you boot into windows using it’s native boot loader) is what you want to repair.

We want to fix the MBR on /dev/sda. To do so, type:

    sudo ms-sys -m /dev/sda

You’ll want to change the ’sda’ bit if your results from ‘fdisk -l‘ are different.  If for instance your windows install is on sdb or hda.

Once you do that, reboot the machine, removing the LiveCD from the drive and Windows should come back to you.

Sure, you could do this by inserting the correct Windows CD and booting into repair mode from it - but I find the Ubuntu way a bit faster and I’m more likely to have an Ubuntu LiveCD on me than a Windows CD.

Ms-sys is not in the current repo's as it is not compatible with the current linux kernel.  Therefore, hopefully, you have an older live cd laying around.  If not, try to download an older version on another computer and burn that to a cd and follow the previously mentioned steps.

I had messed around with numerous rescue cd's that were not easy to understand or follow.  This tutorial works and it's easy.

Good luck!

---

