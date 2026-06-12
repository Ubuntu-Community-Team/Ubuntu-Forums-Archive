---
title: "Moving Wubi - Can't Partition Windows 7"
date: 2011-11-10
forum: New to Ubuntu
---

### Post by Gutuater on 2011-11-10
Hi,

I just bought a brand-new laptop (Win7) without CD/DVD, first thing I did was to install Ubuntu from a USB stick but something went wrong there: I think it failed to copy some files into the ISO - anyway, when I restarted the computer, nothing happened and I could not even open the USB. After installing Ubuntu with Wubi, Ubuntu didn't even recognize the external drive, which I found very strange. I had to format it with a Mac because both Win7 and Ubuntu refused to do it.

So eventually I installed Ubuntu via Wubi, and now I want to move it to a real partition. The problem is that I am not allowed to resize the original partitions. My hard disk looks like this now (see attached screenshot).

For some reason, I am not allowed to touch either the sda3 partition, nor the unallocated one.
And actually I don't understand how this works, since my hard disk officially has 500GB, but the sum of the existing partitions is already over 650. Is the hard disk bigger than I thought or is sda2 somehow "within" sda3? :confused:

My question is: should I resize the "System Reserved" one, if no other option is available? It seems to be the only partition that I am allowed to modify, and I read in some forum that it's possible, in theory, but I am not sure about the consequences for WIndows. I don't want to get rid of WIN7 and I don't have an installation CD of it. It would be great if somebody could suggest me a solution that doesn't involve burning CD/DVDs, since my laptop doesn't support it. 

Looking forward to reading your comments!

---

### Post by mcduck on 2011-11-10
The thing here is that since you are running a Wubi install, your Ubuntu isn't actually located on a partition, it's instead installed into a file inside the Windows filesystem. So you can't edit the partition layout like you would with real partitions.

What comes to disc sizes, the 500GB hard drive shows in your partition manager layout as the 450GiB (notice the difference between GB and GiB;)) /host and the Linux "partition" is actually *inside* that one.

Your hard drive probably actually has only one partition, the one used by Windows. Ubuntu won't be able see the real partition layout, though, and either way you should always resize Windows 7 partitions from Windows itself.

So you should use the Windows 7's own tool to shrink it's partition and to make room for Ubuntu's partitions, and then follow the instructions from here: [http://ubuntuforums.org/showthread.php?t=1519354]("http://ubuntuforums.org/showthread.php?t=1519354")

---

### Post by PPN13 on 2011-11-10
sda3 is your main Windows7 partition. Wubi's partition is a file in that partition so it's in use by ubuntu and you can't mesh with it. Messing with it without care can also destroy your Win installation. 

sda2 is also a Win partition for some system files, if you touch this as well it could cause problem with win7 boot and by extension wubi.

The unallocated space is just 1 MiB which is tiny and I believe that's the reason you can't do anything with it. 

You should resize the windows partition via its own tools thus increasing unallocated space. 

You could then create an extended partition to contain as many partitions as you need for your ubuntu install (root , home , swap)

---

### Post by Mark Phelps on 2011-11-10
If you want to end up with a real dual-boot, then do the following:

1) Remove the Ubuntu install done via Wubi.  Unless you have done a LOT of customization, it's going to be more work to "move" it than to simply remove it and reinstall.

2) Use the Win7 Disk Management utility to shrink the Win7 OS partition.  Reboot into Win7 a couple of times after that to let it make any filesystem adjustments.

3) Then, use the Ubuntu installer to select the unallocated space.  You will have to do manual formatting as, AFAIK, the installer no longer offers the "Use largest free space" option.  Be very careful NOT to select your Win7 partition, otherwise, you will erase it and not be able to recover it.

A good step to perform ahead of time is to make a backup of your "shrunk" Win7 install to an external drive.  You can download and install the FREE version of Macrium Reflect to do this.  That way, if you do accidentally erase Win7, you can restore it from your backup.

---

### Post by azkraja on 2011-11-10
I think it will not work, because i faced same problem and some of the expert in your forum explain me that windows 7 uses Dynamic volume partitions which can be shrunk or extended by Windows built in Disk management system but Ubuntu Disk utility or GParted can not do this except one should not convert this disk to basic volume and it should be done only to during re-installing windows. Although some softwares available to do this job ,but it is risky to loose data, so be careful. you can google to get information about the difference of Dynamic, basic and logical disks.

please read this thread.

[http://ubuntuforums.org/showthread.php?t=1874102&highlight=partition+problem]("http://ubuntuforums.org/showthread.php?t=1874102&highlight=partition+problem&page=2")

---

### Post by Mark Phelps on 2011-11-10
While I agree that MS Windows use of Dynamic Disks creates problems for Linux users, there's no indication in your screenshot that these are Dynamic Disks.

---

