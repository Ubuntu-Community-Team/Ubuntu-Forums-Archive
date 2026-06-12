---
title: "Sharing Files between Windows 7 and Ubuntu"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Lithinous on 2011-11-04
A few days ago I clean installed Ubuntu on to my 1TB hard drive. Earlier today, I installed Windows 7 on to my small SSD. However, I would like a part of the Hard Drive to be shared and one part for the programs in Windows(and the other for Ubuntu programs).

Any help would be greatly appreciated.

---

### Post by Lithinous on 2011-11-04
bump??

---

### Post by fdrake on 2011-11-04
create a new partition in FAT or NTFS format, and it will be available for read/write permissions by both systems. you can use gparted (or a windows program)to create the partition and mount it automatically in Ubuntu editing your Fstab. Windows should be able to read write since is a native File system.

---

### Post by HereInOz on 2011-11-04
You need to install samba on your Ubuntu machine.  Have a look in the Software Centre and install the Samba server.  The client should already be installed.

Then install system-config-samba.  This will give you a GUI configuration utility to set up the shares.  

Don't forget to open the SMB ports in your firewall on the Ubuntu machine, if you are running a firewall. 

There are heaps of how-to's on this around the web.  Most of them talk you through the editing of the configuration file, but I find the system-config-samba utility is quick and easy.

By the way, it is not good form to bump after 15 minutes.

---

### Post by Ricx94 on 2011-11-04
I think you should be able to use a program such as g-parted partition manager to resize your ubuntu partition on the 1tb drive, leaving empty space on the drive, not partitioned. go into windows, right-click on Computer, click Manage, then click Disk Management on the left of that window. locate the 1tb drive on the bottom, and select the not-partitioned part of it. right-click and partition and format it as NTFS, and give it a letter for windows to be able to see it normally. that part should then be visble to both OS's, and be able to be used by both.

---

