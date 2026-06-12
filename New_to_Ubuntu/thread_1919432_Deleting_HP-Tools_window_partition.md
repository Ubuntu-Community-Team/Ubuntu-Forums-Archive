---
title: "Deleting HP-Tools window partition?"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by McTwitch on 2012-02-02
I'm doing an install on a friend's computer for Ubuntu 11.04. I was going to partition their drive so that they have their Windows 7 stuff, and then have an extended partition for Ubuntu. However, there are too many partitions already on the drive, or at least that's the error message that GParted tells me. The only partition that I can see that might not be important, is a little one called HP Tools. So, I was wondering if it would be all right if I just deleted that, and went on with the installation.

---

### Post by lisati on 2012-02-02
I've come across a similarly named partition on a Compaq laptop, and considered deleting it to free up a partition or two for use by Ubuntu. AFAIK it's probably OK. Just remember to make sure that your friend has made a set of recovery disks for the machine, just in case things go wrong and you need to put things back how they were.

---

### Post by Kixtosh on 2012-02-02
> **McTwitch said:**
> I'm doing an install on a friend's computer for Ubuntu 11.04. I was going to partition their drive so that they have their Windows 7 stuff, and then have an extended partition for Ubuntu. However, there are too many partitions already on the drive, or at least that's the error message that GParted tells me. The only partition that I can see that might not be important, is a little one called HP Tools. So, I was wondering if it would be all right if I just deleted that, and went on with the installation.That may be something to do with the way HP allows for restoring the computer to "out of the box" state. My Toshiba laptop shipped with three partitions:

[LIST]
[*]1.6 GB Toshiba System partition.
[*]6.5 GB HDD Recovery partition.
[*]Windows Partition.
[/LIST]
The recovery menus are Toshiba menus, and allow access to recovery options for Windows, which may explain the use of two "recovery" related partitions. 

I was able shrink the main Windows O.S. partition to add an extended partition that is a container for a Swap logical partition and an Ubuntu O.S. logical partition. You may be facing a similar setup and you may have simply exceeded the number of primary partitions allowed. You could use a LiveCD to access the Disk Utility from the Administration tools, and check what partitions are present. You could then post a screenshot of that.

---

### Post by McTwitch on 2012-02-05
> Just remember to make sure that your friend has made a set of recovery disks for the machine, just in case things go wrong and you need to put things back how they were

This is something I've thought of. How would I go about making these for them?

---

### Post by Jerry N on 2012-02-05
On my HP Mini 210 I:
1. Saved the folder in the HP-Tools partition
2. Used the Win 7 tools to delete the HP-Tools partition
3. Used the Win 7 tools to shrink the C: drive and create unallocated space (DO NOT use the Win 7 tools to create a new partition)
4. Used gparted to create an extended partition in the newly unallocated space and created an EXT 4 logical partition, a Linux Swap logical partition, and a 100mb Fat 32 logical partition.
5. Copied the folder saved from the HP-Tools partition to the new Fat32 logical partition.
6. Installed Ubuntu (in this case Linux Mint 9) in the EXT 4 logical partition.

As I mentioned in another earlier thread, if you have a wired ethernet connection, you will get a message about availability of drivers. Let Ubuntu install those drivers and you should be good to go with wireless. You shouldn't have to take any other action than letting Ubuntu do its thing. This did not turn my Mini 210 into a speed demon but it does give me an alternative.  I haven't compared battery charge life between Win 7 basic and Ubuntu.

Jerry

---

### Post by mcduck on 2012-02-05
> **McTwitch said:**
> I'm doing an install on a friend's computer for Ubuntu 11.04. I was going to partition their drive so that they have their Windows 7 stuff, and then have an extended partition for Ubuntu. However, there are too many partitions already on the drive, or at least that's the error message that GParted tells me. The only partition that I can see that might not be important, is a little one called HP Tools. So, I was wondering if it would be all right if I just deleted that, and went on with the installation.

THat depends on the machine, and if your friend considers the tools provided by that partition as useful or not.

(For example on my HP laptop the quickboot OS, and all the recovery and security tools provided by HP depend on that partition, so I decided that creating the recovery discs and removing the recovery partition instead would be a better idea)

---

### Post by Bartender on 2012-02-05
_Definitely_ make the recovery discs before deleting anything.  HP Support should have directions, but directions should be on the PC inside the HP stuff.

Some HP rigs don't have the recovery discs.  I bought an HP Probook 4520S.  You have to buy discs from HP.  No recovery disc creator on the laptop.  What a rip-off.

If your friend is willing, make the recovery discs, save their personal data to an external device, and run the recovery discs.  This will reinstall W7, and possibly get rid of some of the partitions.  On our Acer 5920 running the recovery discs got rid of 3 of the 4 partitions that came with it out of the box.

---

### Post by Mark Phelps on 2012-02-06
IF all your friend needs is a way to restore Win7 later, they can use an alternate approach that allows them to remove the recovery partition entirely:

Macrium Reflect (MR) provides a FREE version that can be used to image and restore partitions or entire drives.

To do this, download the FREE version from their website and install it in MS Windows.

Then, use the option to create and burn a Linux Boot CD.  This will provide you a means of booting and restoring MS Windows later.

Then, use MR to image off the Win7 OS partition (and if there is a boot partition, that as well) to an external drive.

NOW, you have the ability to restore Win7 to its current state, and unlike with the Recovery option, you won't have to reinstall any of your apps.

---

