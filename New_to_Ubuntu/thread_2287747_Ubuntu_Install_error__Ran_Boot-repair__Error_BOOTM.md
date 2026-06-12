---
title: "Ubuntu Install error // Ran Boot-repair // Error: BOOTMGR is missing"
date: 2015-07-22
forum: New to Ubuntu
---

### Post by jl.smith736 on 2015-07-22
So I've tried searching endlessly on these forums for a fix, and no luck with any of the suggestions I've read and tried thus far.

Basically I tried installing Ubuntu 14.10 from a USB-drive on a Win7 desktop, and that's when the issues began. 

The initial install for some unknown reason did not go correctly. When trying to boot computer (simply turning it on) I was given an error message along the lines of "GRUB-error   minimal bash-like line editing enabled". I let my roommate fiddle around with the device to see if he could solve the issue, and again; no luck. 

I have already tried running the boot-repair from a Live-USB and now am given a new error message which states: "BOOTMGR is missing     press CTRL + ALT + Del to restart", when restarting the same error message re-appears. Below is the boot info script for assistance. I do not know how, or why - but i believe my roommate may have deleted the Default partition that had the windows boot files pre-loaded. I can see the files are still in the Windows>boot folder, but im not sure why the computer will not boot through them. 

[http://paste.ubuntu.com/11918032/](http://paste.ubuntu.com/11918032/)

Any response or suggestions will be highly welcomed! I am in great need of getting a working Windows computer again so I can work from home. I am currently unable to work from home due to lack of a working Win7 device...

---

### Post by oldfred on 2015-07-22
Your room-mate deleted the essential Window boot partition which is the only place Windows has its boot files And all the Linux partitions.. So many users have deleted the Windows Boot, that if you run Boot-Repair it will copy the boot files into the main install, just in case.

You do not have to have separate Windows Boot partition. But will have to move boot flag to sda2, and it looks like Boot-Repair already did that.
But due to copy write issues Boot-Repair cannot run most Windows fixes. You need the Windows repairCD or flash drive you made when you installed Windows or first booted it if pre-installed. Or your Windows installer DVD.

       f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/)

If you do not have a repairCD or flash drive, but have access to another Windows system with the same 32 bit or 64 bit version.

 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You also may be able to use testdisk from Ubuntu to restore the sda1 partition. It is in repository so easy to add to live installer. If you can restore it, then you have to move boot flag back to sda1 with gparted.
      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If in testdisk advanced mode to see files, you see bootmgr, be sure to also copy that, just in case. And you can use third party Windows repair tools to rebuild a new BCD. But better to try to restore entire partition.

---

### Post by jl.smith736 on 2015-07-23
Awesome Fred! Thanks for the response, I'm getting started on reading and trying your suggestions. Can you copy/reference the section of the boot script that you were able to discern the errors and issues you referenced above. I've read through the script but couldn't really decipher the text to anything meaningful...

---

### Post by yancek on 2015-07-23
The BOOTMGR is missing is a windows error.  Linux names drives as sda (first hard drive), sdb (second hard drive) and partitions sda1 (first hard drive, first partition) as examples.  Look at the boot repair output.  There is no sda1 which was your windows boot partition.  You can also see that all you have is sda2 which is the second partition of the first hard drive and contains your windows system files but no boot files.  There are no Linux partitions show on the 500GB drive.

---

### Post by yancek on 2015-07-23
The BOOTMGR is missing is a windows error.  Linux names drives as sda  (first hard drive), sdb (second hard drive) and partitions sda1 (first  hard drive, first partition) as examples.  Look at the boot repair  output.  There is no sda1 which was your windows boot partition.  You  can also see that all you have is sda2 which is the second partition of  the first hard drive and contains your windows system files but no boot  files.  There are no Linux partitions show on the 500GB drive.

---

### Post by oldfred on 2015-07-24
Yancek has explained it.

But when you have missing data, it is more difficult to know what is missing. Often several of us have to review same report and see different things.

Some of us have seem many bootscripts and know what to expect.

---

### Post by jl.smith736 on 2015-07-28
Still no success. I tried using the TestDisk tool to recover the deleted partition. I believe i was able to recover the correct partition (following the step-by-step for TestDisk) but the end result wasn't exactly what i think it was supposed to be. It seems i recovered the entire hard drive or some sort because now it looks like this through GParted (see screenshot)  [ATTACH=CONFIG]263447[/ATTACH]


I have a questions, but being that computer fixes are never this simple, i assume you can give a better explanation. If all the Windows boot files (including the BOOTMGR.exe) are in the Windows/Boot folder; why can't i create a new partition (100MB) before the main partition on my C: drive, and just move the Windows Boot folder and its' content onto that partition? (screenshots below show folder & contents)
[ATTACH=CONFIG]263448[/ATTACH][ATTACH=CONFIG]263449[/ATTACH][ATTACH=CONFIG]263450[/ATTACH]

Additionally in the Windows folder is a "Recovery" folder. is there anything of use in this folder? 


I basically just want to get my computer back to a working Win7 machine. I have already made backup of all personal data (e.g., documents, photos, etc.); but a friend built this computer for me so I have no original software, or OE recovery disks/backups...

---

### Post by jl.smith736 on 2015-07-28
thanks for the response Yancek. can you see my response to oldfred below which curtails off your info found. Any help/advice??

---

### Post by yancek on 2015-07-28
In your initial post, the info you posted showed only one partition, sda2 which was a windows ntfs partition on a primary partition.  There was unallocated space at the beginning of the drive which was probably the former boot partition which somehow was deleted.

The GParted image you posted now shows sda1 as an Extended partition with a logical partition (sda5) inside it which is 465GB.  You have 100MB of unallocated space at the beginning of the drive which you could use GParted to create another partition, format it as ntfs to use as a boot partition.  You can't boot windows unless its boot files are on a primary partition according to the microsoft site.

I don't think that moving the boot files to this newly created partition would make it bootable as you will need some code in the master boot record.  This is usually done with a windows installation DVD or a Recovery CD.  You might be able to use a Recovery CD from another computer if it had the same windows version as you had such as Home Premium or whatever. 
You might also try an online search for a recovery CD.  They used to be a free download at neosmart but now there is a charge for the CD.

---

### Post by oldfred on 2015-07-28
In testdisk you should have made the first 100MB as a NTFS primary partition with the boot flag, and the second also as NTFS primary partition. You cannot repair Windows if it is in a logical partition. And starts & sizes of partition will not be correct, but several chkdsks may fix that.

I would first try to see if Testdisk will let you recover the first 100MB as a NTFS partition. Only if you cannot then you can format it, but that will erase it.

You will need a Windows repair CD or flash drive to repair Windows.

---

### Post by leunam12 on 2015-07-29
You can probably create a recovery disk using files from the Recovery and the Windows folder. Take a look at the link below: I think you can do all that from Linux. Format your USB stick n Gparted and flag it with the boot flag and mount the sdb2 drive and see if you can access the files.

[http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools](http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools)

---

### Post by jl.smith736 on 2015-08-06
Good news and bad...

If i try and boot from HDD, i just get black screen with blinking cursor forever. The boot partition and most importating BOOTMGR.exe is still missing....

[Good news, *maybe...*] I got a hold of a Win7 recovery CD. It is made for a Dell computer (which i do not have); but i am unsure if this will cause issues. 

I booted to the CD and tired running the **Repair Windows Boot Issues **option which did not give me any success. I believe i set myself back a step when I tried to recover the deleted boot partition prior using TestDisk. For some reason, i seemed to have copied the main partition of my HDD so i now have some weird issue with this resulting in the failure of the the repair CD. 

[Bad news] Like i indicated above, i screwed up my partitions with the *extended*. see below. I think they're copies of eachother that was "recovered" using TestDisk. I thought i was "recovering" the deleted boot partition. I was wrong. 

[ATTACH=CONFIG]263694[/ATTACH]

Please keep in mind im New to Ubuntu and computers for the most part so dont fully understand everything im reading, particullary some of the words. I believe one of these parititons is *Logical *. I dont know what that means, but im certain it cant be good.


Considering i now have the Win7 Recovery/Repair CD, i was hoping i could restore my HDD partition structure back to default (i.e.: small boot partition first, large partition to hold OS, files, and personal documents). 

I've already made a backup of my photos, documents, etc. from the HDD; but i just want to get it back to an operating Win7 machine. This was all a result of the deletion of the partition holding the Win7 boot folder/files.

---

### Post by yancek on 2015-08-06
I don't know that a recovery CD will do the necessary repairs to your boot files, generally an install CD/DVD is required.  Could you tell us what happened when you ran the recovery CD?

>  i screwed up my partitions with the *extended*. see below. I think they're copies of eachother 

That is not a problem.  The Extended partition (sda1) contains the logical partition (sda5).  An Extended partition cannot hold data but a logical partition can.  There is a lot of info on this here at the forum if you search or do an online search.  the problem is with the filesystem on sda5 as show by the red icon in addition to the deleted boot partition.  Have you tried looking at the microsoft site or windows forums?  They may be able to give better advice as it specifically related to that operating system.

---

### Post by oldfred on 2015-08-06
Did you try running testdisk and recovering the first 100MB as bootable (*) and the main NTFS as P - primary, not logical?

Post screen shots of testdisk, if you need help.

---

