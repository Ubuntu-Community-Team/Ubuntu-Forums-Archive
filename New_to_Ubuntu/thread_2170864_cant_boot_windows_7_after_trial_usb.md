---
title: "cant boot windows 7 after trial usb"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by chris90 on 2013-08-27
I am really scared here.  I wanted ti try ubuntu so I put it on a usb like instructed.  I switched my boot to usb and tried it out.  I never installed ubuntu.  Now when I start up I get startup repair screen.  I need my windows back.  Please someine point me in the right direction.  I trued my install disk and repair disk still wont boot.  I tried in command prompt bootrec.exe/fixmbr and /fixboot bit nothing still.  Please help me.

---

### Post by kesman on 2013-08-28
Is it this screen: [http://cdn.howtogeek.com/wp-content/uploads/2009/12/sshot20091217020232.png](http://cdn.howtogeek.com/wp-content/uploads/2009/12/sshot20091217020232.png)

If so, doesn't it help to select "start windows normally"?

---

### Post by chris90 on 2013-08-28
> **kesman said:**
> Is it this screen: [http://cdn.howtogeek.com/wp-content/uploads/2009/12/sshot20091217020232.png](http://cdn.howtogeek.com/wp-content/uploads/2009/12/sshot20091217020232.png)

If so, doesn't it help to select "start windows normally"?

It just goes directly to the startup repair no matter if I select repair or start normaly.  I cant use my computer now and will loose everything with a reformat.  So there is no way to fix this or no one cares?  Whats the forum for.  I searched the forum and cant find a solution that works.

---

### Post by newb85 on 2013-08-28
Did you switch the boot settings in your BIOS back to your HDD (or SSD, as the case may be)?

---

### Post by eternal243 on 2013-08-28
> **chris90 said:**
> It just goes directly to the startup repair no matter if I select repair or start normaly.  I cant use my computer now and will loose everything with a reformat.  So there is no way to fix this or no one cares?  Whats the forum for.  I searched the forum and cant find a solution that works.

Actually we do care, trying linux is supposed to be a good experience, and a live usb/cd should not break your windows installation, but we need some more information to know how to help you.

First tell us what kind of computer you are using, desktop or laptop? What brand/model is it?
What version of Windows do you have installed? Win XP/Vista/7/8?

Where you able to load Ubuntu from your usb-stick without any problem? If so then start Ubuntu from your USB again and run the following command from Terminal:
```
sudo fdisk -l
```

This will list all harddrives on your computer and all partitions on those harddrives.

Then copy that information and post back in this thread, it will help us figure out what the problem might be. :)

---

### Post by mastablasta on 2013-08-28
+1 live OS does not touch the hard disk on boot.

---

### Post by sceptre78 on 2013-08-28
But the live OS does very little to stop you from using something like gparted. Check your bios like                                                                                     [[COLOR=#000000]newb85[/COLOR]]("http://ubuntuforums.org/member.php?u=833049") suggested. Make sure the drive with Windows 7 is first. If that doesn't work. list your partitions with the above instructions. Windows should be the partition with the NTFS file system (under system). (or if you can access it from the live OS desktop) If you got that you should still have windows . First try Startup Repair (first option in system recovery on install disk). if that doesn't work then boot with your install disk, be sure to click repair, then choose command and prompt type
 [B][I]
bootrec.exe /RebuildBcd[/I][/B]  

The above command will scan all your disks for other operating systems compatible with Windows 7 (including Windows) and allow you to add them to your system's boot list.

Here are some other options: 
[http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)

---

### Post by chris90 on 2013-08-28
> **sceptre78 said:**
> But the live OS does very little to stop you from using something like gparted. Check your bios like                                                                                     [[COLOR=#000000]newb85[/COLOR]]("http://ubuntuforums.org/member.php?u=833049") suggested. Make sure the drive with Windows 7 is first. If that doesn't work. list your partitions with the above instructions. Windows should be the partition with the NTFS file system (under system). (or if you can access it from the live OS desktop) If you got that you should still have windows . First try Startup Repair (first option in system recovery on install disk). if that doesn't work then boot with your install disk, be sure to click repair, then choose command and prompt type
 [B][I]
bootrec.exe /RebuildBcd[/I][/B]  

The above command will scan all your disks for other operating systems compatible with Windows 7 (including Windows) and allow you to add them to your system's boot list.

Here are some other options: 
[http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)

Tried all this and my partition is only showing the storage of 598 not the windows partition.  Still cant boot

---

### Post by sceptre78 on 2013-08-28
> **eternal243 said:**
> Actually we do care, trying linux is supposed  to be a good experience, and a live usb/cd should not break your  windows installation, but we need some more information to know how to  help you.

First tell us what kind of computer you are using, desktop or laptop? What brand/model is it?
What version of Windows do you have installed? Win XP/Vista/7/8?

Where you able to load Ubuntu from your usb-stick without any problem?  If so then start Ubuntu from your USB again and run the following  command from Terminal:
```
sudo fdisk -l
```

This will list all harddrives on your computer and all partitions on those harddrives.

Then copy that information and post back in this thread, it will help us figure out what the problem might be. :smile:


Can you copy and past the output from the instructions above. It will look something like this:

root@uplink:/# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e136

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   234440703   117219328   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0004875d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1250263039   625130496   8e  Linux LVM

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008e732

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1       953335808   976773119    11718656   82  Linux swap / Solaris
/dev/sdc2       758024192   953335807    97655808    b  W95 FAT32
/dev/sdc3            2048   758024191   379011072   8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/mapper/home-home: 1028.2 GB, 1028233625600 bytes
255 heads, 63 sectors/track, 125008 cylinders, total 2008268800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

---

### Post by chris90 on 2013-08-28
I followed the link above.  Did everythin step by step.  Now my pc is showing a error and wont start.  The windows 7 shows up but wont boot.

---

### Post by sceptre78 on 2013-08-28
whats the error?

---

### Post by chris90 on 2013-08-28
Started to boot finally then bsod.  I dont want to use ubuntu.  Its just keeps bsod after it says starting windows

---

### Post by chris90 on 2013-08-28
> **sceptre78 said:**
> whats the error?

Here is a pic

---

### Post by sceptre78 on 2013-08-28
can it boot in safe mode? F8 before the starting windows splash screen, choose safe mode.

---

### Post by chris90 on 2013-08-28
> **sceptre78 said:**
> can it boot in safe mode? F8 before the starting windows splash screen, choose safe mode.

I tried same thing bsod

---

### Post by eternal243 on 2013-08-28
> **chris90 said:**
> I followed the link above.  Did everythin step by step.  Now my pc is showing a error and wont start.  The windows 7 shows up but wont boot.

Well, if you want help to solve your problem, you need to help us help you, try to post all your hardware specifications as good as you can and answer our questions. I realize you might not know exactly what kind of hardware you have in your computer, but write what you do know.

It is at least good to know that you are running Windows 7.

**1: What else do you know about your computer? Brandname? Model number? Other things?**
This will help us with searching for other people who have had similar problems, it could be specific to your computer.

**2: Are you able to boot Ubuntu from the USB you made in your first post?**
This is important because sometimes you can repair a damaged windows installation from Linux. And in worst case scenario it might be a way to save important documents and files from your harddrive.

**3: If you can get into Ubuntu from your USB, can you write the command "sudo fdisk -l" into terminal and post whatever output you get from that command here?**
This helps us to see if your harddrive can be detected successfully by Linux and might also give us a hint if the data on your drive is intact.

And finally, if you get any error messages, then post the error messages including any error code here, it might give us a clue at what is going on. =)

**EDIT: ** but first follow the tips in sceptre78's post below.

---

### Post by sceptre78 on 2013-08-28
From Microsoft:

To work around this issue, start the computer from the disc drive or  from the USB drive by using the Windows installation media. Delete the  Bootcat.cache file, and then restart the computer.

[http://support.microsoft.com/kb/981833](http://support.microsoft.com/kb/981833)

**Note** The Bootcat.cache file is located at  %SystemRoot%\system32\codeintegrity.

---

### Post by chris90 on 2013-08-28
> **eternal243 said:**
> Actually we do care, trying linux is supposed to be a good experience, and a live usb/cd should not break your windows installation, but we need some more information to know how to help you.

First tell us what kind of computer you are using, desktop or laptop? What brand/model is it?
What version of Windows do you have installed? Win XP/Vista/7/8?

Where you able to load Ubuntu from your usb-stick without any problem? If so then start Ubuntu from your USB again and run the following command from Terminal:
```
sudo fdisk -l
```

This will list all harddrives on your computer and all partitions on those harddrives.

Then copy that information and post back in this thread, it will help us figure out what the problem might be. :)

Im running windows 7 ultimate 64bit on a custom pc.  Asus board 640gb wd hd.  Heres a pic of info.

---

### Post by chris90 on 2013-08-28
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2d2feaa1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848  1250258943   625026048    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   312496127   156247040    7  HPFS/NTFS/exFAT

Disk /dev/sdg: 8011 MB, 8011120640 bytes
255 heads, 63 sectors/track, 973 cylinders, total 15646720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x090511ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          63    15646719     7823328+   b  W95 FAT32

---

### Post by chris90 on 2013-08-28
> **sceptre78 said:**
> From Microsoft:

To work around this issue, start the computer from the disc drive or  from the USB drive by using the Windows installation media. Delete the  Bootcat.cache file, and then restart the computer.

[http://support.microsoft.com/kb/981833](http://support.microsoft.com/kb/981833)

**Note** The Bootcat.cache file is located at  %SystemRoot%\system32\codeintegrity.

So command promt the what do i type?

---

### Post by chris90 on 2013-08-28
I dont know how to get to % system32%\........

---

### Post by sceptre78 on 2013-08-28
cd windows\system32\codeintegrity\

dir/w   (verify Bootcat.cache is there)

del Bootcat.cache


dir/w   (verify Bootcat.cache is gone)

reboot system

---

### Post by chris90 on 2013-08-28
> **sceptre78 said:**
> cd windows\system32\codeintegrity\

dir/w   (verify Bootcat.cache is there)

del Bootcat.cache


dir/w   (verify Bootcat.cache is gone)

reboot system


So when I open command prompt it says
X:\windows\system32>

I then type the command in you posted?

---

### Post by sceptre78 on 2013-08-28
yes.

cd windows\system32\codeintegrity\          (takes you where you need to go)

 dir/w                                                     (verify Bootcat.cache is there)               

del Bootcat.cache                                    (deletes the file)

dir/w                                                       (verify Bootcat.cache is gone)



then reboot your computer

EDIT: cd C:\windows\system32\codeintegrity\

---

### Post by eternal243 on 2013-08-28
> **chris90 said:**
> Im running windows 7 ultimate 64bit on a custom pc.  Asus board 640gb wd hd.  Heres a pic of info.

That's good, all info looks great in the picture, your disk does not seem to be damaged. Removing the Bootcat.cache probably solves the problem, what puzzles me is how that got messed up by trying to run Ubuntu from a live USB since it shouldn't touch your harddrive at all, and that is a Windows file that only affects the Windows boot-process.

---

### Post by chris90 on 2013-08-28
> **sceptre78 said:**
> yes.

cd windows\system32\codeintegrity\          (takes you where you need to go)

 dir/w                                                     (verify Bootcat.cache is there)               

del Bootcat.cache                                    (deletes the file)

dir/w                                                       (verify Bootcat.cache is gone)



then reboot your computer




EDIT: you may  first have to cdir C:\         (change to C  )

Not there.

---

### Post by chris90 on 2013-08-28
> **eternal243 said:**
> That's good, all info looks great in the picture, your disk does not seem to be damaged. Removing the Bootcat.cache probably solves the problem, what puzzles me is how that got messed up by trying to run Ubuntu from a live USB since it shouldn't touch your harddrive at all, and that is a Windows file that only affects the Windows boot-process.

Not working

---

### Post by sceptre78 on 2013-08-28
try copying the file from a working PC of the same OS..... other then that I'm tapped out.

---

### Post by chris90 on 2013-08-28
This is awsome.  I try ubuntu and it screws up 4yrs worth of pics, movies.....  second time this did this to me.  I cant believe im gonna have to format over this.

---

### Post by eternal243 on 2013-08-28
> **chris90 said:**
> This is awsome.  I try ubuntu and it screws up 4yrs worth of pics, movies.....  second time this did this to me.  I cant believe im gonna have to format over this.

Man, get your facts straight, trying linux is always done at your own risk, I have told you that your harddrive is okay and all files are probably there, if you format it it will all be gone. If you can't take the time to solve it here, you can always turn in your computer to a professional and pay them to recover your files. And for the future my top suggestion is to always keep regular backups if you can't afford to lose your data. We have tried to be nice and help you, we are not professionals and we do this for free on our free time. Thanks.

---

### Post by chris90 on 2013-08-28
> **eternal243 said:**
> Man, get your facts straight, trying linux is always done at your own risk, I have told you that your harddrive is okay and all files are probably there, if you format it it will all be gone. If you can't take the time to solve it here, you can always turn in your computer to a professional and pay them to recover your files. And for the future my top suggestion is to always keep regular backups if you can't afford to lose your data. We have tried to be nice and help you, we are not professionals and we do this for free on our free time. Thanks.

Im just mad.  Not at you.  I appreciate all the help.  Losing all my files is a heartbreaker.  The reason I did it from usb is to prevent this problem from happen Ing again.

---

### Post by chris90 on 2013-08-28
> **sceptre78 said:**
> try copying the file from a working PC of the same OS..... other then that I'm tapped out.

Sceptre78 I appreciate all your help.  One last question.  How do I get the file and how do I copy it to my pc?  Thanks again

---

### Post by sceptre78 on 2013-08-28
Remove your hard drives. put them in a friends computer. move everything off of the smallest hard drive, put that one back in your computer. install windows.

---

### Post by sceptre78 on 2013-08-28
copy it from a friends computer onto the  usb stick you got ubuntu on

---

### Post by eternal243 on 2013-08-28
> **chris90 said:**
> Im just mad.  Not at you.  I appreciate all the help.  Losing all my files is a heartbreaker.  The reason I did it from usb is to prevent this problem from happen Ing again.

Yes, being mad is fine, but keeping a reasonable tone and good manners is important too, just to make sure, most of your files are probably still there, they can probably be recovered.

You don't seem to like Linux much at all, but what I would do is to start from a live CD, then plug-in an external harddrive, mount the internal drive and copy all the contents to the the external drive. There are other ways though and it might still be possible to recover your windows installation, even though I'm at a loss on how to do that.

I have been trying to help you with a problem I have never experienced, so it is not easy at all to help when I can't see what is going on.

> **chris90 said:**
> Sceptre78 I appreciate all your help.  One last question.  How do I get the file and how do I copy it to my pc?  Thanks again

You could copy it to an USB-stick or external harddrive, but I don't know if it will help.

---

### Post by sceptre78 on 2013-08-28
boot ubuntu in live mode..... click NOTHING except the windows hdd and the folders needed to navigate to the filepath of where it needs to go and copy and past it over like you would in windows. shut down remove usb stick turn on computer

---

### Post by sceptre78 on 2013-08-28
after that I can only suggest try asking here.
[https://support.microsoft.com/oas/default.aspx?gprid=14019&st=1&wfxredirect=1&sd=gn](https://support.microsoft.com/oas/default.aspx?gprid=14019&st=1&wfxredirect=1&sd=gn)

---

### Post by chris90 on 2013-08-28
Thanks all.  Gonna format and reinstall on my 160gb.  Keep files on 640 and transfer.  Then reinstall on 640 and switch it all back.  Lot of work but I got to many photos of ky daughter I cant loose.  Thanks again.  Great support.  I will try ubuntu again but safer next time.

---

### Post by eternal243 on 2013-08-28
> **chris90 said:**
> Thanks all.  Gonna format and reinstall on my 160gb.  Keep files on 640 and transfer.  Then reinstall on 640 and switch it all back.  Lot of work but I got to many photos of ky daughter I cant loose.  Thanks again.  Great support.  I will try ubuntu again but safer next time.

I wish you the best of luck, both with the recovery of your files and with trying Ubuntu again. Take care! :)

---

### Post by sceptre78 on 2013-08-28
I don't if this will help but I keep my system (root) on the smaller HDD  and my home folder on the two larger drives. That way if something goes  wrong I only have to redo the system drive. anyway good luck.

---

### Post by sceptre78 on 2013-08-28
could it be hard drive issues, The times he claims it happens is when the HDD is being read or written too.

---

### Post by sceptre78 on 2013-08-28
sorry meant to put that somewhere else.

EDIT: too much caffeine, not enough sleep :p

---

### Post by eternal243 on 2013-08-28
> **sceptre78 said:**
> sorry meant to put that somewhere else.

You can edit your post instead of double/tripple posting. It keeps the forum uncluttered! =)
Just a tip for the future!

---

### Post by chris90 on 2013-08-28
So I reinstalled win 7 and now after install I got a black screen.  It will say starting windows then acts like it is gonna start and just sits at a black screen.  Any ideas?

---

### Post by chris90 on 2013-08-29
I got it to work.  Had to wipe both drives then reset bios.  something got messed up in there i think.

---

