---
title: "Dual Booting with Windows 7 and Ubuntu. 4 Primary Partitions max?"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by ClarkH85 on 2013-05-10
This is my first go at creating a dual boot. I want to make sure I do everything right.

I just got a new laptop with Windows 7. There are currently 2 ***primary*** partitions - the standard OS on C: and a much smaller "Recovery" partition. I've read that I cannot exceed four primary partitions per disk. What I'd like to do next is install Ubuntu on a small partition (this will include /home), create a small swap partition, and then have a large NTFS partition for data to be accessed by either Ubuntu or Windows. But, will this exceed the number of primary partitions allowed? 

When I create a swap partition while installing Ubuntu from my USB stick, will that swap partition be a ***primary*** partition? Can I create it as a logical partition? What's the difference?

Will the large NTFS storage partition be a primary partition? Could I create *this one* as a logical partition?

Which would you advise I create as a logical partition? That is, if that's the solution you suggest. And, how would I do that? With GParted?

Should I create the NTFS storage partition using GParted after installing Ubuntu? Currently what I have 650GB unallocated. I'm planning to install Ubuntu next, before creating additional partitions.

Thank you!

---

### Post by ClarkH85 on 2013-05-10
Actually, from some screenshots of installation process for Ubuntu 12.10, I can see that there is an option to set up the swap partition as either logical or primary, but what's the difference?

Also, I would still appreciate feedback about how I should set up my NTFS storage partition.

Thank you!

---

### Post by Mark Phelps on 2013-05-10
The way partitioning is generally done is to create a single Extended partition (which is a Primary) and, inside that, create two partitions, one for the Ubuntu filesystem and the other for swap.  That will give you three partitions for Windows (boot, OS, data) and one Extended that contains the Linux partitions.

Please read through the materials below BEFORE you launch into partitioning:

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by fantab on 2013-05-10
> **ClarkH85 said:**
> Actually, from some screenshots of installation process for Ubuntu 12.10, I can see that there is an option to set up the swap partition as either logical or primary, but what's the difference?

Also, I would still appreciate feedback about how I should set up my NTFS storage partition.

Use ONLY Windows Disk management tool/utility to Resize your NTFS partition so that you have at least 40GB free space to install Ubuntu and for SWAP. If you plan to create another NTFS partition then free up more space. Create NTFS partition with Windows only. Leave the space for Ubuntu as 'unallocated" don't create any more partitions with Windows.

Note this, Windows MUST have atleast 25%-30% of Free Space in its C: partition after everthing is installed for optimal performance, otherwise it will slow down.

To Bypass the 4 primary partition limit we use EXTENDED partition (which is a primary partition) which serves as a container for several LOGICAL Partitions. So Make your FOURTH Partition as EXTENDED with GParted (present on Ubuntu install Disk) after booting with Ubuntu LiveDVD/USB. Choose "SOMETHING ELSE" during Ubuntu install and guide your install.

Good Luck....

---

### Post by oldfred on 2013-05-10
Are you sure you just have two partitions? Windows 7 usually has a (hidden) 100MB boot/repair partition and vendors add a 4th for vendor tools.

You can have all of Linux and NTFS data partitions in the extended partition as logical partitions. Only Windows requires that you use a primary partition to boot from.
I usually make all of the unallocated the extended partition so I can add many logical partitions. I then put swap at the end just so it is out of the way. 

Difference between versions of installer is minor.
 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by cmcanulty on 2013-05-10
I used easus partition free and was able to do a lot more than the built in windows partitioner with no issues at all

---

