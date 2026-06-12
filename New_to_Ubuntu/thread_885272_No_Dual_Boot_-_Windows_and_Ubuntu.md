---
title: "No Dual Boot - Windows and Ubuntu"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by buddytd on 2008-08-09
I am VERY new to Ubuntu and Linux, but not to computers (30+ years as a consulting professional, hardware and software). Even so, assume nothing when you respond, thanks in advance.

Anyway, I told the installer to reserve 50% of the partition to Windows XP and the other half to Ubuntu. Everything seemed to go normally until I rebooted.

I was not given any option for choice of bootup - it just came up in Windows XP as if I had never installed Ubuntu at all.

What do I do to make it give me the option to boot into one or the other?

Thanks in advance.

Bud Izen
Turner Oregon
[email]budizen@msn.com[/email]

---

### Post by Seti on 2008-08-09
Is it possible you installed Ubuntu first and then Windows? In that case, Windows would have over-written the disc's MBR during installation.

---

### Post by cdtech on 2008-08-09
It's just the GRUB boot loader wasn't installed to the boot sector.

You'll have to use the Live CD to install GRUB.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands.

$sudo grub
> root (hd0,0)
> setup (hd0)
> exit

Remove the Live CD reboot and you should see a GRUB boot menu.

##############################################
Differences of the GNU/Linux and GRUB device names:

1st Physical Hard Drive:
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)
/dev/hda3 ----(hd0,2)----- /dev/sda1-------(hd0,2)
/dev/hda4 ----(hd0,3)------/dev/sda2-------(hd0,3)

2nd Physical Hard Drive:
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hdb1---- (hd1,0)----- /dev/sdb1------ (hd1,0)
/dev/hdb2---- (hd1,1)----- /dev/sdb2------ (hd1,1)
/dev/hdb3---- (hd1,2)----- /dev/sdb1------ (hd1,2)
/dev/hdb4---- (hd1,3)----- /dev/sdb2-------(hd1,3)

---

### Post by buddytd on 2008-08-09
As I said, I am only new to Ubuntu, not to computers. I set up Windows XP first, then Ubuntu. It only boots into Windows and does not give any alternative options. Not sure if I can make this any clearer. Please let me know if you need more information. Here's what I did, in the order I did it:

Installed Windows XP, SP2. Updated to SP3 and all relevant patches. Ran defrag. Tested for proper operation.

Downloaded Ubuntu disk, checked it for validity, no problems. 

Rebooted and installed Ubuntu, creating a 50-50 partition for each OS.

Rebooted. Now it only boots into Windows with no options given on boot.

Hope that makes things more clear.

Bud

---

### Post by cdtech on 2008-08-09
Again, read my post. You'll have to boot using the **Ubuntu Live CD** to repair the issue.

**P.S.**
You have to have a mutual boot loader that can understand both Linux and Windows which will be the GRUB boot loader. This has to be installed over the Windows boot loader within the MBR (first sector of the drive)

---

### Post by Seti on 2008-08-09
Actually that is not too clear; from your description, you make it sound like you did your partitioning AFTER you had already installed Windows.
By 50-50 I take it you mean you divided your hard-drive into two paritions?

If you are going to dual-boot, I always suggest the following partition scheme to people. Use Gparted on the live CD to do this if you don't know how to use unix fdisk or cfdisk.

Make a primary partition for Windows. Typically it will be called /dev/hda1 or something along those lines. Then make a second primary partition of only about 500 MB for /swap. Make an extended partition after that to house your linux partitions. I always recommend making at least two separate paritions, one for / and one for /home/. That way, in the future if you need to reinstall Ubuntu, you only have to format / while all your personal files on /home remain intact.
Good luck!

---

### Post by epiphonygirl on 2008-08-10
Well, this might be a different take on things, you said you were new to linux, ubuntu specifically. Like you I am rather new to linux and ubuntu so I used wubi to install ubuntu inside of windows and haven't looked back. I would just format the harddrive and then install windows and use wubi for linux so that you can really give it a try and learn how to use it. Then you will probably learn a lot without a headache to begin with. All that you need to do is pop in the disk you made while running windows and then install, allocate up to 30GB of harddrive space to ubuntu and it'll install and offer you the boot option before windows starts to load. That would be my fix to allow you to just use the OS without having to troubleshoot right off the bat, or maybe troubleshoot something smaller, like [[COLOR="Blue"]wireless[/COLOR]]("http://ubuntuforums.org/showthread.php?t=873980") was in my case. Just a suggestion :D

---

### Post by gbrad901 on 2008-08-10
> **cdtech said:**
> It's just the GRUB boot loader wasn't installed to the boot sector.

You'll have to use the Live CD to install GRUB.

1) Boot off the LiveCD

2) Open a Terminal and type in the following commands.

$sudo grub
> root (hd0,0)
> setup (hd0)
> exit

Remove the Live CD reboot and you should see a GRUB boot menu.

##############################################
Differences of the GNU/Linux and GRUB device names:

1st Physical Hard Drive:
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)
/dev/hda3 ----(hd0,2)----- /dev/sda1-------(hd0,2)
/dev/hda4 ----(hd0,3)------/dev/sda2-------(hd0,3)

2nd Physical Hard Drive:
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hdb1---- (hd1,0)----- /dev/sdb1------ (hd1,0)
/dev/hdb2---- (hd1,1)----- /dev/sdb2------ (hd1,1)
/dev/hdb3---- (hd1,2)----- /dev/sdb1------ (hd1,2)
/dev/hdb4---- (hd1,3)----- /dev/sdb2-------(hd1,3)

I was having a similar issue. i installed windows xp into a partition i set up with the partition editor. windows took over and i followed your steps but windows does not show up on the grub list. i looked at the partition editor and that partition has an orange triangle with an exclamation point instead of the keys symbol.any ideas?

---

### Post by cdtech on 2008-08-10
You should shut down windows properly or it leaves the filesystem dirty. Some how you'll need to run "chkdsk /f" from the windows command prompt, **or "chkdsk /p" from the recovery console**. Try to use the latest gparted live cd. It is the latest version available, newer than the one on the Ubuntu cd.

---

### Post by gbrad901 on 2008-08-10
i can't get into windows at all. so i should run the gparted live cd and repeat your steps?

---

### Post by cdtech on 2008-08-10
That could work. You could use the windows install disc for the recovery mode but try the gparted live cd first it might save you some time here.

---

### Post by gbrad901 on 2008-08-10
oh well, no luck. i guess i'll do new installs

---

### Post by buddytd on 2008-08-10
When I installed, I used the Guided Setup, so I am presuming (first cousin to an assumption, and I HATE to make assumptions) that Ubuntu got installed onto the correct partition.

I followed the advice I was given, and tried to do the grub thing. When I got to the step

grub setup (hd0)

I never got any further because that statement generated

Error 17 Cannot mount selected partition

So, it looks to me like something non-standard is going on. I have no clue how to proceed from here.

Bud

---

### Post by bumanie on 2008-08-10
Boot live cd and post the output of > sudo fdisk -l This will show the partitions and OSes installed on your system, before playing around with grub, one needs to know what is physiacally on the hard drive/s.

---

### Post by tgyorgyi on 2008-08-10
I have the same problem. I had a well working XP/Hardy dual boot before. I re-installed hardy, and since then I get grub errors. I managed to get XP boot again with the help of the XP recovery CD, running fixmbr and fixboot, and then re-installed Hardy. But upon restarting XP starts automatically, there is no grub menu.

The tip with the grub shell commands result in "Error 17"

Result of fdisk -l is

> Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf20cb228

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            7039        7296     2072385   82  Linux swap / Solaris
/dev/sda3            2551        4345    14418337+  83  Linux
/dev/sda4            4346        7038    21631522+  83  Linux

Partition table entries are not in disk order

sda3 is my /home partition, sda4 is where Ubuntu is supposed to be installed.

---

### Post by buddytd on 2008-08-10
Ok, here's what fdisk reports:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x6c0adaf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17752   134205088+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9806    78766663+   7  HPFS/NTFS
/dev/sdb2            9807       38913   233801977+   5  Extended
/dev/sdb5           19515       38157   149749866   83  Linux
/dev/sdb6           38158       38913     6072538+  82  Linux swap / Solaris
/dev/sdb7            9807       19113    74758414+  83  Linux
/dev/sdb8           19114       19514     3221001   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by HotCupOfJava on 2008-08-10
OK - I have done several dual-boot installs. Here is what I suggest:

It sounds like Windows might be messed up. Re-install it. Don't worry about the partitions yet. Once Windows is reinstalled, run the Ubuntu Live CD and open GParted. Size the Windows partition down to what you want (you can actually click on the graphic of the filsystem and "drag" it over). This will create empty (no filesystem) space on the drive. That is what you want. Then reboot with the live cd again. This time choose "install ubuntu". When it gets to the screen with installation options, choose "Guided - use largest continuous free space". Proceed with installation. When it is finished and you reboot, it should give you the option of which OS you want to boot into. Be aware the first time you boot back into Windows, it will probably fuss and want to examine the filesystem. Let it do it, it will be OK.

---

### Post by tgyorgyi on 2008-08-11
XP was working fine before, and after. Nevertheless, I tried the clean install, nothing to lose right now. The problem is still on. I get automatic XP boot, no grub list. 

Meanwhile, I also noticed that the install is not running properly probably. But the Live CD works fine, I did the CD test, no errors there. What happens though is, that after copying and installing files, the process at one point stops, no error message, I just get back to the regular Live CD desktop, I am not promted to restart or anything. Maybe the install is not done fully, and grub is simply not written, this is why it cannot be found? I'll try and burn a new CD, and see if that makes any difference.

---

### Post by Bölvaður on 2008-08-11
> **tgyorgyi said:**
> Maybe the install is not done fully, and grub is simply not written, this is why it cannot be found? I'll try and burn a new CD, and see if that makes any difference.

Burn the alternate cd, it doesn't give you GUI installer but it uses less ram and is more solid and error free than the GUI one.
I think you are right about grub not being installed, but it also might be something I have never seen before. Installing with the alternate cd would solve your problem most likely.

---

### Post by Bölvaður on 2008-08-11
buddytd : If I were having the same problem as you are having I would without no doubt try to do a complete reinstall if I had done something wrong the first time.


But before you do that try seeing if Grub is ok. You can do it with a special cd from the grub website or check the grub files (in /boot) are alright.

Reinstalling:
I suggest to you to know exactly what you are going to do before you do it. So you map your partitions on paper, then boot up with the live cd and open up gParted (Partition Editor) and follow your plan. Use Ext3 for linux partitions, it is very secure compared to most.

I would suggest you to make /data partition in Linux for backups and make it easier later on to install different distro (format everything except /data and just mount it without formating it).

When you have installed windows on the windows partition (without touching the linux ones) you are ready to install the Ubuntu distro.
DO NOT USE GUIDED PARTITIONING.
You should have the experience to know what you are doing, so use manual partitioning option (I never trust auto configs). Mount and format the rest of the drives.

Swap partitions are automaticly mounted so no worries.
Your main Linux partition should be mounted to "/" (filesystem) and choose to format it.
You should mount your data partition to "/data" and format it (unless if you have data on it already).

I wouldn't expect any problems with booting after doing it manually unless if Windows some how managed to block grub and set it on fire.

---

### Post by kansasnoob on 2008-08-11
> **buddytd said:**
> Ok, here's what fdisk reports:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x6c0adaf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17752   134205088+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9806    78766663+   7  HPFS/NTFS
/dev/sdb2            9807       38913   233801977+   5  Extended
/dev/sdb5           19515       38157   149749866   83  Linux
/dev/sdb6           38158       38913     6072538+  82  Linux swap / Solaris
/dev/sdb7            9807       19113    74758414+  83  Linux
/dev/sdb8           19114       19514     3221001   82  Linux swap / Solaris

Partition table entries are not in disk order

What I can see from that is that you have two hard drives, sda and sdb, but both sda and sdb have a * in the boot column.

It also appears that you have two Linux operating systems installed, sdb5 and sdb7:confused:

It would be helpful to me to see a screenshot from gparted (aka: partition editor) which will be found in the live CD environment by going to System > Administration > Partition Editor. If you do in fact have two hard drives post a screenshot of both.

Sample screenshot:

[ATTACH]81117[/ATTACH]

You see in the upper right hand corner where I highlighted "/dev/sda" you can toggle to each drive.

It would also be helpful to see your menu list:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by kansasnoob on 2008-08-11
> **tgyorgyi said:**
> I have the same problem. I had a well working XP/Hardy dual boot before. I re-installed hardy, and since then I get grub errors. I managed to get XP boot again with the help of the XP recovery CD, running fixmbr and fixboot, and then re-installed Hardy. But upon restarting XP starts automatically, there is no grub menu.

The tip with the grub shell commands result in "Error 17"

Result of fdisk -l is



sda3 is my /home partition, sda4 is where Ubuntu is supposed to be installed.

Please start a new thread. Trying to solve two similar but different boot problems with individual competing menu lists and drive/partition arrangements will make my brain explode, and could easily result in the OP thinking suggestions meant for you are meant for him and vice versa.

---

### Post by buddytd on 2008-08-11
I have no idea how to embed the graphic screen shots so I attached them. Hopefully you can download and view them without problems. Otherwise, let me know how to embed them and I will do that.

It seems to me that, somehow, Ubuntu (and maybe Windows) sees my "boot" drive as drive B or 0 (i.e. number one) and the other drive as A or 1. Both drives are SATA 300GB drives.

I have no way to tell which one is logically configured as drive 0 or drive 1, so I was thinking I should just unplug one, then the other if necessary, to see which one Windows is installed on. Once that is determined, leave the other drive unplugged, then get rid of all other partitions on the Windows drive, and try to install Ubuntu again. Once Ubuntu is installed and boots, I could then re-attached the other drive and format it for data only.

Does this make sense?

Bud

---

### Post by appi2012 on 2008-08-11
It appears as if you installed ubuntu twice on the hard drive in the second picture. Can you boot into windows? If so, check whether your C: Drive is around 75 GB or 125 GB. If it is 125, then you have windows on dev/sda (in grub, known as hd0). If not, it is on dev/sdb (hd1). You tried to install ubuntu twice on sdb. What I would do, is delete all the linux/swap partitions on sdb (leaving the ntfs one) Unplug the drive that isn't the windows one. Now, run the installer, using the option to "use free space" (or something similar). Now you will have now errors in grub, and windows will also boot perfectly. If you wish, you can plug in the other drive, after the installation.

Hope that helps!

---

### Post by kansasnoob on 2008-08-11
Well, Ubuntu is definitely on drive sdb which Grub sees as hd(1,x). The (x) is the partition #. So Ubuntu is on either sdb7, which Grub sees as hd(1,6) or sdb5, which Grub sees as hd(1,4).

You see Grub begins numbering with 0 (zero) so sda is 0, sdb is 1 .......... and partition #5 is 4, partition #7 is 6, etc.

No need to unplug anything!

Could you now post the output of:

```
sudo gedit /boot/grub/menu.lst
```

I am confused as to why it appears that you have two ubuntu operating systems, but lets take one thing at a time, eh?

---

### Post by appi2012 on 2008-08-11
kansasnoob: buddytd mentioned something about installing ubuntu again, so I'm guessing he didn't delete the old ubuntu partition, just resized both the windows and the ubuntu partitions.

---

### Post by kansasnoob on 2008-08-11
> **appi2012 said:**
> kansasnoob: buddytd mentioned something about installing ubuntu again, so I'm guessing he didn't delete the old ubuntu partition, just resized both the windows and the ubuntu partitions.

That's what I thought too, I just thought he'd probably deleted the first before reinstalling, but that's easy to deal with after we get him bootable.

And we will!

---

### Post by appi2012 on 2008-08-11
If you can't boot windows, try burning a copy of super grub disk:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
Boot from the cd, and choose the Super Grub Disk -- with help :-))))) option.
Now go the the boot windows option (I'm not quite sure where in the menus this is, but its not hard to figure out. from here choose: "Activate partition" and choose one of your ntfs partitions (sda1 or sdb1) Then choose the boot partition options, and choose the same one. That should get windows to boot.

---

### Post by kansasnoob on 2008-08-11
If you're having trouble with the command:

```
sudo gedit /boot/grub/menu.lst
```

I perhaps should have mentioned that the .lst is lower case .LST .......... it's an L not a 1(one).

I just want to see what's already going on before we make any changes.

Also, could you tell me how much RAM you have. Your swao is unusually large.

---

### Post by kansasnoob on 2008-08-11
I've been following and trying to help with a few of these threads because I do a lot of installing and here's a step I forgot (or never knew), whatever it's awesome!

Check out comment #17 in this thread:

[http://ubuntuforums.org/showthread.php?t=886273&page=2](http://ubuntuforums.org/showthread.php?t=886273&page=2)

And be sure to thank caljohnsmith!

The "find grub" thing is awesome!

---

### Post by buddytd on 2008-08-11
Ok, I am making progress. Saving only the Windows partition, I blew out everything else with the partition editor. Using the CD, and rearranging the boot order in the BIOS, I made sure that the physical boot drive was hd0. I tried everyone's suggestions, but nothing worked.

I used fixmbr to fix the boot record, and a utility to replace the missing or damaged NTLDR and I could then boot Windows.

After that, I booted into the CD and expanded the Windows partition to use all of hd0. I then installed Ubuntu using all of hd1.

When I rebooted the first time, I wasn't quick enough to hit ESC and it booted right into Ubuntu. Worked great.

I then rebooted, hit ESC and the grub menu does NOT show a Windows boot option.

I tried the SUDO grub thing, but still came up with a 17 error, cannot mount drive, even though both drives appear to be mounted. Not sure if the hd0 is actually mounted since it is only used by Windows.

Do I try to use SuperGrub to alter the grub to show Windows? If so, I sure would appreciate specific directions. When I was using it earlier, it didn't seem all that clear to me which option would allow dual boot.

If it makes any difference, this is an Intel Quad Core processor with 4GB of Ram and two 320GB SATA hard drives.

What happened initially was death by assumption and further death by ignorance. First, I did try to install Ubuntu twice, but assumed that the second install would automatically overwrite the first. OOPS. Second, in between installs, I added a second higher capacity DVD drive, and (I think) that made some difference to the BIOS settings as I later had to go in to manually change the boot order so that the drive that I originally installed Windows onto was going to be C drive to Windows and hd0 to Linux. Live and learn.

Thanks very much for all the support and suggestions. I feel like I am now pretty close to getting it all running properly. Couldn't have done it without all of you!

Bud

---

### Post by Hyper Tails on 2008-08-11
> i can't get into windows at all. so i should run the gparted live cd and repeat your steps?

Here 2 choices i would recommend:

1)partition your hardrive and when you were in the setup have you selected grided:use largest continues space

2)reinstall windows  and insert the live cd in windows and select install inside windows. (the prgram that is called wubi. it is an easy ubuntu windows installed and you can also uninstall wubi at anytime. no partitioning needed)

try it :)

---

### Post by buddytd on 2008-08-11
Not sure if this last post by Hyper was an answer meant for me. As I say, my Windows partition is solid and so is my Ubuntu partition. All I need now is a way to boot either OS.

Bud

---

### Post by Victormd on 2008-08-11
> **buddytd said:**
> I then rebooted, hit ESC and the grub menu does NOT show a Windows boot option.

Since you have 2 HDs, there are a few steps you have to take to get Grub to add windows. I believe using supergrub will help, but you might want to take a look at this [link]("http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands"). It's a very nice tutorial that discusses the whole grub+windows scenario.

---

### Post by buddytd on 2008-08-11
Okay, so, feeling brave, I followed the directions in the Super Grub Disk Wiki and added the following to the menu.lst

title           Windows
rootnoverify            (hd0,0)
makeactive
chainloader     +1
boot

I then restarted the machine, pressed ESC and got the full list. BUT when I pressed the Windows option, I got a DISK READ error and was told to restart.

No luck. Open to suggestions as always.

Bud

---

### Post by Victormd on 2008-08-11
Check the link I posted earlier. There are several dual-boot scenarios on multiple HDs and how to solve them...

---

### Post by appi2012 on 2008-08-13
Can you post the output of ```
sudo fdisk -l
```
and also your menu.lst?

---

### Post by sandysandy on 2008-08-13
post output of [COLOR="Blue"]cat /boot/grub/menu.lst[/COLOR]

and also [COLOR="Blue"]sudo fdisk -lu[/COLOR]

regards

---

### Post by buddytd on 2008-08-14
Okay, here are the two screenshots. I'm sure they'll mean more to you than to me. Again, thanks for the assistance.

Bud

---

