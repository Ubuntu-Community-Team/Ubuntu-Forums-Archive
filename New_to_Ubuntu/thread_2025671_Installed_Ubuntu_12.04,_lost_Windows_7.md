---
title: "Installed Ubuntu 12.04, lost Windows 7"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by jkatlek on 2012-07-14
Alright, I'm kind of new to Ubuntu, so I really screwed up my install. I downloaded the installation CD (Ubuntu 12.04) and ran it on my Windows 7 PC. I figured I knew what I was doing when I set up my partitions, but I totally failed. Here's what happened:

First, I set aside a 100 GB partition for my Ubuntu install, and then I ran the disc. However, it labeled this partition as "unusable". I then deleted the partition and used the built-in tool (on the installation CD) to partition it. However, I mistakingly reformatted the partition where my Windows 7 install was.

Eventually, I got Ubuntu installed. Despite this, I would like to have access to Windows 7 once again. I have an original Windows 7 Home Premium disc and the OEM product key. However, the problem I face with utilizing this is that when I try to reinstall Windows 7 with this method, it does not detect any available disks (even when I repartition and format NTFS).

I also have a recovery partition left on my HD, but when I try to load it from the startup options, I am not given the option to do a system recovery (it is grayed out). I believe I also have the HP Recovery Discs somewhere but have yet to find them.

Is there any way (considering the circumstances) that I could get Windows 7 back on my computer?

Thanks

---

### Post by GreatDanton on 2012-07-14
If your Ubuntu is using whole disk, then you have to shrink Ubuntu partition with Gparted, and then install windows7 on it. Make sure you have backups before you do this. If your Ubuntu is not on the whole Hard disk drive, then format the other partition (where you want to install Windows7), and leave it as unallocated.

After that put your CD with windows7 on it and the installer will take care of it.

Good luck with your installation!

---

### Post by jkatlek on 2012-07-14
Actually, I have already tried repartitioning with Gparted (and even formatting it NTFS). However, when I get to the point in the Windows 7 install where I have to choose an install location, no disks appear.

---

### Post by Sef on 2012-07-14
Have you checked out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk")?

---

### Post by jkatlek on 2012-07-14
Unfortunately, since my HD had to be completely reformatted in order to get Ubuntu installed, I fear that recovering the Windows 7 partition is almost hopeless.

---

### Post by mwl128340 on 2012-07-14
make sure when you partition, the ntfs partition is at the beginning of the disk. windows being windows wont recognixe it unless it is. here is a link to multibooting with windows and read the whole page before doing anything. id recommend reading as much as possible before proceeding with partitioning. [http://www.multibooters.co.uk/multiboot.html]("http://www.multibooters.co.uk/multiboot.html")

---

### Post by Mark Phelps on 2012-07-14
Would help us if we could see what you have, instead of guessing.

To do that, boot from an Ubuntu CD, choose the Try Ubuntu option, and when you (finally) get to a desktop, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one) -- and post the output here.

That way, we can tell you what partitions to remove.

And, don't go creating any from Ubuntu -- it doesn't use the same NTFS version as does Win7.  Best to let Win7 create its own partitions as part of the install.

---

### Post by westie457 on 2012-07-14
> **Sef said:**
> Have you checked out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk")?

+1 to this.

It is very good for recovering partitions.

It is best to use from a LiveCD/USB. Testdisk is available in the repositories. Full usage instructions are available here. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by jkatlek on 2012-07-14
> **mwl128340 said:**
> make sure when you partition, the ntfs partition is at the beginning of the disk. windows being windows wont recognixe it unless it is. here is a link to multibooting with windows and read the whole page before doing anything. id recommend reading as much as possible before proceeding with partitioning. [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

This definitely makes sense. :D However, since my Ubuntu/swap partitions were created first, I have no way of making Windows at the beginning of the disk without uninstalling and then reinstalling - unless there's some way to rearrange them.

> **Mark Phelps said:**
> Would help us if we could see what you have, instead of guessing.

To do that, boot from an Ubuntu CD, choose the Try Ubuntu option, and when you (finally) get to a desktop, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one) -- and post the output here.

That way, we can tell you what partitions to remove.

And, don't go creating any from Ubuntu -- it doesn't use the same NTFS version as does Win7.  Best to let Win7 create its own partitions as part of the install.

I haven't yet run that command in terminal yet. However, I did take a screenshot of Gparted:

[IMG]http://img406.imageshack.us/img406/5007/gpartedy.png[/IMG]

---

### Post by oldfred on 2012-07-14
You still have all 4 primary partitions used. So you have to delete one. Many backup and then delete the HP tools as it is small and  easily backed up. Someone posted that it can also be downloaded from HP if necessary.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

But windows has to be in a primary partition or boot from a primary. Since it was Windows 7 you can use sda1 still as the boot partition or you could delete it can just install Windows 7 into one partition. If you have a primary NTFS formated partition with the boot flag Windows will install to it. Some have posted that gparted's NTFS needs reformating if you are using Windows 7 as it formats it ok for XP. Windows only creates the small boot partition so you can encrypt the main install, so otherwise it does not have to be separate. Many have installed Windows 7 into one partition particularly when overwriting Vista.

---

### Post by Jerry N on 2012-07-14
> **Mark Phelps said:**
>   ...And, don't go creating any from Ubuntu -- it doesn't use the same NTFS version as does Win7.  Best to let Win7 create its own partitions as part of the install.

I have installed Win 7 several times on NTFS partitions created and formatted by gparted and have had no problem whatsoever.  I used either gparted live or parted magic, but I don't remember which.  It could have been both of them at different times.

Jerry

---

### Post by jkatlek on 2012-07-15
Thanks for all the help guys! I got Windows 7 reinstalled alongside Ubuntu 12.04. In case you're curious, here's how I did it:

1.) I reformatted my entire HD using the diskpart command via my Windows 7 install disc (unfortunately, that means my recovery partition is gone forever though I know the recovery discs are laying around somewhere).
2.) I installed Windows 7 using the install disc.
3.) I installed Ubuntu 12.04 using the "Install Alongside Windows 7" option.

---

