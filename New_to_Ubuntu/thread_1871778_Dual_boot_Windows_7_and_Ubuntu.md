---
title: "Dual boot Windows 7 and Ubuntu ?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by Zyklon87 on 2011-10-29
Hi guys, this is my first post, and lets hope you can help me since this is official Ubuntu forum :)

I have installed as main OS Windows 7 Professional, I want to create new partition for Ubuntu 11.10, I tryed to create new partition from Win 7, shrink a new partiton and format it as NTFS, but when I try to install Ubuntu it wont show on list of partitions since Ubuntu works in ext3 format.
I have 320GB HDD as 2 partitions, C=100GB and D=300GB, I want to shrink from D 20GB for Ubuntu.
So tell me guys how to create new partition for Ubuntu and install it, without affecting Windows 7 !
Thanks in advance.

---

### Post by roger_1960 on 2011-10-29
Hi

Use the **windows partition tool** to shrink the d: partition.  I would give yourself a bit more than 20G as you have a lot!  Then use the Ubuntu installer on the live CD and install ubuntu alongside windows using the newly freed unpartitioned space.  Ubuntu will create and format the ext3/4 partition which will house ubuntu.  If you have already created a 20G ntfs empty partition, delete it before trying to install ubuntu.

As always, back up all your data to an external drive/cloud before you start the process. (In case of murphy being around)

---

### Post by oldfred on 2011-10-29
Do not create partitions with Windows. It will convert to dynamic or sfs which is compatible with noting including some Windows repair tools.

You need to have an extended partition which can hold many logical partitions. Windows has to install to a primary partition and it is best to install a second copy of windows to a primary partition, but you only can have 4 primaries with MBR(msdos) and one needs to be the extended.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Zyklon87 on 2011-10-29
> **oldfred said:**
> Do not create partitions with Windows. It will convert to dynamic or sfs which is compatible with noting including some Windows repair tools.

You need to have an extended partition which can hold many logical partitions. Windows has to install to a primary partition and it is best to install a second copy of windows to a primary partition, but you only can have 4 primaries with MBR(msdos) and one needs to be the extended.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

Im trying to dual boot in my laptop, I dont have any extended HDD, this is partitioned in 2 logical partitions, so can you tell me how to do this with step by step guide ?

---

### Post by roger_1960 on 2011-10-29
Hi again

We are not disagreeing with each other.  You should not create a partition with windows, if you have, delete it.

Do as I said before.  

Backup your data

Defragment windows (if not done recently)

Use **windows** (not ubuntu) to shrink the existing d: partition.

Reboot to the Ubuntu CD or USB

Install ubuntu "alongside" windows using the free space you have made by shrinking the windows partition.

If you are not sure, read this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) , but use windows to shrink the windows partition.

---

### Post by oldfred on 2011-10-29
+1 on roger_1960 suggestions.

The links posted give step by step instructions. And some show screenshots. If not exactly the same version screens may vary slightly but the install process is the same.

---

### Post by nogoodnamesleft on 2011-10-29
Is there any chance we can fix the thread title? I have Windows 8 running on metal and I got all excited when I saw the title.

And yes, I agree with the other guys. Follow the instructions given, and it will work.

---

### Post by Zyklon87 on 2011-10-30
> **roger_1960 said:**
> Hi again

We are not disagreeing with each other.  You should not create a partition with windows, if you have, delete it.

Do as I said before.  

Backup your data

Defragment windows (if not done recently)

Use **windows** (not ubuntu) to shrink the existing d: partition.

Reboot to the Ubuntu CD or USB

Install ubuntu "alongside" windows using the free space you have made by shrinking the windows partition.

If you are not sure, read this [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) , but use windows to shrink the windows partition.

I shrinked new partition using Win 7 Disk Management, here it is a screenshot.

[[IMG]http://img444.imageshack.us/img444/4392/ubuntuparion.th.png[/IMG]]("http://imageshack.us/photo/my-images/444/ubuntuparion.png/")

[U]
I burned ISO file and on partition list of Ubuntu setup, I cant figure it out which one is this partition that I created on Windows, here it is two screenshots.

[[IMG]http://img200.imageshack.us/img200/817/35783789.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/200/35783789.jpg/")


[[IMG]http://img97.imageshack.us/img97/3345/62210420.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/97/62210420.jpg/")

I selected in this last partition on list, I saw its 'unusuable' but the size it was ~ 20000MB but when I clicked 'Install Now' here what error appeared.

[[IMG]http://img35.imageshack.us/img35/3103/10524808.th.jpg[/IMG]]("http://imageshack.us/photo/my-images/35/10524808.jpg/")

Which one is the partitioned labeled 'Ubuntu' in Windows ?

@[/U]nogoodnamesleft
Hmm I didnt even noticed, I checked 2-3 times after saw your post, and I cant rename it, any rename this topic to 'Dual boot Windows 7 and Ubuntu' !

Help me out pls !

---

### Post by oldfred on 2011-10-30
You have 4 primary partitions and that is the maximum you can have. You have to delete one of the primary and convert it to the extended, which is still one of the 4 primary but then can hold logical partitions for your install of Ubuntu.

Partitions do not have to be in order and it looks like sda2 is 0 size? But sure to back up before deleting anything. Make sure you have a Windows repairCD. You also should have the vendor recovery DVDs also, if you have not made those.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Zyklon87 on 2011-10-30
> **oldfred said:**
> You have 4 primary partitions and that is the maximum you can have. You have to delete one of the primary and convert it to the extended, which is still one of the 4 primary but then can hold logical partitions for your install of Ubuntu.

Partitions do not have to be in order and it looks like sda2 is 0 size? But sure to back up before deleting anything. Make sure you have a Windows repairCD. You also should have the vendor recovery DVDs also, if you have not made those.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Can you tell me how to convert, and which one to delete, and what software do I need to convert partition to extended, Im newbie, be more specific please, otherwise If I would know how to do this I wouldnt be here asking ...
Here is a sreenshot of Disk Management from Windows 7 showing partitions.
[[IMG]http://img444.imageshack.us/img444/2492/winyg.th.png[/IMG]]("http://imageshack.us/photo/my-images/444/winyg.png/")

Ubuntu partition list |||      Windows partition list
sda |||                             ???
sda1|||                           OEM partition
sda2                           ||| ???
sda3 |||                           System Reserved
sda4|||                           Windows 7 (C)
unusable                     ||| wtf is this ???

Where's 'Ubuntu' partition that I created in Win 7 ?
Is there any chance that I can create partition and install without losing my data on (C) and (D), I dont have any external HDD to backup !

---

### Post by oldfred on 2011-10-30
If your data has no value then you do not have to have backups as you can then just reinstall from the Vendor recovery DVDs.

You have created dynamic partitions which is a major problem. Do not create partitions with Windows. Almost all Windows 7 systems have used all 4 primary partitions and then Windows converts to dynamic if you add more. Windows does not let you convert back. Per Windows you have to back up, delete everything, and reinstall/restore data.

You have g: as NTFS labeled Ubuntu. Ubuntu does not install to NTFS partitions unless you use wubi and I am not sure that works with dyamic. Some users have also reported that Windows repairs do not work on dynamic partitions. 

Did you make your recovery vendor DVDs & a Window repairCD? That is vital. I copy my most important data to DVDs.

If you use all 4 primary partitions you cannot create more and the space is unusable. Normally you create an extended partition (which is one of the 4 primaries) to include all the unallocated space and then you can create as many logical partitions as you want.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

