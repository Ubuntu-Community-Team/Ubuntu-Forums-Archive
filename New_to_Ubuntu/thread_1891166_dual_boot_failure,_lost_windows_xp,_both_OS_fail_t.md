---
title: "dual boot failure, lost windows xp, both OS fail to boot?"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by monsterbronc on 2011-12-05
I attempted to set up a dual boot system of Xubuntu and Windows XP, I had a book from the library that explaned different ways of doing so,(not on me at the moment) I chose to install Xubuntu on its own drive, so I installed a second hard drive 80GB, and jumped through some hoops to clone my 30GB onto it, it worked perfectly, I tested it and Windows worked fine on the new hard drive. then I set it as the master drive and reinstalled the old 30GB as the slave and installed Xubuntu. The book explained that it would give me the option of where I wanted it, but it didnt, it just installed without asking where I wanted it alongside windows. when it rebooted, windows loaded, and I figuered While I was in there I would check disc management and see where it put Xubuntu.
 
to my surprise it installed dual copies of it, one in the 30GB drve, and one partitioned next to WindowsXP in the 80GB, thats not what I wanted. so I turned off the computer and rebooted, expecting some sort of prompt to decide what OS I want to boot with (the book mentioned this) but it just booted in Xubuntu. so I shut it down again and unhooked the 30GB drive and rebooted, but now it wont boot windowsXP, or Xubuntu, I just get a flashing "_" in the upper left corner after BIOS loads. If I hook up the 30GB drive again, I have a working copy of Xubuntu, but Windows will not load.
 
Is there a way to fix this, or did my windows program crash completely?
And is it possible to go back in through Xubuntu, acess the windows files (if anythings left, "my pictures", and "documents" etc.) and rescue the family pictures and whatnot if windows is in fact no more?
 
Im in a panic, I would hate to loose the pics and a few other files Alot was backed up, but not all of it, I ran out of CDs.
 
I do have a windows XP pro disc for a dell, Can I fix a broken Windows OS with it? will it work in an HP? will I be able to register it?

---

### Post by diablo75 on 2011-12-05
> **monsterbronc said:**
> I attempted to set up a dual boot system of Xubuntu and Windows XP, I had a book from the library that explaned different ways of doing so,(not on me at the moment) I chose to install Xubuntu on its own drive, so I installed a second hard drive 80GB, and jumped through some hoops to clone my 30GB onto it, it worked perfectly, I tested it and Windows worked fine on the new hard drive. then I set it as the master drive
I'm gonna stop you right here to ask a few questions.

First, how did you clone the 30 GB hard drive on to the 80 GB hard drive?  Was some kind of cloning software used?  If so, what was it?

Second, how EXACTLY did you test to make sure the clone worked?  What technique did you use to make sure you weren't actually booting from the 30 GB drive?

Third, how did you test to make sure the clone worked BEFORE setting the 80 GB hard drive to be the master drive?

Fourth, how did you change the drives designations regarding Master and Slave?  Are these SATA drives or PATA/IDE drives with jumpers on them?
> 
...and reinstalled the old 30GB as the slave and installed Xubuntu. The book explained that it would give me the option of where I wanted it, but it didnt, it just installed without asking where I wanted it alongside windows.

Assuming you were running with the 80 GB hard drive as your current master drive which was housing a 30 GB partition that was cloned on to it (leaving about 50 GB free) the default selection of "Alongside Windows XP" would have assumed you wanted to install Xubuntu across the unallocated 50 GB space on the 80 GB drive, completely ignoring the 30 GB drive.  If you wanted something more specific/custom, you should have selected Manual Partitioning during the install.
> 
when it rebooted, windows loaded, and I figuered While I was in there I would check disc management and see where it put Xubuntu.

So after the install and restarting the system rebooted and went directly into Windows with no interaction from you, is that correct?
 > 
to my surprise it installed dual copies of it

No, it didn't.
> 
 one in the 30GB drve, and one partitioned next to WindowsXP in the 80GB, thats not what I wanted. so I turned off the computer and rebooted, expecting some sort of prompt to decide what OS I want to boot with (the book mentioned this) but it just booted in Xubuntu.

You just said that after you finished installing Ubuntu that the system rebooted [directly?] into Windows XP and did not prompt you with a GRUB boot menu.  Now you're saying after one reboot with no further changes made by you that the system is booting into Xubuntu without a GRUB menu.  So which is it?
> 
 so I shut it down again and unhooked the 30GB drive and rebooted, but now it wont boot windowsXP, or Xubuntu, I just get a flashing "_" in the upper left corner after BIOS loads. If I hook up the 30GB drive again, I have a working copy of Xubuntu, but Windows will not load.

What happens if you disconnect the 80 GB drive and set the 30 GB to master?  (I am assuming, by your use of the words "master" and "slave", that your hard drives are PATA/IDE, because with SATA drives you only specify one drive to be primary in the BIOS and everything else requires no explicit assignment.  Also, be sure that if you are switching jumpers around that you aren't accidentally setting the drives into cable select mode and plugging them into the wrong connector on the ribbon cable, because in cable select the connector the drive is attached to determines which is master/slave.  Also you cannot mix CS mode with MA/SL jumper modes between two drives.  Either both have to be in CS or both have to be either a MA or SL drive).
> 
Is there a way to fix this, or did my windows program crash completely?

Hard to say at this point; your Master Boot Record probably needs to be replaced and you can do that with a Windows setup CD and droping into a recovery console to run fixmbr at the prompt, but we don't know that this is the problem just yet.
> 
And is it possible to go back in through Xubuntu, acess the windows files (if anythings left, "my pictures", and "documents" etc.) and rescue the family pictures and whatnot if windows is in fact no more?

If you have access to a working copy of Xubuntu it should be VERY easy to use it to access all partitions on both drives and find your data so you can copy it to an external drive and start over from scratch if nothing else.  Unless you told it to replace Windows during the Install it should not have erased anything that was already there.
 > 
Im in a panic, I would hate to loose the pics and a few other files Alot was backed up, but not all of it, I ran out of CDs.
 
I do have a windows XP pro disc for a dell, Can I fix a broken Windows OS with it? will it work in an HP? will I be able to register it?

You should be able to boot from the disc to get access to a recovery console for minor fixes like fixing the master boot record. 

**Disconnect the 80 GB drive, set the 30 to master and reboot to see what that does.**

Let this experience be a hard lesson learned.  Most might shy away from telling you this, but it's something you need to hear:  When you encounter a problem you've never encountered before, the first thing you **shouldn't** do is try to go at it alone.  You've described a list of events that confused you and rather than stop to ask for directions you plowed forward into the dark without a flashlight.  Next time, stop and ask questions so you don't dig yourself in so deep.  Hang in there, your stuff should be fixable but this will take **_patience_** on your part.  We're here to help.

---

### Post by monsterbronc on 2011-12-06
Ok, sorry, I know just enough about computers to get into trouble like this, Ill answer as best as I can.
 
to clone the drive, I used HD cloner, and I know it worked because after I cloned it (without a partition) I removed the 30gb drive and windows worked perfectly (well, as well as windows can). they are PATA/IDE drives, I set them with the jumpers as noted on the drives for correct designation. I used the 80gb drive with a working copy of windows for about a month with the 30gb on a shelf.
 
as for the first reboot, Yes, it finished install and then said to remove the disc and reboot, so I did, I took out the disk and hit enter for the highlighted "reboot" button, and windows came up. I thought that was weird, and actually wondered it the install was sucsessful, thats why I checked disc manager, and it shows a 30gb partition in the 30gb drive and a 3.9 partition that wasnt there before in the 80gb drive. then I restarted, expecting to see the boot grub, but no, it just loads Xubuntu. the first reboot after install was the one and only time windows loaded, all others booted Xubuntu, with no boot grub. I fiddled around a bit with the jumpers trying different settings, and changing master/ slave settings only tells me I have a crashed hard drive if they are both the same, or in cable select otherwise no difference. the original configuration during the install was master on the 80gb, and slave to the 30gb.
 
If I remove the 80gb drive and boot off the 30gb drive, Xubuntu boots just fine, (with no grub), so I know there is Xubuntu where I want it, but when I remove the 30gb and boot off the 80gb, all I get after BIOS is the blinking"_" in the left corner, It always did that before, but only a second or so before windows started, now its stuck there or something, so I think I didnt toast windows, but I broke a command or something. 
 
AS for acess to my stuff, if I boot with both drives installed, it boots Xubuntu, and my 80gb drive shows up on desktop, and (this is a major reilef) I CAN acess it, and it appears everything is there, in fact I was able to extract a copy of my entire (12gb) "my documents" folder and all my pics and whatnot open just fine in Xubuntu. So I think windows xp IS ok, but its got a file or something out of whack, and Im not in a panic anymore. 
 
I really appreciate your advice, and I admit, I kinda dove in head first, but we do learn from our mistakes. I wuold like to continue with the dual boot Idea, but if windows is a goner, at least my files are ok, and Xubuntu works.
 
Im curious as to why there is a 3.9gb partition on the 80gb drive, I assumed it was another copy of Xubuntu, I know it was NOT there before. I wonder if it thought I was installing on multiple computers?

---

### Post by kansasnoob on 2011-12-06
With both drives connected please download and run the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then post the full RESULTS.txt here.

I'd bet we can salvage this fairly easily.

---

### Post by monsterbronc on 2011-12-06
Ill give it a try,but im still in the buntu learning curve.

 A friend of mine seems to think its not windows thats messed up, but a problem with GRUB loader, since it doesnt seem to be there.

---

### Post by Bartender on 2011-12-06
> **monsterbronc said:**
> Im in a panic, I would hate to loose the pics and a few other files Alot was backed up, but not all of it, I ran out of CDs.
 
I do have a windows XP pro disc for a dell, Can I fix a broken Windows OS with it? will it work in an HP? will I be able to register it?

I know the feeling.  First thing: don't make it any worse.  Windows is still on the 80GB disc, right?  Even if it won't boot, you can still get to your data.  Pull that 80 GB HDD out of the system entirely so no more damage can be done.  Set up the 30GB as master, install Xubuntu.  When that's done, turn the PC off, unplug it, and install the 80GB as a slave on the same data cable or on the second data cable.  When you boot into Xubuntu, you'll be able to access your personal data within Windows and save it to the 30 GB, or an external HDD, or an external USB thumb drive, or whatever you can come up with.

Once that's done, you know that at the very worst you at least have your pictures, music, docs, etc.

AFAIK a Dell recovery disc isn't going to work on an HP.  

Look into [gparted]("http://gparted.sourceforge.net/download.php")  A gparted bootable CD is the single handiest tool I know of for partitioning, etc.  It's not going to solve your immediate problem (broken Windows installation) but a great tool for your next project.

---

### Post by diablo75 on 2011-12-06
> **Bartender said:**
> 

AFAIK a Dell recovery disc isn't going to work on an HP.  



He won't be able to reinstall the OS with it but it will let him drop to a recovery console to execute simple DOS commands; **fixboot** and **fixmbr** being the two most relevant in this case.

---

### Post by critin on 2011-12-06
> **diablo75 said:**
> 

Let this experience be a hard lesson learned.  Most might shy away from telling you this, but it's something you need to hear:  When you encounter a problem you've never encountered before, the first thing you **shouldn't** do is try to go at it alone.  You've described a list of events that confused you and rather than stop to ask for directions you plowed forward into the dark without a flashlight.  Next time, stop and ask questions so you don't dig yourself in so deep.  Hang in there, your stuff should be fixable but this will take **_patience_** on your part.  We're here to help.

:KS   Well said, *diablo75  *

---

### Post by monsterbronc on 2011-12-07
> **Bartender said:**
> I know the feeling. First thing: don't make it any worse. Windows is still on the 80GB disc, right? Even if it won't boot, you can still get to your data. Pull that 80 GB HDD out of the system entirely so no more damage can be done. Set up the 30GB as master, install Xubuntu. When that's done, turn the PC off, unplug it, and install the 80GB as a slave on the same data cable or on the second data cable. When you boot into Xubuntu, you'll be able to access your personal data within Windows and save it to the 30 GB, or an external HDD, or an external USB thumb drive, or whatever you can come up with.
 
Once that's done, you know that at the very worst you at least have your pictures, music, docs, etc.
 
Ive done that, and yes thankfully all my stuff is still there, as far as I can tell all of windows is too, but its a boot problem.
 
Im at work now, and I didnt get much time to mess with it yesterday, but I did try to use the Dell disc to try and fix windows, but its got a scratch and wont load, it tries to load then says HARD ERROR and stops there, and the recovery utility asks me to insert a boot floppy (do floppies exist anymore?) so Im gonna try [[COLOR=#000000]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/") and see what I get. and ill see if any of my buddies have a windows disc that might work, or I might be able to clean up that disc.
 
If I can, I might just wipe out windows, and start over (if I can find a windows disc that works) and just reinstall everything all over again, do a fresh windows install, then since I already copied all my stuff from the original drive, reinstall it all and then set up the dual boot the way It was supposed to be, and if it boogers up again, its all backed up this time.

---

### Post by Mark Phelps on 2011-12-07
If XP is still there but you're just having boot problems with it, then try using Boot-Repair to fix it:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by kansasnoob on 2011-12-07
> **monsterbronc said:**
> Ive done that, and yes thankfully all my stuff is still there, as far as I can tell all of windows is too, but its a boot problem.
 
Im at work now, and I didnt get much time to mess with it yesterday, but I did try to use the Dell disc to try and fix windows, but its got a scratch and wont load, it tries to load then says HARD ERROR and stops there, and the recovery utility asks me to insert a boot floppy (do floppies exist anymore?) so Im gonna try [[COLOR=#000000]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/") and see what I get. and ill see if any of my buddies have a windows disc that might work, or I might be able to clean up that disc.
 
If I can, I might just wipe out windows, and start over (if I can find a windows disc that works) and just reinstall everything all over again, do a fresh windows install, then since I already copied all my stuff from the original drive, reinstall it all and then set up the dual boot the way It was supposed to be, and if it boogers up again, its all backed up this time.

DO NOT wipe out Windows!

That would be pointless!

We need to see the RESULTS.txt from the Boot Info Script to determine what is wrong. If you have trouble figuring out how to use it just say so.

In fact, if you're having trouble understanding how to run the Boot Info Script, have you at least found the terminal in Xubuntu?

If so please post the output of these commands:

```
lsb_release -a
```

```
sudo parted -l
```

That will provide me with a starting point :)

I can assure you that this is likely very easy to fix :D

---

### Post by monsterbronc on 2011-12-08
> **kansasnoob said:**
> DO NOT wipe out Windows!

That would be pointless!

We need to see the RESULTS.txt from the Boot Info Script to determine what is wrong. If you have trouble figuring out how to use it just say so.

In fact, if you're having trouble understanding how to run the Boot Info Script, have you at least found the terminal in Xubuntu?

If so please post the output of these commands:

```
lsb_release -a
``````
sudo parted -l
```That will provide me with a starting point :)

I can assure you that this is likely very easy to fix :D

Yes I am having trouble with the boot info script, I downloaded it, unzipped it and put it on desktop, but now I have no idea what to do with it. I poked around in it, and it just appears to me as a word document of sorts. Do I copy and paste it to terminal? I have found terminal, and have done a few things there, but mostly unsuccessfully, (Ive been trying to install wine in another desktop, and it wont install, keeps coming up with some other program not installed, whole other issue) Bear in mind, I am not online with Ubuntu yet, all internet activity is either from my Windows laptop, or Windows computers at work and the library. But Im working on it, for now everything has to be transferred via flashdrive. Ill go try those commands, ans post back.

---

### Post by monsterbronc on 2011-12-08
Code:
 	lsb_release -a 
 	Code:
 	sudo parted -l 
Both of these come up as "command not found"

And when it does do what its supposed to do, How do I get copy and paste to work? I thought copy was Ctrl+c, and paste was Ctrl+alt+v? but apperently Im wrong. Obviously Im a Ex-Windows user.

---

### Post by monsterbronc on 2011-12-08
> **Mark Phelps said:**
> If XP is still there but you're just having boot problems with it, then try using Boot-Repair to fix it:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This will have to wait, ill download it at work, my sad dialup would never get 300+mb. it usually drops my connection after 10mb (im convinced netzero does it on purpose)

Boot_info_script isnt working at all, I followed the directions exactly from source forge, it is unzipped, and sitting in a directory on my desktop, but when I type what it says, the response is "no such file or directory", Ill try it with the older version.

---

### Post by kansasnoob on 2011-12-08
> **monsterbronc said:**
> Code:
 	lsb_release -a 
 	Code:
 	sudo parted -l 
Both of these come up as "command not found"

And when it does do what its supposed to do, How do I get copy and paste to work? I thought copy was Ctrl+c, and paste was Ctrl+alt+v? but apperently Im wrong. Obviously Im a Ex-Windows user.

I haven't used Xubuntu in quite some time, only Ubuntu and Lubuntu, so I'm dieing to know what version of Xubuntu you installed. 

Was this a CD included with the book you read?

Or was this something you downloaded and burned to disc?

I explained a bit about "copy-n-paste" here:

[http://ubuntuforums.org/showpost.php?p=11459388&postcount=160](http://ubuntuforums.org/showpost.php?p=11459388&postcount=160)

Seriously you need to learn how to run those two simple commands before we consider the Boot Info Script. Trust me, you'll laugh at yourself once you figure this out :)

When I started I couldn't even find the terminal :D

---

### Post by monsterbronc on 2011-12-08
Ha, Got It.

In the directions it said to use "sudo bash ~/ bla bla bla

if I removed the ~/ it worked, Here it is.................................


                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for oh.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for cd.
 => No boot loader is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *     11,718,000   156,248,189   144,530,190   7 HPFS/NTFS
/dev/sda2               2,046    11,716,607    11,714,562   5 Extended
/dev/sda5               2,048     7,540,735     7,538,688  83 Linux
/dev/sda6           7,542,784    11,716,607     4,173,824  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    73,988,095    73,986,048  83 Linux
/dev/sdb2          73,990,142    78,163,967     4,173,826   5 Extended
/dev/sdb5          73,990,144    78,163,967     4,173,824  82 Linux swap / Solaris


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1054 MB, 1054343168 bytes
2 heads, 63 sectors/track, 16343 cylinders, total 2059264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             32     2,059,263     2,059,232   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BA0BB982CC314718                       ntfs       HP_PAVILION                   
/dev/sda2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="2" 
/dev/sda5        f74d0b08-09ae-45fb-b00b-f5e8a4a63073   ext4                                     
/dev/sda6        41dbc077-0048-4fd0-b745-1450421cc254   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4e9d5bac-2bfd-4caa-86ed-51fc3febb722   ext4                                     
/dev/sdb2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="2" 
/dev/sdb5        260c8701-b89e-4d63-8383-48623ddb3589   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        00C3-94F8                              vfat       KEYFOB III                    
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdg1        /media/KEYFOB III        vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f74d0b08-09ae-45fb-b00b-f5e8a4a63073 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=41dbc077-0048-4fd0-b745-1450421cc254 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


   6.8GB: initrd.img

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 4e9d5bac-2bfd-4caa-86ed-51fc3febb722
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 4e9d5bac-2bfd-4caa-86ed-51fc3febb722
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 4e9d5bac-2bfd-4caa-86ed-51fc3febb722
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=4e9d5bac-2bfd-4caa-86ed-51fc3febb722 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 4e9d5bac-2bfd-4caa-86ed-51fc3febb722
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=4e9d5bac-2bfd-4caa-86ed-51fc3febb722 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 4e9d5bac-2bfd-4caa-86ed-51fc3febb722
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 4e9d5bac-2bfd-4caa-86ed-51fc3febb722
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root BA0BB982CC314718
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4e9d5bac-2bfd-4caa-86ed-51fc3febb722 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=260c8701-b89e-4d63-8383-48623ddb3589 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   9.1GB: boot/grub/core.img
   6.5GB: boot/grub/grub.cfg
   6.8GB: boot/initrd.img-3.0.0-12-generic
  34.4GB: boot/vmlinuz-3.0.0-12-generic
   6.8GB: initrd.img
  34.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  81 cf 03 00 82 cf 03 00  83 cf 03 00 84 cf 03 00  |................|
00000010  85 cf 03 00 86 cf 03 00  87 cf 03 00 88 cf 03 00  |................|
00000020  89 cf 03 00 8a cf 03 00  8b cf 03 00 8c cf 03 00  |................|
00000030  8d cf 03 00 8e cf 03 00  8f cf 03 00 90 cf 03 00  |................|
00000040  91 cf 03 00 92 cf 03 00  93 cf 03 00 94 cf 03 00  |................|
00000050  95 cf 03 00 96 cf 03 00  97 cf 03 00 98 cf 03 00  |................|
00000060  99 cf 03 00 9a cf 03 00  9b cf 03 00 9c cf 03 00  |................|
00000070  9d cf 03 00 9e cf 03 00  9f cf 03 00 a0 cf 03 00  |................|
00000080  a1 cf 03 00 a2 cf 03 00  a3 cf 03 00 a4 cf 03 00  |................|
00000090  a5 cf 03 00 a6 cf 03 00  a7 cf 03 00 a8 cf 03 00  |................|
000000a0  a9 cf 03 00 aa cf 03 00  ab cf 03 00 ac cf 03 00  |................|
000000b0  ad cf 03 00 ae cf 03 00  af cf 03 00 b0 cf 03 00  |................|
000000c0  b1 cf 03 00 b2 cf 03 00  b3 cf 03 00 b4 cf 03 00  |................|
000000d0  b5 cf 03 00 b6 cf 03 00  b7 cf 03 00 b8 cf 03 00  |................|
000000e0  b9 cf 03 00 ba cf 03 00  bb cf 03 00 bc cf 03 00  |................|
000000f0  bd cf 03 00 be cf 03 00  bf cf 03 00 c0 cf 03 00  |................|
00000100  c1 cf 03 00 c2 cf 03 00  c3 cf 03 00 c4 cf 03 00  |................|
00000110  c5 cf 03 00 c6 cf 03 00  c7 cf 03 00 c8 cf 03 00  |................|
00000120  c9 cf 03 00 ca cf 03 00  cb cf 03 00 cc cf 03 00  |................|
00000130  cd cf 03 00 ce cf 03 00  cf cf 03 00 d0 cf 03 00  |................|
00000140  d1 cf 03 00 d2 cf 03 00  d3 cf 03 00 d4 cf 03 00  |................|
00000150  d5 cf 03 00 d6 cf 03 00  d7 cf 03 00 d8 cf 03 00  |................|
00000160  d9 cf 03 00 da cf 03 00  db cf 03 00 dc cf 03 00  |................|
00000170  dd cf 03 00 de cf 03 00  df cf 03 00 e0 cf 03 00  |................|
00000180  e1 cf 03 00 e2 cf 03 00  e3 cf 03 00 e4 cf 03 00  |................|
00000190  e5 cf 03 00 e6 cf 03 00  e7 cf 03 00 e8 cf 03 00  |................|
000001a0  e9 cf 03 00 ea cf 03 00  eb cf 03 00 ec cf 03 00  |................|
000001b0  ed cf 03 00 ee cf 03 00  ef cf 03 00 f0 cf 00 20  |............... |
000001c0  21 00 83 63 4e d5 02 00  00 00 00 08 73 00 00 63  |!..cN.......s..c|
000001d0  4f d5 05 52 b9 d9 02 08  73 00 00 b8 3f 00 00 00  |O..R....s...?...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  fc ee b6 d2 1b a4 5c c8  2c ca 76 21 b8 67 a0 9a  |......\.,.v!.g..|
00000010  a6 84 ca 59 9a 9e e0 8e  c3 81 84 3e bf 38 18 5e  |...Y.......>.8.^|
00000020  46 b1 13 7b a3 68 17 b9  06 f4 03 23 90 8c 83 46  |F..{.h.....#...F|
00000030  42 c0 5b 5e 2b 73 4b cb  73 3e b4 65 4f e2 8a 0b  |B.[^+sK.s>.eO...|
00000040  8f a7 d5 e7 01 71 b2 6b  64 9c 12 e0 5f 6e f4 b3  |.....q.kd..._n..|
00000050  f9 c1 60 0d 8b 55 4f 45  96 93 35 1b b7 aa e0 59  |..`..UOE..5....Y|
00000060  e4 e7 dd b8 91 c7 a0 bd  fb 12 b7 83 2f 22 b6 f8  |............/"..|
00000070  80 54 b4 23 3f 31 7d 5a  a9 f7 bb 66 cf 33 f7 24  |.T.#?1}Z...f.3.$|
00000080  64 8a dc 6c 2f cb 12 e5  75 23 b2 82 7f 5d 59 b2  |d..l/...u#...]Y.|
00000090  72 3d 77 85 ae f6 fc d4  99 a8 d7 5c 9b 8d 4d 87  |r=w........\..M.|
000000a0  ba 7f a5 e6 59 13 7b 7f  ec 86 84 da 0e fe 5c a5  |....Y.{.......\.|
000000b0  78 da ba 18 c7 58 5c 23  4e cd c6 24 38 e1 9a 1b  |x....X\#N..$8...|
000000c0  fd ed 28 2e 36 68 0a 41  86 0c 86 02 27 1c 6a cd  |..(.6h.A....'.j.|
000000d0  79 16 85 4f 21 40 35 6c  99 e0 bc 16 89 bb 0c 27  |y..O!@5l.......'|
000000e0  66 47 bf 42 8d 85 cd 84  8a 11 39 7c c8 93 12 c0  |fG.B......9|....|
000000f0  e5 e8 a0 cb 54 62 65 33  80 28 b9 3e 73 bd 8b 51  |....Tbe3.(.>s..Q|
00000100  ba e1 62 be 1b 2a 9a f6  9b 11 1c 68 d9 d8 82 5d  |..b..*.....h...]|
00000110  40 a4 17 cf 92 18 10 8b  01 38 b3 6f 22 8e bf 52  |@........8.o"..R|
00000120  cf 90 26 e8 8c 69 8e 7c  8c 2f fb 7f a7 91 01 54  |..&..i.|./.....T|
00000130  b8 1e 90 5e 12 fb 72 73  92 b7 27 e7 83 5b 3c f5  |...^..rs..'..[<.|
00000140  61 50 5a ad da f1 34 50  2b 30 d7 7c 89 03 1b 56  |aPZ...4P+0.|...V|
00000150  78 09 57 e7 d2 b8 40 97  5f cb 69 18 1a 6d df 8a  |x.W...@._.i..m..|
00000160  de 71 cd 18 2b 7e 00 ab  fe c3 3e 36 6f 81 85 0e  |.q..+~....>6o...|
00000170  7c 63 02 ba 4a d1 24 94  a7 3f 1f 45 0c 06 f0 5d  ||c..J.$..?.E...]|
00000180  3e a2 34 29 d5 5a c3 2b  a6 7a 95 c4 b9 c9 68 0c  |>.4).Z.+.z....h.|
00000190  3c 7e 58 7a 5b d4 39 2f  0d 10 43 6a 0a 0c 6c cf  |<~Xz[.9/..Cj..l.|
000001a0  7b fa 3f f2 e3 d2 b6 16  99 67 b9 53 c0 89 40 a9  |{.?......g.S..@.|
000001b0  04 0d fa a9 af a9 dc 96  36 e5 ff 79 95 8e 00 fe  |........6..y....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 3f 00 00 00  |............?...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

---

### Post by monsterbronc on 2011-12-08
> **kansasnoob said:**
> I haven't used Xubuntu in quite some time, only Ubuntu and Lubuntu, so I'm dieing to know what version of Xubuntu you installed. 

Was this a CD included with the book you read?

Or was this something you downloaded and burned to disc?

I explained a bit about "copy-n-paste" here:

[http://ubuntuforums.org/showpost.php?p=11459388&postcount=160](http://ubuntuforums.org/showpost.php?p=11459388&postcount=160)

Seriously you need to learn how to run those two simple commands before we consider the Boot Info Script. Trust me, you'll laugh at yourself once you figure this out :)

When I started I couldn't even find the terminal :D

I got Xubuntu 11.10 mailed to me through Ubuntu, via on-disc.com, and I checked a book out from the library, but the library book did come with a cd, it was fiesty fawn, but my BIL tried ubuntu from a book, and had problems, thats why I went to the Ubuntu site and ordered the disks. I guess it was a bit outdated.

---

### Post by kansasnoob on 2011-12-08
I'm foggy eyed sleepy so give me time :)

---

### Post by monsterbronc on 2011-12-08
> **kansasnoob said:**
> I'm foggy eyed sleepy so give me time :)
take all the time you need, I dont expect it fixed tonight. I myself work the Vampire shift so I know all about "foggy eyed sleepy"

I looked through the results, and see a couple errors listed, but to be honest, I just as well be trying to read Mandarin or something, for all I know, its normal.

Funny, I swear its a 30gb drive, but this lists it as a 40gb, windows always showed it as 3100-ish Mb's so where did the other 9 gigs come from?

---

### Post by kansasnoob on 2011-12-09
I asked for some help with this because it appears that XP does not start in the proper sector of the hard drive ...... but I'm not sure.

I also don't see how you ended up with two copies of Xubuntu, maybe due to this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

So let's see if oldfred has some thoughts :)

---

### Post by oldfred on 2011-12-09
Added code tags to make script easier to read. From full/advanced edit edit panel at top right is # which will add code tags around highlighted "code". Makes it easier to review & preserves some formating.

How did you get boot script version 55, the default download is now 60.
#!/bin/bash
VERSION='0.60';
RELEASE_DATE='17 May 2011';

But that should not make any real difference.

You have swapped drives and as I understand you have IDE drives. I need to understand if your BIOS lets you choose which drive to boot, and are you correctly setting master/slave jumpers or are you using cable select with jumpers set to cable select? 

One install of grub looks like it may work and the other not. Windows looks ok, but that does not guarantee it boots. Sometimes boot sector repair or chkdsk is needed. You do have a strange sda1 as it is sda1 but is at the end of the drive after the extended partition. Windows does need primary partition which it is, but did the install move it somehow, if so, then a fixBoot and chkdsk may be required. NTFS partition boot sector has info in it that has to match partition table or location of partition on drive, if it gets moved then repairs are required.

You should be able to use any XP install disk, or any Windows install to run chkdsk and reinstall a boot sector. I have used a Windows 7 repair USB to fix my XP. Commands are different depending.

[http://support.microsoft.com/kb/310994](http://support.microsoft.com/kb/310994)

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #[COLOR=Red]do not run[/COLOR] if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

---

### Post by monsterbronc on 2011-12-10
I GOT XP TO BOOT!
 
I was having some other strange issues with Xubuntu, it keeps loosing my settings, when I reboot, it looses my background picture, and wipes out my color schemes, it basically goes back to default, but not always, or completely, sometimes it would keep my scheme and loose the desktop background, or it would keep that and change my appearences. or both. that and I have no sound.(thats probobly just a quick fix) Its also doing strange things with Hibernate and sleep, sometimes it goes to screen saver, and other times it locks up instead of sleep, and It will not hibernate, it turns off the monitor and always freezes up, the cpu, or tower stays running and nothing will wake it up, I have to turn it off and reboot. but when left alone, it seems to have no trouble going to sleep on its own, only when I tell it too.
 
So I reinstalled Xubuntu in the 30gb drive, and when it rebooted, I GOT GRUB!:P but it shows 2 Ubuntu 11.10's:confused: then a couple tests, and at the bottom is Windows XP home edition. and if I select it, it boots just as it did before this snafu.
 
I havent had time to see if my hibernate or setting issues have cleared up, but if there is a sound Xubuntu makes at startup, its not working.
 
I went back in through windows, and sure enough there is a partition on the master drive next to windows that wasnt there before, and when I startup in Xubuntu its listed just under my windows drive on the desktop as 3.9 file system, and it appears to be program files, it looks like a carbon copy of file system. so if it is a second Xubuntu OS, how would I go about getting rid of it? without hurting Windows again, and could that be the strange sda1 you were talking about?
 
I havent tried booting the second Ubuntu, so Im not sure what happens there, if it is a second ubuntu, should I wipe the 30gb drive and just use it as storage, and run both OS's off the 80gb drive? also how would I go about that without hurting Windows, or grub?
 
I ended up with the boot-info-script055 because I couldnt get 060 to work, so I tried the older version, then I figured out the problem with the ~/ symbols, I have them both, 060 will probobly work fine, its just that I was messing with 055 when I figured it out.
 
I thank you all very much for your patience with a noob.

---

### Post by mastablasta on 2011-12-10
cpuld it be possibel if oyu created first one via Wubi there is a left over there. can you see anyhtign in windows control panel-->add/remove programms?

---

### Post by monsterbronc on 2011-12-10
My bios does let me choose what drive to boot off of, and they are set to slave and master, the one with windows is the master.
 
Whats Wubi? I have it on a flashdrive but never installed it, what does it do, and is it neccessary?
 
I skimmed through that bug, and it does seem like that may actually be part of my problem, it didnt ask where I wanted it, it just installed alongside, and after it started I freaked out, I contemplated turning off the machine but was afraid it would really mess something up. I see the similarity where they tested it with a flashdrive plugged in, where I had a second drive plugged in, I wonder had i a flashdrive plugged in would it have made a third install on it?

---

### Post by kansasnoob on 2011-12-10
> **monsterbronc said:**
> I GOT XP TO BOOT!
 
I was having some other strange issues with Xubuntu, it keeps loosing my settings, when I reboot, it looses my background picture, and wipes out my color schemes, it basically goes back to default, but not always, or completely, sometimes it would keep my scheme and loose the desktop background, or it would keep that and change my appearences. or both. that and I have no sound.(thats probobly just a quick fix) Its also doing strange things with Hibernate and sleep, sometimes it goes to screen saver, and other times it locks up instead of sleep, and It will not hibernate, it turns off the monitor and always freezes up, the cpu, or tower stays running and nothing will wake it up, I have to turn it off and reboot. but when left alone, it seems to have no trouble going to sleep on its own, only when I tell it too.
 
So I reinstalled Xubuntu in the 30gb drive, and when it rebooted, I GOT GRUB!:P but it shows 2 Ubuntu 11.10's:confused: then a couple tests, and at the bottom is Windows XP home edition. and if I select it, it boots just as it did before this snafu.
 
I havent had time to see if my hibernate or setting issues have cleared up, but if there is a sound Xubuntu makes at startup, its not working.
 
I went back in through windows, and sure enough there is a partition on the master drive next to windows that wasnt there before, and when I startup in Xubuntu its listed just under my windows drive on the desktop as 3.9 file system, and it appears to be program files, it looks like a carbon copy of file system. so if it is a second Xubuntu OS, how would I go about getting rid of it? without hurting Windows again, and could that be the strange sda1 you were talking about?
 
I havent tried booting the second Ubuntu, so Im not sure what happens there, if it is a second ubuntu, should I wipe the 30gb drive and just use it as storage, and run both OS's off the 80gb drive? also how would I go about that without hurting Windows, or grub?
 
I ended up with the boot-info-script055 because I couldnt get 060 to work, so I tried the older version, then I figured out the problem with the ~/ symbols, I have them both, 060 will probobly work fine, its just that I was messing with 055 when I figured it out.
 
I thank you all very much for your patience with a noob.

I'd personally like to see the output of this command before going any further:

```
sudo parted -l
```

But, **lets slow down and have an important discussion!**

You used software I don't understand to copy Windows to the new 80GB drive. That's fine, and it worked so that makes it great :)

But, **it's almost always a very bad idea to move the "front-end" of any Windows OS partition!**

So, it looks like you ended up with a copy of Xubuntu in the wrong place, and I'd suspect it won't boot anyway. I strongly suspect it's due to this bug (that I filed):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/766265)

So, if copying your Win XP to the new drive left free space at the beginning of the drive, Ubuntu/Xubuntu tried to use that space but somehow failed.

Then I suspect you tried to install again and got the working Xubuntu on the 30GB drive. Does that make sense?

Now, there's a reason for my request of the output of "parted -l". It's more human readable. I have a very complex partitioning arrangement - look:

[ATTACH]208847[/ATTACH]

[ATTACH]208848[/ATTACH] 

And look at the outputs of both fdisk and parted:

```
lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6391

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    84646484    42323211   83  Linux
/dev/sda2        84646485   168313004    41833260   83  Linux
/dev/sda3       168313005   252349019    42018007+  83  Linux
/dev/sda4       252350462   976768064   362208801+   5  Extended
/dev/sda5       631209978   730464255    49627139   83  Linux
/dev/sda6       738861543   843637409    52387933+  83  Linux
/dev/sda7       843637473   950919479    53641003+  83  Linux
/dev/sda8       950919543   971852174    10466316   83  Linux
/dev/sda9       971852238   976768064     2457913+  82  Linux swap / Solaris
/dev/sda10      588637728   631209914    21286093+  83  Linux
/dev/sda11      546161868   588637664    21237898+  83  Linux
/dev/sda12      503878788   546161804    21141508+  83  Linux
/dev/sda13      460904913   503878724    21486906   83  Linux
/dev/sda14      295001721   336144059    20571169+  83  Linux
/dev/sda15      336144123   377318654    20587266   83  Linux
/dev/sda16      377318718   419119784    20900533+  83  Linux
/dev/sda17      419119848   460904849    20892501   83  Linux
/dev/sda18      252350464   295000063    21324800   83  Linux
/dev/sda19      730466304   736731135     3132416    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000424d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   152127487    76062720   83  Linux
/dev/sdb2       152129534   156301311     2085889    5  Extended
/dev/sdb5       152129536   156301311     2085888   82  Linux swap / Solaris

```

```
lance@lance-desktop:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  43.3GB  43.3GB  primary   ext4            boot
 2      43.3GB  86.2GB  42.8GB  primary   ext3
 3      86.2GB  129GB   43.0GB  primary   ext3
 4      129GB   500GB   371GB   extended
18      129GB   151GB   21.8GB  logical   ext4
14      151GB   172GB   21.1GB  logical   ext3
15      172GB   193GB   21.1GB  logical   ext4
16      193GB   215GB   21.4GB  logical   ext4
17      215GB   236GB   21.4GB  logical   ext4
13      236GB   258GB   22.0GB  logical   ext4
12      258GB   280GB   21.6GB  logical   ext4
11      280GB   301GB   21.7GB  logical   ext4
10      301GB   323GB   21.8GB  logical   ext4
 5      323GB   374GB   50.8GB  logical   ext3
19      374GB   377GB   3208MB  logical   fat32
 6      378GB   432GB   53.6GB  logical   ext3
 7      432GB   487GB   54.9GB  logical   ext3
 8      487GB   498GB   10.7GB  logical   ext3
 9      498GB   500GB   2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800JB-00JJ (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  77.9GB  77.9GB  primary   ext4
 2      77.9GB  80.0GB  2136MB  extended
 5      77.9GB  80.0GB  2136MB  logical   linux-swap(v1)


```

So, give me the output of:

```
sudo parted -l
```

Then we can go from there :D

---

### Post by kansasnoob on 2011-12-10
> **mastablasta said:**
> cpuld it be possibel if oyu created first one via Wubi there is a left over there. can you see anyhtign in windows control panel-->add/remove programms?

The BIS shows no WUBI files at all, don't make things worse, PLEASE!

---

### Post by monsterbronc on 2011-12-11
Untill I know what wubi is, theres no way im useing it,
 
Will that command give me a window like your screenshots, or just code?
either way, how do I copy/paste to a flashdrive to post results here via computer with working internet since I dont have Xubuntu online yet?
 
Ive tried to copy and paste in terminal, and have had no luck.
 
Im on vacation this week, so Ill have a bit of free time to fiddle with this,(not a whole lot, but more than I have had)
 
>  
Then I suspect you tried to install again and got the working Xubuntu on the 30GB drive. Does that make sense?



 
that does make sense, but I only installed once, untill recently, when I reinstalled over the top of Ubuntu in the 30gb drive. truthfully, I don't really care where Xubuntu is, as long as it works right, and I havent got my free memory all boogered up. I originally wanted just Windows XP on the 80GB drive, and Linux Xubuntu on the 30Gb drive that way each system had its own territory, so to speak. But I am willing to change that if you guys have a more efficient/better way to do it.

---

### Post by oldfred on 2011-12-11
Wubi is a version of Ubuntu that installs inside Windows. It is like an extended test like the liveCD but allows updates. It requires no partitioning, but as a file inside the Windows NTFS partition will suffer also if Windows gets corrupted. If willing to partition then a full install is better.

Keeping Windows on one drive & Ubuntu on the other is my preferred way to install. It avoids many issues, but with many IDE drives only boot the primary master, so in those cases you cannot have total separation. 

Can you boot with liveCD on system. That way you can copy & paste from liveCD when running from liveCD.

If you want lots of detail on dual drive install. Some new users may think this is too complex only because Herman has so much extra info and links. Installs to external drives or second drives are really the same, but need somewhat different instructions than an install to the same drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

---

### Post by monsterbronc on 2011-12-12
here is a weird attempt at posting the results, MS Word wasnt too keen on deciphering Abiword :P 

I found it deciphers leafpad much better.






  monsterbronc@DeepThoughtII:~$ sudo parted -l
[sudo] password for monsterbronc: 
Model: ATA Maxtor 6Y080L0 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End      Size       Type      File system     Flags
 2      1048kB  5999MB  5998MB  extended
 5      1049kB  3861MB  3860MB  logical   ext4
 6      3862MB  5999MB  2137MB  logical   linux-swap(v1)
 1      6000MB  80.0GB  74.0GB  primary   ntfs            boot


Model: ATA ST340015A (scsi)
Disk /dev/sdb: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End      Size      Type      File system     Flags
 1      1049kB  37.9GB  37.9GB  primary   ext4            boot
 2      37.9GB  40.0GB  2137MB  extended
 5      37.9GB  40.0GB  2137MB  logical   linux-swap(v1)


monsterbronc@DeepThoughtII:~$

---

