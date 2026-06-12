---
title: "Have I lost Windows after Ubuntu install?"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by WB0HYQ on 2013-05-30
I was unable to use a newly created 12.04.2 DVD (it won't boot) and used my old 11.10 install DVD to set up a dual-boot installation to co-exist with Windows 7 (64-bit).  The installation began and I set up a new partition on an external HD of 1.5Tb for Ubuntu.  After it all installed, I was asked to remove the DVD and reboot.  When it came back up, all I got was a black screen with the following:

error: no such device 08262888-f69c-4d8d-ac57-c6ac1445dbc5
grub rescue>

That's it.  Further attempts to reboot using F11 to select which device I boot from produces the same results.  Have I managed to mess up Windows, or is there a way back from the monumental mistake in judgement on my part?

What do I tell this 'grub' person so that I can get my Windows back?

Bill

---

### Post by VMC on 2013-05-30
I doubt you lost your Windows install. The question is do you want to install Ubuntu along side of Windows or just remove it and have Windows boot only.

---

### Post by presence1960 on 2013-05-30
Boot from the Ubuntu Live CD. When the desktop loads open a terminal and run
> sudo apt-get install lilo
Ignore the warning and continue. When finished run in terminal
> sudo lilo -M /dev/sda mbr

Reboot without Live CD and you will boot right to windows. You said you wanted windows back. This will set your MBR to windows. Currently GRUB is on MBR.

---

### Post by WB0HYQ on 2013-05-30
Ah.  Two good answers.

@VMC: I would like to keep both installations if possible, but failing that, I'll opt for Windows because it has a lot of my development stuff on it.  

@presence1960: I am assuming that the live CD you mention is the one I originally booted from, but just tell it to use it on the CD instead of installing.  Correct?
And, "open a terminal" how?

Bill

---

### Post by presence1960 on 2013-05-30
> **WB0HYQ said:**
> Ah.  Two good answers.

@VMC: I would like to keep both installations if possible, but failing that, I'll opt for Windows because it has a lot of my development stuff on it.  

@presence1960: I am assuming that the live CD you mention is the one I originally booted from, but just tell it to use it on the CD instead of installing.  Correct?
And, "open a terminal" how?

Bill

Don't install when you boot the CD. When the desktop loads open a terminal and run the commands.

If you want to keep both do what I suggest without the external plugged in. Then you need to install GRUB on MBR of sdb (external, if yours is sdb) This will do two things. When your external is unplugged you boot right to windows. When your external is plugged in and it is set as first boot device you get the GRUB menu and can boot ubuntu. If you want to go this route post back and we'll get you started.

---

### Post by presence1960 on 2013-05-30
> **WB0HYQ said:**
> 
And, "open a terminal" how?

Bill
 click the top dash of the unity bar and type in terminal and it will display for you.

---

### Post by WB0HYQ on 2013-05-30
Got Windows back.  That's a relief.

I would still like to keep Ubuntu and am ready to tackle the MBR alteration to do so.  My External HD is plugging in all the time because it is kind of difficult to reach.  That means that I'll have to go the MBR alteration.

As you have gathered, I am really a nebbish at LINUX, but I've been with Windows for years and years (even before there were Windows).

I remembered from foggy recesses about the Crtl-Alt-F2 and F7 for a full-screen terminal and did it that way.

EDIT:  Now that I think about it, I may have not installed the correct version of Ubuntu after all.  The machine is a 64-bit machine and I installed the 32-bit version of 11.10.  Will that make a difference?  Should I just go ahead and download the 64-bit version of 11.10 anyway and re-install it?

Bill

---

### Post by presence1960 on 2013-05-30
To keep each installation's bootloader untouched and on it's own MBR is the goal. You already have windows MBR set up. Now you want to put GRUB on the external disk's MBR, How many disks do you have? I will assume one internal and the external, let me know before we proceed.

---

### Post by presence1960 on 2013-05-30
> **WB0HYQ said:**
> .

EDIT:  Now that I think about it, I may have not installed the correct version of Ubuntu after all.  The machine is a 64-bit machine and I installed the 32-bit version of 11.10.  Will that make a difference?  Should I just go ahead and download the 64-bit version of 11.10 anyway and re-install it?

Bill

If you have more thasn 4GB od RAM I would go with the 64 bit as 32 bit only sees and makes use of a little less than 4GB. I would go with 12.04 Ubuntu LTS. It is a very stable long term support version.

---

### Post by WB0HYQ on 2013-05-30
Yeah.  You're right.  I have the 64-bit version downloading right now (25% done - hour & 45 to go).  I'll go with that.  So, what I currently have will be overwritten with the newer version anyway.  I have 8G of RAM.

Will I have the same problem after the reinstall, or should the dual-boot setup work this time?

I have 2 HD's, a 470Gb SATA primary (drive C and a 1.5TB external USB of which I have partitioned into 800G as NTFS for Windows use and there appears to be two other partitions (both marked as Healthy Primary) of 589G and 8G.  They weren't there before so I assume that the UBUNTU installer created them.

The new 64-bit version should be able to spot those two partitions I hope.

Bill

---

### Post by presence1960 on 2013-05-30
It should work. You want to choose the device (location) of bootloader to be sdb, not sda. There is a drop down box on the installer that lets you choose where to install the boot loader (GRUB). It will look like this: /dev/sdb
 Leave sda alone, it is set to boot windows. Put GRUB on MBR of sdb (external). If you mess up the bootloader during the install, no worries. You know how to set your internal disk's MBR back to windows like you just did. Then we can get GRUB set up on MBR of external disk (sdb) Either way it will work.

---

### Post by WB0HYQ on 2013-05-30
Great!  I'll do that just as soon as this pesky download finishes and I burn the DVD.  Probably won't get it done totally until tomorrow morning though.  I'll get back to this thread then.

EDIT:  The first time I installed, the drop-down installer box only gave me the USB external drive.  The internal drive was not in the list.

Bill

---

### Post by presence1960 on 2013-05-31
> **WB0HYQ said:**
> Great!  I'll do that just as soon as this pesky download finishes and I burn the DVD.  Probably won't get it done totally until tomorrow morning though.  I'll get back to this thread then.

EDIT:  The first time I installed, the drop-down installer box only gave me the USB external drive.  The internal drive was not in the list.

Bill

I just thought of something. if you can open the case and disconnect your internal drive, then install ubuntu onto the external disk this will avoid most problems. GRUB will automatically be put on the MBR of the external. After the installation check to see ubuntu boots. Then hook your internal disk back up. In BIOS set the external as first device to boot. Boot up to Ubuntu. Open a terminal and run

```
sudo update-grub
```

This will search for your windows OS and add it to the GRUB menu. As long as you have the external set to boot first you will be able to boot Ubuntu & windows from GRUB. If for some reason the external is disconnected or the internal disk is set to boot first you will boot right to windows.

---

### Post by WB0HYQ on 2013-05-31
That certainly makes sense.  I can pull the desktop out far enough to get the side panel off, disconnect the SATA cable and boot up on the DVD.  That way, the installer won't find anything but the USB drive (again) and I can just overwrite the previous partition the 32-bit installer created.

A great solution to the problem.  Thanks a bunch.  I'll get right on that this morning and come back here for a report on how it went.

Bill

---

### Post by WB0HYQ on 2013-05-31
Hmmmm.  I don't think that was a good idea to disconnect the SATA drive.  The installer asked me to set up the new install (over the older,32-bit version, which was a good thing) but it called the drive SDA and had the three partitions on it.  Another problem was that the installer said it would use ALL of the external USB 1.5TB drive unless I altered the partition table.  Now, I've done that a few times, but the UBUNTU change procedure was not clear to me as it offered a host of file systems I knew nothing about (NTFS was not one of those offered).  I didn't want to overwrite all the stuff I had in the (resized NTFS) USB partition so I stopped the install and exited.

I've hooked the SATA back up now and, since I know how to get the MBR back, I'll just proceed like I did the first time.  See any problems with that?

Bill

---

### Post by WB0HYQ on 2013-05-31
Well, that was an exercise in futility.  I let the 64-bit version install (one of the install choices was "replace 11 with 12" and I accepted that one).  It took a while to install and when it was done, I pulled the install disk and rebooted.

Same message as the first post in this thread, good old "Grub rescue >".

Now what?  I have reset the MBR so I can get into Windows, but I'm now pretty much against going much further until I can get an explanation of WHY I can't dual-boot into UBUNTU.  I thought that the installer would do all that for me and I'd be offered a choice of OS's to boot into, not the Grub prompt.  What happened?

Windows disk management says that there are the two partitions on my USB external, like before, and I've done a CHKDSK on the remaining Windows portion of the drive, but I can't see how to kickstart UBUNTU into operation.

Bill

---

### Post by fantab on 2013-05-31
Can you post the screenshot of your disks from widnows? Two screen-shots each showing a different disk.
Have you set up the BIOS to boot USB devices first? Is USB booting enabled in BIOS?

---

### Post by WB0HYQ on 2013-05-31
BIOS is set to boot 1) USB; 2) HDD0; 3) CD/DVD.

When I let the machine boot up, it blows right through POST and starts Windows.  Doesn't stop at all and give me any option.

Not quite sure what you mean by "screenshot of the disks".  I can post shots of what Windows System Management thinks is on the USB disk, but it simply shows that I have reduced the initial 1.5TB to 800G for Windows, and two other partitions marked as "healthy, primary".  One is 600G and the other is 8G.  The latter two were created by the UBUNTU installer.

Bill

---

### Post by layolayo on 2013-05-31
I have had a very similar issue today - took 5 hours to eventually fix it... my Dad was very patient watching it all go wrong and his Sony Vaio potentially been killed... got there in the end though.

The lilo commands above will get you Windows back.

I had 2 x HDD installed and Ubuntu 12.04 got installed without choice onto the second one (sdb) windows is on (sda).

I booted up a live usb version of Ubuntu 12.04 and did the following:

[COLOR=#333333][FONT=Ubuntu Beta]You can try to repair GRUB.[/FONT][/COLOR]

[LIST=1]
[*]To do this, boot from any Live CD and open a terminal.
[*]Mount the partition with your installed Ubuntu by entering

sudo mount /dev/sda? /mnt  

Important: replace the '?' with the partition where you installed Ubuntu! If you don't know which partition this is, open gparted and look for it. Mine was sdb1
[*]Include the directory with important device information

sudo mount -o bind /dev /mnt/dev 

sudo mount -o bind /sys /mnt/sys 

sudo mount -t proc /proc /mnt/proc
[*]Now change into the mounted system:

sudo chroot /mnt /bin/bash
[*]Then you can install GRUB by typing (sda here will overwrite/replace the standard windows bootloader)

grub-install /dev/sda

update-grub
[*]Exit the terminal with exit.

This got me back the GRUB and all has been well.
[/LIST]

---

### Post by presence1960 on 2013-05-31
Seems to be a BIOS thing. You should be able to press a key at boot to bring up a one time boot from device menu. On my BIOSTAR motherboard it is F9. This brings up a menu which allows me to select what device to boot from. Refer to your motherboards documentation for which key to press. It may even be displayed at POST. Choose the external disk to boot from. This wil tell if your ubuntu & GRUB are properly configured.

BTW with only one hard disk (your external) of course it will be referred to as sda. There is no other disk when you did the installation. That is not the problem. Sorry for the delay as I was in work.

---

### Post by WB0HYQ on 2013-05-31
> **presence1960 said:**
> Seems to be a BIOS thing. You should be able to press a key at boot to bring up a one time boot from device menu. On my BIOSTAR motherboard it is F9. This brings up a menu which allows me to select what device to boot from. Refer to your motherboards documentation for which key to press. It may even be displayed at POST. Choose the external disk to boot from. This wil tell if your ubuntu & GRUB are properly configured.

BTW with only one hard disk (your external) of course it will be referred to as sda. There is no other disk when you did the installation. That is not the problem. Sorry for the delay as I was in work.

But it isn't a BIOS thing.  I can hit F11 and get the boot device menu.  the USB HDD is one of the choices and, if it use it, I get the Grub Rescue prompt and nothing else.  I have to go back and boot up the UBUNTU DVD again, get into "use off the DVD", and put the MBR back to get into Windows again.

There is no other option I can see to give me UBUNTU on the partition it created.

Bill

---

### Post by WB0HYQ on 2013-05-31
@Layolayo:  I'll give that a try and see what happens.  I'm about to give up on the whole mess now.  I really wanted to give LINUX another try after the computer I had it on died, and thought that the new version was a good place to start.  I'm almost sorry I started this operation.  I've never had such trouble installing an OS before.

EDIT:  You give a couple of commands that have additional conversational information tacked onto them.  I am not sure exactly what you mean with the following:

          sudo mount -o bind /dev /mnt/dev and /sys   <-- is the "and /sys" part of the command, or is there additional info needed here?

          sudo mount -o bind /sys /mnt/sys "and the interface data"   <-- is that part of the command also?  If so, what takes its place?


Bill

---

### Post by WB0HYQ on 2013-05-31
Okay.  Here's what 'gparted' gives me under the top-right dropdown list:

/dev/sda  <-- this is my primary Windows SATA internal drive and I don't want to mess with it at all.

/dev/sdb  <-- this is my USB external drive, it is further divided up as follows:

   /dev/sdb1  NTFS  /media/TERA-T   799.95Gb  <-- this is my re-partitioned Windows drive with my development data on it.  I don't want to mess with it either.

   /dev/sdb2  Extended   (further divided - below)

      /dev/sdb6  ext4  /media/ba8eee86-76cb-4221-8329-3de60a973905, /mnt  <-- this is where UBUNTU is installed (I think)

      /dev/sdb5  linux-swap

      unallocated  unallocated  <-- a very small bit left over from the partitioning, I think.

So, where do I go from here?  What commands do I issue to the terminal in the Live CD to get things rolling?

Bill

---

### Post by fantab on 2013-06-01
By screen-shot of your partitions I meant, How does your partition look from Windows disk management? You can boot into Windows right? I want to see how your partitions look. 

If you can boot Ubuntu Live Disk... then post the output of:
```
sudo parted -l
```

---

### Post by WB0HYQ on 2013-06-01
Here is the screenshot from Windows:

[IMG]http://intellisigsys.net/pics/diskmanagement_01.jpg[/IMG]


And here is the output from 'sudo parted -l':

```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AADS-9 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdb: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  859GB   859GB   primary   ntfs
 2      859GB   1500GB  642GB   extended
 6      859GB   1492GB  633GB   logical   ext4
 5      1492GB  1500GB  8588MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           


```


Hope this helps because, frankly, I'm about to abandon the whole operation as a bad idea.  I thought that installing LINUX was supposed to be an easy thing now and here I am trying various command-line entries just to get my MBR back after the installer messes it up.

Bill

---

### Post by fantab on 2013-06-01
Your partitions on both HDDs look fine. No issues there AFAIK. However there is no Boot Flag on your EXHDD. That is your problem.

I hope you have all your data on ExHDD Backed up. We have to reinstall ubuntu 64bit, its easier and simple.

We will Delete partitions 5, 6, and 2 (in that order) from /dev/sdb (ExtHDD). Use Gparted from Ubuntu LiveDVD/USB. 'Apply' All changes in Gparted to finalize delete.

Recreate Partitions for Ubuntu. You may use the following suggestion...

Ext HDD: /dev/sdb
/dev/sdb1 859GB Primary NTFS (Which is already there)
/dev/sdb2 30GB Primary Ext4 (Install Ubuntu here with Mountpoint=/)
/dev/sdb3 4GB Primary SWAP
/dev/sdb4 All the remaining GB Primary Ext4 (Mountpoint=/home, this is where all your personal DATA is stored). (If you are comfortable sharing DATA between both Ubuntu and Windows then format this as NTFS and do NOT use any mountpoint).

Apply all changes in Gparted. Close Gparted. Restart. Boot into Windows and run 'chdsk' on the ExtHDD. We don't want any errors there. [http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

 Boot with Ubuntu LiveDVD/USB, 'Try Ubuntu'. Once the desktop is ready, Establish Internet connectivity. From Desktop 'Install Ubuntu'. At 'Installation Type' Dialog SELECT "Something Else". Choose your ExHDD and Select the partition where you intend to install Ubuntu (/dev/sdb2 or the 30GB partition) and click "CHANGE". Select USE AS=Ext4, MOUNTPOINT=/ select Format. 
Similary choose /dev/sdb4 or the Partition with 'all the remaining GB' and Select USE AS=Ext4, MOUNTPOINT=/home, select format. If you want to use this as NTFS then ignore this step.

At the bottom of the first dialog you find drop-down options to install GRUB- Bootloader. Select the /dev/sdb (ExHDD). Continue with installation. Reboot once done.

If your Bios is set to boot USB first then you will see Grub Menu. If it is not then Windows will boot.

Good Luck.

---

### Post by WB0HYQ on 2013-06-01
Since my last post, I went down to the local store and bought a 250G, internal, SATA drive and installed it.  In Windows, I verified that the drive is installed properly and formatted as NTFS.  Using the Live DVD I ran gparted and verified that there was a 'boot' flag on this drive.  I spotted that potential problem probably about the same time you did.  For some reason, the external USB HDD doesn't like to boot.  I suspect that it is due to a strange delay in starting up after it sits for a while or it simply tells everyone who asks that it isn't set up to boot.  In any case, the new drive is flagged as bootable.

I am now is the process of re-re-reinstalling on the new drive and it is about half over now.  As part of the reinstall, I told the installer to set it up as 'ext4' and then it complained about a 'mount point' so I selected "/".  Hope that works.

Once that operation is completed, I will report back as to how it went and I definitely appreciate the work that went into your last post, Fantab.

Bill

---

### Post by WB0HYQ on 2013-06-01
Well, the results were better, but the mouse died.  I can now boot to either windows or UBUNTU.  I still have to set BIOS to boot from the UBUNTU drive, but once I do, I get the Grub menu that lets me boot into Windows if I want.  So BIOS needs to be adjusted.

What didn't work was the mouse.  It dies a horrible death and refuses to move - at all.  Pressing TAB lets me navigate around a bit, but I am totally unfamiliar with any of the hot key commands that UBUNTU uses so that is of little help.

Is there any cure to the bad mouse?  And, while I'm at it, I need to know how to exit UBUNTU gracefully NOT using the mouse.

Bill

---

### Post by AgentZ86 on 2013-06-01
Typically installing ubuntu is simple along side of windows

However what your doing is not as typical to install and boot to external drives and no boot flags on the linux partition either.

As far as the mouse issues goes what type is the mouse/model  ?

---

### Post by fantab on 2013-06-01
Post #26 is still relavant just apply it to your New 250GB Internal SATA. 

One more thing... Check your BIOS for SATA Mode, it should have options like, IDE, AHCI, RAID. Setting it to AHCI will improve your disks' communication with Mother Board. However if you change it to 'AHCI' then your Windows will not boot. Ubuntu will work alright.

If your SATA Mode is not set to AHCI and if you want to set it to AHCI then do this first in Widnows then reboot and change mode:  [Read HERE]("http://www.ocztechnologyforum.com/forum/showthread.php?67697-Guide-to-enable-IDE-AHCI-without-reinstalling&p=478334&viewfull=1#post478334"). I suspect that this could be another reason for non-bootable ExHDD.

---

### Post by WB0HYQ on 2013-06-01
I am curious, AgentZ86.  How am I not typical?  External USB installations for some of my friends worked just fine.  i suspect that my particular brand of external HDD just isn't set up to boot from.  My Mobo is a new upgrade and has loads of bells/whistles.  The mouse is a HP model S-48 and works just fine everywhere else (including when I boot up the Live DVD), so I'm assuming some sort of driver didn't get set up properly and need to know the procedure for fixing that.

@Fantab:  I come from the 'if is isn't broken, don't mess with it' group so I'll not be changing any modes.  If I set my new drive as the boot first drive in BIOS, then the Grub menu will come up and I can choose Windows if I wish or just let it time out and UBUNTU will start.  I just need to fix the mouse problem now.

Bill

---

### Post by AgentZ86 on 2013-06-01
> **WB0HYQ said:**
> I am curious, AgentZ86.  How am I not typical?  External USB installations for some of my friends worked just fine.  i suspect that my particular brand of external HDD just isn't set up to boot from.  My Mobo is a new upgrade and has loads of bells/whistles.  The mouse is a HP model S-48 and works just fine everywhere else (including when I boot up the Live DVD), so I'm assuming some sort of driver didn't get set up properly and need to know the procedure for fixing that.

@Fantab:  I come from the 'if is isn't broken, don't mess with it' group so I'll not be changing any modes.  If I set my new drive as the boot first drive in BIOS, then the Grub menu will come up and I can choose Windows if I wish or just let it time out and UBUNTU will start.  I just need to fix the mouse problem now.

Bill

HP model S-48 ? So it's a 2 button PS2 scroll mouse ?
I'm assuming you are pluggin into a PS2 port and not some PS2 to USB adapter thing ? 

What your doing is single booting from a selected device such as: select HD, CD, USB, Flash etc. thats not really dual boot in the general sense. And without the boot flag it's even less typical to redirect the boot process to a non-bootable external drive.

Typically the dual boot subject is related to both OS's on the same physical Drive.
Booting from 1 or the other physical hard drive thats not really typical and not really dual booting either.

---

### Post by WB0HYQ on 2013-06-01
Okay.  Semantics aside, the boot flag has been taken care of by using my new, internal SATA drive instead of the external USB drive to reinstall UBUNTU in a dual-DEVICE boot configuration.

The mouse works perfectly when I boot using the Live boot disk so whatever driver that uses should work in the installed version; but it doesn't.  So, since the UBUNTU desktop is unusable without the mouse, I'm assuming I have to make at least one more boot-up using the Live DVD in order to start a terminal to correct the mouse issue.

I was also totally unsuccessful in gracefully exiting UBUNTU's desktop because I could find no hot key or combination of keys that would shut down UBUNTU.  I had to hold down the power button to kill it.  Of course, two seconds later I remembered that if I had used the Ctrl-Alt-F2 terminal and issued the 'shutdown' command that would have worked also.

The mouse driver(s) are my main concern now.

Bill

---

### Post by WB0HYQ on 2013-06-01
Aha!  I managed (painfully, using keyboard pecks) to download/install the NVIDIA driver for my desktop so I could get the 1600x900 resolution and the mouse started working.  Some subtle problem between the generic video driver and the actual NVIDIA driver probably.

In any case, I now have a functioning UBUNTU installation.

My thanks to all involved.

Bill

---

### Post by PedroPV on 2013-06-01
I have just done it. Try pressing F2 when you boot.

---

### Post by WB0HYQ on 2013-06-01
> **PedroPV said:**
> I have just done it. Try pressing F2 when you boot.

Done what?  Why should I press F2?

Bill

---

### Post by presence1960 on 2013-06-01
So it would seem the problem after all was your external drive, not the installs you did. Glad you got it sorted out. BTW linux does not need a boot flag to boot, however windows does.

---

### Post by WB0HYQ on 2013-06-01
> **presence1960 said:**
> So it would seem the problem after all was your external drive, not the installs you did. Glad you got it sorted out. BTW linux does not need a boot flag to boot, however windows does.

It would seem so.  I've gone to the WD website and put in a technical support question about my external drive being unable to support 'boot from USB', but any reply may take a while (if ever).

I am now happily Ubunting away.  First off I have to download/install around 130 updates.  That can wait until tomorrow however.

Thanks for your help.

Bill

---

### Post by AgentZ86 on 2013-06-01
Ok great so mouse is working now

---

### Post by fantab on 2013-06-01
> **presence1960 said:**
> So it would seem the problem after all was your external drive, not the installs you did. Glad you got it sorted out. BTW linux does not need a boot flag to boot, however windows does.

Regarding Boot Flag:
I have two HDD (internal); one Widnows only and the other Linux only both booting in Legacy 'msdos'. /dev/sda1 and /dev/sdb1 have 'Boot' flags set. I also use an ExHDD to boot Knoppix, in legacy mode. Its first partition too has 'Boot' Flag. I have NOT set any Boot Flag myself.

When GRUB is installed on HDD it puts a 'Boot' Flag. So I think 'Boot' Flag is needed. Please confirm.

---

### Post by presence1960 on 2013-06-01
Unless there has been a recent modification to GRUB 2 as far as I remember linux does not need a boot flag. See [here]("http://ubuntuforums.org/showthread.php?t=1850805") 
Here is my fdisk -l output:

```
raz@raz-TA790GXE:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7408b4a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   283836415   141917184    7  HPFS/NTFS/exFAT
/dev/sda2       283836416   435967999    76065792    7  HPFS/NTFS/exFAT
/dev/sda3       435968000   467425279    15728640   83  Linux
/dev/sda4       467425280   488396799    10485760   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x886a559e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4094   188745727    94370817    5  Extended
/dev/sdb2       188745728  1953523711   882388992   83  Linux
/dev/sdb5            4096     4198399     2097152   82  Linux swap / Solaris
/dev/sdb6         4200448    81795071    38797312   83  Linux
/dev/sdb7        81797120   159390869    38796875   83  Linux
/dev/sdb8       159393792   188745727    14675968   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00016836

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953521663   976759808    7  HPFS/NTFS/exFAT
raz@raz-TA790GXE:~$ 

```

sda1 is windows 7
sda3 is Arch
sda4 is Arch /home
sdb6 is Ubuntu
sdb7 is Mint

---

### Post by fantab on 2013-06-01
From the link you gave, oldfred's post reads:
> Some BIOS (Intel motherboard primarily) will only let you boot if you  have a boot flag on a primary partition (Seems to assume Windows).

That could be it. Since I do have Intel MoBo. In that case its not GRUB but the MoBo firmware.

Lets hope that someone else, like WB0HYQ confirms this.

Regards...

EDIT: 
By the way, if we use GUID Partition Table and boot in 'BIOS mode (NOT UEFI) then a 1-2MB unformatted partition with Boot Flag set is needed to run Grub and boot Ubuntu/Linux.

---

### Post by presence1960 on 2013-06-01
I have been booting for years without a boot flag for linux. So maybe it is hardware related.

---

### Post by presence1960 on 2013-06-01
> **fantab said:**
> From the link you gave, oldfred's post reads:


That could be it. Since I do have Intel MoBo. In that case its not GRUB but the MoBo firmware.

Lets hope that someone else, like WB0HYQ confirms this.

Regards...

EDIT: 
By the way, if we use GUID Partition Table and boot in 'BIOS mode (NOT UEFI) then a 1-2MB unformatted partition with Boot Flag set is needed to run Grub and boot Ubuntu/Linux.

LOL. It looks like we are both right!!

---

### Post by WB0HYQ on 2013-06-02
I have heard back from WD.  The gist of their email (English is not their first language) is that the delay I am seeing is what they term a 'resting period'.  I think they mean something like a reduced-power kicking in after "N" minutes to reduce wear on the drive.  Since it is packaged in a non-ventilated plastic case I can believe it.

They also state that certain motherboards, even though they may say they support USB booting, will not boot with their drive.  They don't know why.

As to the boot flag, it does indeed appear that it is largely a hardware-related function and not related to the particular LUNUX distro.

Bill

---

### Post by presence1960 on 2013-06-02
Glad you got everything sorted out Bill. Enjoy Ubuntu!

Edit: That explanation from WD makes sense. Both setups you got the GRUB rescue prompt because the disk was not initialized fast enough and your GRUB files in /boot on the external disk could not be read/found. It doesn't matter what MBR GRUB is on, it stiill looks to /boot directory on your Ubuntu /.

---

### Post by WB0HYQ on 2013-06-02
I am enjoying it very much.  Cruising all the software packages now for interesting things.  The Software display app keeps crashing and restarting though, but it still works well enough to install software.

Seems like a few things are marked as Free, but there is only a Buy button over on the right.  I tried to send a 'something wrong with this page' to wherever it goes, but I'm always told the server is busy and to try again later.  Oh well.

Bill

---

### Post by layolayo on 2013-06-10
Looks like you got things working - great! I've updated my post, removing the additional text from end of commands. Thanks for pointing out.

---

### Post by WB0HYQ on 2013-06-10
Sure did.  All is fine now.  I don't know under what conditions the Wireless Access point decided it was "boss", but it sure messed things up.  I know just what to do if it happens again.

Bill

---

