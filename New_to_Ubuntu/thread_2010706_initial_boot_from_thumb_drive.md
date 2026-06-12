---
title: "initial boot from thumb drive"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by jlapinski4 on 2012-06-25
I just purchased a asus zenbook prime and haven't taken it out of the box.  I plan to run a single boot of 12.04 LTS. Can anyone answer this question: if I download the distro to a thumb drive and load the drive prior to the turning the laptop on for the 1st time, can I immediately load ubuntu, wipe out windows, and not cause any damage?

---

### Post by Kopkins on 2012-06-25
Sure, I would just check your hardware compatibility before wiping windows. 

Why not keep it as a dual boot if you have the hard drive space? I know that sometimes when my ubuntu install is acting up I like to have the os x side of my macbook to use, because I know it will always work.

---

### Post by oldfred on 2012-06-25
While I now have stopped booting XP after about 5 years of saying I would, it may pay just to create the recovery DVDs in case you want to sell computer & buyer wants Windows. Or, we see many users with that one application that does not run in Ubuntu and want Windows dual boot back. (Often with new hardware virtual install may be better, but you cannot do that with the OEM version.)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Then you can install Ubuntu or dual boot as you have the original software available just in case.

---

### Post by jlapinski4 on 2012-06-26
> **oldfred said:**
> While I now have stopped booting XP after about 5 years of saying I would, it may pay just to create the recovery DVDs in case you want to sell computer & buyer wants Windows. Or, we see many users with that one application that does not run in Ubuntu and want Windows dual boot back. (Often with new hardware virtual install may be better, but you cannot do that with the OEM version.)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694



Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Then you can install Ubuntu or dual boot as you have the original software available just in case.


Thank you! It is brand new machine with nothing but the pre-installed  software.  Will a dual boot cause performance issues with Ubuntu? I have  a read in a few places that dual booting isn't the best option.  

I have an old xp laptop that I may wipe clean with a new install first to see how difficult it is.

---

### Post by jlapinski4 on 2012-06-26
> **Kopkins said:**
> Sure, I would just check your hardware compatibility before wiping windows. 

Why not keep it as a dual boot if you have the hard drive space? I know that sometimes when my ubuntu install is acting up I like to have the os x side of my macbook to use, because I know it will always work.


It's a brand new machine with just the preinstalled software. My only concern with a dual boot is sacrificing performance on the ubuntu side.  I currently run a mac book pro that I intend to keep as a backup

---

### Post by Kopkins on 2012-06-26
> **jlapinski4 said:**
> It's a brand new machine with just the preinstalled software. My only concern with a dual boot is sacrificing performance on the ubuntu side.  I currently run a mac book pro that I intend to keep as a backup

Dual booting won't sacrifice any performance. When you dual boot the only thing that is shared is hard drive space. Only one OS is booted at a time so whichever is running has full access to your hardware resources, so no performance is lost.

To test your hardware compatibility I would just boot up Ubuntu on your liveusb, check to make sure that everything works, meaning just go through everything and use each bit of hardware. Test the wireless, ports, webcam, etc. just to make sure you're not going to be disappointed when you install and part of it doesn't work.

Kopkins

---

### Post by oldfred on 2012-06-26
Most new computers use all four primary partitions in the old BIOS and MBR(msdos) partitioning configuration. A few newer one have the UEFI with gpt partitioning without the proposed lock down that Windows 8 will require.

Ubuntu only needs 10GB to install with some working room. I normally suggest up to 25GB  for / if you have a separate /home, shared NTFS data partition or data in other Linux partitions as your data can be very large. But system does not have to be. Neither does the Windows system partition but it usually needs to be 30 to 50GB with data in other partition(s).

Use Windows to shrink the Windows NTFS partition but not to create any new partitions or it may convert to dynamic which does not work with Linux.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by Cheesemill on 2012-06-26
Even if you do plan to remove Windows then I would at least boot it up once and create the recovery disks. When it comes to selling it second hand you will get more money for it if you can reinstall Windows first or provide the recovery disks along with it.

---

### Post by audiomick on 2012-06-26
The only solid reason not to boot into Windows on a new machine is if you plan to try and get a refund on the basis of having rejected the windows on the machine. If you are planning on doing that, you might like to unpack the machine  in front of the shop guy and have him watch you re-format the drive without having started windows.

If you don't plan on trying that, I would do the following.

Make your set of recovery disks.
As mentioned, you will quite likely have 4 primary partitions on there. Delete the one that is the recovery one.

Use the Windows tool to shrink down all the Windows partitions. Leave Windows a bit of room, but if you are not planning on using it, it wont need much. Since you have payed for Windows "by default", you may as well leave it on there unless you are absolutely desperate for the drive space.

Create an extended partition in the empty space, and do your Ubuntu install in there.

---

### Post by jlapinski4 on 2012-06-27
> **audiomick said:**
> The only solid reason not to boot into Windows on a new machine is if you plan to try and get a refund on the basis of having rejected the windows on the machine. If you are planning on doing that, you might like to unpack the machine  in front of the shop guy and have him watch you re-format the drive without having started windows.

If you don't plan on trying that, I would do the following.

Make your set of recovery disks.
As mentioned, you will quite likely have 4 primary partitions on there. Delete the one that is the recovery one.

Use the Windows tool to shrink down all the Windows partitions. Leave Windows a bit of room, but if you are not planning on using it, it wont need much. Since you have payed for Windows "by default", you may as well leave it on there unless you are absolutely desperate for the drive space.

Create an extended partition in the empty space, and do your Ubuntu install in there.

I am not desperate for disk space - just had years of bad experiences with windows.  I seem to have run it to a new problem anyway... Since it is an ultrabook I bought an external CD/DVD drive and the laptop will not boot from it! Any ideas?

---

### Post by jlapinski4 on 2012-06-28
> **oldfred said:**
> Most new computers use all four primary partitions in the old BIOS and MBR(msdos) partitioning configuration. A few newer one have the UEFI with gpt partitioning without the proposed lock down that Windows 8 will require.

Ubuntu only needs 10GB to install with some working room. I normally suggest up to 25GB  for / if you have a separate /home, shared NTFS data partition or data in other Linux partitions as your data can be very large. But system does not have to be. Neither does the Windows system partition but it usually needs to be 30 to 50GB with data in other partition(s).

Use Windows to shrink the Windows NTFS partition but not to create any new partitions or it may convert to dynamic which does not work with Linux.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. 
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)


Now I am convinced that Windows 7 prevents itself from being uninstalled. The computer will not boot from a CD/DVD and when I run the CD and attempt to make a new boot file to allow it to I get multiple error messages!  HELP!!

---

### Post by oldfred on 2012-06-28
Are you following instructions from Ubuntu site?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by jlapinski4 on 2012-07-03
> **jlapinski4 said:**
> I am not desperate for disk space - just had years of bad experiences with windows.  I seem to have run it to a new problem anyway... Since it is an ultrabook I bought an external CD/DVD drive and the laptop will not boot from it! Any ideas?


Resolved the issue with the external CD drive and the boot issues. So easy once I thought about it...

---

