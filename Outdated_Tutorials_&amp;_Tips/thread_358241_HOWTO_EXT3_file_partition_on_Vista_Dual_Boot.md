---
title: "HOWTO: EXT3 file partition on Vista Dual Boot"
date: 2007-02-10
forum: Outdated Tutorials &amp; Tips
---

### Post by laughingLoki on 2007-02-10
[SIZE="3"]**WARNING**[/SIZE]
I'm a busy person.  I don't know how often I'll be able to update this guide or support those that have problems.  I'll try my best, but don't be surprised if I get too busy to support this guide.

Any moderator/admin is more than welcome to update this guide or edit it as necessary.  Let someone else maintain it if you want.  I just wanted to get the information out there in a useful format.

[b]I'm not entirely sure, but I think that EXT2IFS only works on 32 bit processors.  If you try it on a 64 bit system, and it fouls up, I don't take any responsibility.

I have tested this process only on 32 bit machines.

If EXT2IFS doesn't work for you on a 64 bit system, try [<ext2fsd>](http://ext2fsd.sourceforge.net/).  Maybe that will work.  Just be aware that it has an ugly splash screen that starts on each boot.

I do not take any responsibility for anything that may occur from following this guide.  (I have to put some sort of message like this as stated in the sticky.  Nothing personal.  ;___;)[/b]

[SIZE="3"]**Introduction**[/SIZE]
Several people use dual boot configurations, because they need to use Windows for some reason or another.  In order to facilitate file storage on these systems, a separate partition is usually maintained so that you can access your files under Linux and Windows.

In Windows XP, it was possible to use EXT2IFS to integrate EXT2/EXT3 into the system.  This was just great for systems using Ubuntu and Windows XP, but what about those who want or need to upgrade XP to Vista?

This HOWTO aims to outline how to get EXT2IFS to work under Windows Vista.  I haven't found instructions anywhere on how to get EXT3 support in Vista.  If anyone finds one, please post a link below.  It may have some information that is not outlined in this guide!

I've tested the instructions that follow.  However, I did try to get EXT2FSD working first.  I couldn't get it to work at all on my machine (Dell Latitude D600), so I uninstalled it completely.  If you can't get the following instructions to work, please describe your problem in a post below.

[SIZE="3"]**My Specs**[/SIZE]
Here are my machine's specs--just in case someone wants to know:
Dell Latitude D600
1 GB RAM
80 GB HDD
Pentium M (1.7 GHz)
(running Ubuntu 6.10 and Windows Vista Business)

[SIZE="3"]**Getting Started**[/SIZE]
Install Windows Vista (you didn't see that one coming, did you?  ^___~).  Restore grub if you already had Ubuntu installed.  A guide for restoring Grub is located [<here>](http://ubuntuforums.org/showthread.php?t=224351).  I've followed that guide, and it worked just fine for me.

[SIZE="3"]**Installing EXT2IFS**[/SIZE]
1. Download the installer [<here>](http://www.fs-driver.org/download.html).

2. If you try running the installer now, you'll get a nasty [<error message>](http://img521.imageshack.us/img521/1443/compatabilityerrorla5.png).  Instead, right click Ext2IFS_1_10c.exe, and select properties.

3. Click the "Compatibilty" tab.  [<Enable the "Run this program in compatibility mode for" checkbox, and select "Windows XP Service Pack 2".>](http://img68.imageshack.us/img68/1458/propertiesqa0.png)

4. Right click Ext2IFS_1_10c.exe, and select "Run as administrator".

5. The installer will now run as it did in XP.  Yay!   ^___^

6. When going through the installer, just make sure that the enable large files options is enabled.  It should be by default.  Otherwise, this is just a next, next, next, done sort of install.  **[<Make sure to select what drive letters you want to use at the end of the installation.>](http://img510.imageshack.us/img510/4594/rememberthedriverlettersm4.png)**

7. Restart your computer.

8. When you start up again, your files should show up in the drive that you specified during the install.

That's it!  You're done.  This should work just fine unless Microsoft decides to break it with an update.

[SIZE="3"]**Uninstallation**[/SIZE]
If you want to uninstall EXT2IFS, simply remove it normally in the control panel.  Nothing special about this process.

[SIZE="3"]**Changing Drive Letters**[/SIZE]
If you want to change the drive letter assigned to your EXT2/ETX3 partition, use the IFS Drives applet.  In the control panel, there is an icon labelled "Additional Options".  After clicking that icon, a link to the IFS Drives applet is shown.  You can use that applet to change the drive letter of your EXT2/EXT3 partition.  Unlike Windows XP, you need to restart your computer every time you change a drive letter in the IFS Drives applet.  Bummer.

[SIZE="3"]**Issues**[/SIZE]
[LIST]
[*]Attempting to install something on Windows Vista with the installation files on your EXT2/EXT3 partition doesn't seem to work.  I don't know exactly why this is the case.  Maybe it's some new security "feature"?
[*]Files in your EXT2/EXT3 file partition will not be moved to the "/Recycled" directory as they were in Windows XP.  This means that files deleted from EXT2/EXT3 partitions in Windows Vista will bypass the recycling bin completely; whereas in Windows XP, you always had to empty the recycling bin to finally deallocate the space your deleted files were using just sitting in the recycling bin.
[*]If your EXT2/EXT3 file system is not cleanly unmounted, then you won't be able to access it in Windows.  So, if you do something like disconnect all power sources from your computer while running Ubuntu, and then boot into Windows, you won't have access to your EXT2/EXT3 file system.  If you reboot into Ubuntu and unmount the FS, and then boot into Windows, all will be well.  (You can always just boot back into Ubuntu, do a clean restart, and boot Windows to get back access to the EXT2/EXT3 FS if you're having troubles.)
[/LIST]

[SIZE="3"]**Are you that weird guy from ebay/myspace?**[/SIZE]
No.  I'm not.  It looks like two hippies decided to use my handle on ebay and myspace.  I don't like or use ebay or myspace at all.  So there!

I've been asked this on IRC before.  I thought I'd get that out of the way.  0___o

P.S.: I'm not that guy from okcupid.com, either.  That guy so looks like a paedophile.

---

### Post by Aldrik on 2007-02-14
Thanks for the guide/how-to laughingLok works great. The only thing is it has both read & write support  (I tried a bunch of other ext2/3 drivers also without any luck). So I contacted the developer of [Ext2 ifs]("http://www.fs-driver.org") ([Stephan Schreiber]("http://www.fs-driver.org/author.html")) and he said the next release will have options for read-only. So I'll be waiting for that... :)

---

### Post by kevinf311 on 2007-02-14
Good stuff. My roommate has a brand new computer that he built with Vista on it. He expressed interest in installing Ubuntu. I was mildly worried about how Vista would handle another OS on it's turf. 

I have XP set up with FS Driver, and planned on helping him set up the same. Seeing that it works gives me more confidence. 

I set up my partitions as follows (and am planning a similar set up for my roommate):

[---Windows_ntfs---][---------------/home_ext2or3----------------][--Root_ext3--][swap]

Programs stay in their respective OS partitions, files and settings reside in /home. It's nice being able to listen to music no matter what OS I'm in.

Also, If your windows installation has been around for awhile, it's a good idea to move off all of your files (that are going to the /home partition) and then defrag the volume. If the data is too spread out, then you will have issues resizing the partition in gparted (or your partition manager of choice).

Good HowTo, it will come in handy.

---

### Post by laughingLoki on 2007-02-14
> **kevinf311 said:**
> Good stuff. My roommate has a brand new computer that he built with Vista on it. He expressed interest in installing Ubuntu. I was mildly worried about how Vista would handle another OS on it's turf. 

I have XP set up with FS Driver, and planned on helping him set up the same. Seeing that it works gives me more confidence. 

I set up my partitions as follows (and am planning a similar set up for my roommate):

[---Windows_ntfs---][---------------/home_ext2or3----------------][--Root_ext3--][swap]

Programs stay in their respective OS partitions, files and settings reside in /home. It's nice being able to listen to music no matter what OS I'm in.

Also, If your windows installation has been around for awhile, it's a good idea to move off all of your files (that are going to the /home partition) and then defrag the volume. If the data is too spread out, then you will have issues resizing the partition in gparted (or your partition manager of choice).

Good HowTo, it will come in handy.

I have the exact same setup, except I have a Dell diagnostic partition in there.  I have to keep the partition, or Dell support will hassle me whenever my laptop gets repairs under warranty.  >___<

I realised that the drive letters *can* be changed under the control panel.  I guess I just wasn't used to the new interface yet.  The HOWTO will be updated accordingly.

---

### Post by Jose Catre-Vandis on 2007-02-15
I am running Vista (NFTS), Edgy (EXT3) and a shared EXT3 partition. I used "Ext2IFS_1_10c" to enable support on Vista to the shared partition, which after installation, and a reboot, works flawlessly, and give read/write. Vista also has NFS Client in "Features" so you can easily enable NFS shares into Vista as well. Much easier than in XP.

32 bit machine and Vista Ultimate

---

### Post by ramasdf123 on 2007-02-18
i will consider you to be THE MAN if this work and i am going to go try it now

```
sudo shutdown -r now
```

---

### Post by DerArzt on 2007-02-19
It works! thanks a lot.

---

### Post by richandcreamy on 2007-02-22
THANK YOU THANK YOU THANK YOU! :guitar: you rock~~

---

### Post by Imek on 2007-02-25
This doesn't work for me... I follow the instructions exactly, and the drives appear after I reboot, but when I try to open them I get an "I:\ refers to a location that is not available" etc. message. I can't run the control panel tool either. Anyone have any ideas?

---

### Post by laughingLoki on 2007-02-25
> **Imek said:**
> This doesn't work for me... I follow the instructions exactly, and the drives appear after I reboot, but when I try to open them I get an "I:\ refers to a location that is not available" etc. message. I can't run the control panel tool either. Anyone have any ideas?

Try installing the driver in test mode.  Press F8 as soon as Windows starts booting to startup in test mode.

Test mode disables driver signing checks.  That would help in the case where the driver cannot install properly due to it failing those checks.

Edit:

I thought of another possible cause of your problem:  perhaps, the drive letter you selected is in use by another partition/device.  This would then cause a conflict, since you cannot manage the drive names of EXT2/EXT3 partitions using the Windows disk management utility.

Open the Windows disk utility by running compmgmt.msc, and the selecting "Disk Management" in the left-hand tab.  Change the drive letter of any device/partition using the drive letter I to something else.  Simply right-click the device/partition and select "Change drive letter and paths" to change the drive letter.

You may need a restart for it all to take effect.

---

### Post by Imek on 2007-02-25
Thanks! The test mode idea worked. However, it only works when I put the thing on in the boot menu, then stops working again if I boot up without setting it. I think I've found a way to turn off the driver signing permanently, but it really doesn't seem wise.. Do you know of a way around this, e.g. to get it to ignore this one driver?

Though I guess it's not that important, as long as it works. Now all I need to do is to get SLI and SB Live both working and I can ditch XP altogether.

---

### Post by laughingLoki on 2007-02-27
> **Imek said:**
> Thanks! The test mode idea worked. However, it only works when I put the thing on in the boot menu, then stops working again if I boot up without setting it. I think I've found a way to turn off the driver signing permanently, but it really doesn't seem wise.. Do you know of a way around this, e.g. to get it to ignore this one driver?

Though I guess it's not that important, as long as it works. Now all I need to do is to get SLI and SB Live both working and I can ditch XP altogether.

There was no driver sign checking in XP.  If there was, I think you could just click "OK" during installation, and it would install anyway.  I'd prefer keeping driver signing checking off, myself.

Could you tell me your method?  Is it some sort of startup script?  Do you get the lame "Test mode" message in the corners of the screen?

I don't know of any way of ignoring a specific driver during the check.  Sorry.

Edit:

Is this your method?

```
Bcdedit.exe /set nointegritychecks ON
```

---

### Post by Imek on 2007-02-28
Don't remember specifically, but that looks like it. I did have a weird problem with it stopping working after two reboots, but it mysteriously started working again and I've had no problems since then.

---

### Post by laughingLoki on 2007-02-28
> **Imek said:**
> Don't remember specifically, but that looks like it. I did have a weird problem with it stopping working after two reboots, but it mysteriously started working again and I've had no problems since then.

That's Windows for you.  >___>

---

### Post by dejitarob on 2007-03-29
This doesn't work for me on Vista. I was able to assign my ext3 partition a drive letter but when I try to open it in my computer, Vista gives me a prompt saying I need to format the drive before I can use it. In the Disk Management console, the ext3 partition does not have the drive letter that I assigned it during the fs-driver installation. I tried the command to disable driver signing. I also tried booting into 'Disable Driver Signing Enforcement' mode to install and then rebooted again into this mode to test.

**Edit**: Ok, I [RTFM'ed]("http://fs-driver.org/troubleshoot.html") and ran this [diagnostic tool]("http://fs-driver.org/download/mountdiag.exe"). It told me the ext3 was probably not unmounted cleanly. I rebooted into Linux and then back into Vista and it worked fine! Thanks for your help.  I just hope this doesn't happen often or is sign of something worse with the ext3 partition.

---

### Post by laughingLoki on 2007-04-03
> **dejitarob said:**
> This doesn't work for me on Vista. I was able to assign my ext3 partition a drive letter but when I try to open it in my computer, Vista gives me a prompt saying I need to format the drive before I can use it. In the Disk Management console, the ext3 partition does not have the drive letter that I assigned it during the fs-driver installation. I tried the command to disable driver signing. I also tried booting into 'Disable Driver Signing Enforcement' mode to install and then rebooted again into this mode to test.

**Edit**: Ok, I [RTFM'ed]("http://fs-driver.org/troubleshoot.html") and ran this [diagnostic tool]("http://fs-driver.org/download/mountdiag.exe"). It told me the ext3 was probably not unmounted cleanly. I rebooted into Linux and then back into Vista and it worked fine! Thanks for your help.  I just hope this doesn't happen often or is sign of something worse with the ext3 partition.

Sorry to take so long to get back to you.  It seems like you fixed the issue.

I'll add that bit of information to the tutorial.  If you do something so the EXT2/3 partition is not unmounted cleanly (e.g. suddenly remove power from your computer), then you cannot access it in Windows.

I've had the same thing happen to me a couple of times: once when I hibernated Ubuntu and then went into Windows, and once when I crashed Ubuntu and booted into Windows.  I don't think it's anything to worry about.

---

### Post by schneidexe on 2007-05-21
Hi,

first o all: nice howto. worked perfectly! but when I try to launch the IFS Manager ("IFS Drives") from the control panel, I always get an error, that this legacy programm can not run with this privileges. I can not add the tool to the whitelist (control panel > system > advanced), because there only .exe-Files can be added.

Any idea how to get it work? I dont want to install the whole program every time i want to change the drive letter.

schneidexe

---

### Post by Curlydave on 2007-05-22
Whenever I try to open the new partition in Vista after setting this up, it says that I need to format it before I view it. Any ideas around this?

---

### Post by laughingLoki on 2007-05-24
> **schneidexe said:**
> Hi,

first o all: nice howto. worked perfectly! but when I try to launch the IFS Manager ("IFS Drives") from the control panel, I always get an error, that this legacy programm can not run with this privileges. I can not add the tool to the whitelist (control panel > system > advanced), because there only .exe-Files can be added.

Any idea how to get it work? I dont want to install the whole program every time i want to change the drive letter.

schneidexe

I think you need administrative privileges to run the applet.


> **Curlydave said:**
> Whenever I try to open the new partition in Vista after setting this up, it says that I need to format it before I view it. Any ideas around this?

Your partition probably wasn't cleanly unmounted.  This could be caused by using a suspend-to-disk function (a.k.a. hibernation), and then booting into Windows.

Try the following:

(1) Start up Ubuntu.
(2) Log in, and do a hard shut down.
(3) Boot Windows.
(4) Check the partition by navigating to its associated drive letter in Explorer.

---

### Post by Curlydave on 2007-05-27
> **laughingLoki said:**
> I think you need administrative privileges to run the applet.




Your partition probably wasn't cleanly unmounted.  This could be caused by using a suspend-to-disk function (a.k.a. hibernation), and then booting into Windows.

Try the following:

(1) Start up Ubuntu.
(2) Log in, and do a hard shut down.
(3) Boot Windows.
(4) Check the partition by navigating to its associated drive letter in Explorer.

That would do it. Ubuntu usually won't shut down, it just goes black and doesn't do anything when I try.

---

### Post by joshuadugie on 2007-06-07
> **schneidexe said:**
> Hi,

first o all: nice howto. worked perfectly! but when I try to launch the IFS Manager ("IFS Drives") from the control panel, I always get an error, that this legacy programm can not run with this privileges. I can not add the tool to the whitelist (control panel > system > advanced), because there only .exe-Files can be added.

Any idea how to get it work? I dont want to install the whole program every time i want to change the drive letter.

schneidexe

I think the error you're describing is caused by Windows's "Data Execution Prevention" service.  It automatically checks RunLegacyCPLElevated.exe to ensure that no Control Panel applet is able to access system resources in a suspicious manner.  The DEP service prevents the IFS Drives applet from running correctly.  The only way I have found to fix this is to disable DEP entirely (which is REALLY not recommended, but is necessary because you cannot tell DEP to ignore RunLegacyCPLElevated.exe).  To do this, you must open a command prompt window as an administrator and enter: "bcdedit.exe /set {current} nx AlwaysOff".  Then reboot.  IFS Drives worked for me after that.  However, DEP should be running on your computer for your own security.  Hopefully an updated IFS Drives applet for Vista will be created so that DEP can run at the same time.  If anyone knows of another way to circumvent this error, it would be greatly appreciated.

---

### Post by macmasterxiv on 2007-07-03
Ok, I have this setup working, but I have one issue that is new to Vista that didn't occur in XP. After using the ext3 partition, when I shut down the system cleanly in XP, it would be clean according to fdisk on ubuntu startup. With Vista, whenever I access the ext3 partition, then cleanly shut Vista down, fdisk always reports errors on the ext3 during ubuntu startup, and does the long (and successful) repair. No, it is not a hardware issue. Any ideas?

---

### Post by Olivier Berten on 2007-07-15
Any idea how to tell Vista that the charset of the file names is UTF-8 ? It reads it as single-byte...

---

### Post by The TJ on 2007-07-28
> **macmasterxiv said:**
> Ok, I have this setup working, but I have one issue that is new to Vista that didn't occur in XP. After using the ext3 partition, when I shut down the system cleanly in XP, it would be clean according to fdisk on ubuntu startup. With Vista, whenever I access the ext3 partition, then cleanly shut Vista down, fdisk always reports errors on the ext3 during ubuntu startup, and does the long (and successful) repair. No, it is not a hardware issue. Any ideas?

Yeah, I have the same problem.  It's something about write times in the future.  I don't know how to disable it.  Does anyone here know?

---

### Post by yashonath on 2007-09-04
> **laughingLoki said:**
> [SIZE="3"]**WARNING**[/SIZE]
I'm a busy person.  I don't know how often I'll be able to update this guide or support those that have problems.  I'll try my best, but don't be surprised if I get too busy to support this guide.

Any moderator/admin is more than welcome to update this guide or edit it as necessary.  Let someone else maintain it if you want.  I just wanted to get the information out there in a useful format.

[b]I'm not entirely sure, but I think that EXT2IFS only works on 32 bit processors.  If you try it on a 64 bit system, and it fouls up, I don't take any responsibility.

I have tested this process only on 32 bit machines.

If EXT2IFS doesn't work for you on a 64 bit system, try [<ext2fsd>](http://ext2fsd.sourceforge.net/).  Maybe that will work.  Just be aware that it has an ugly splash screen that starts on each boot.

I do not take any responsibility for anything that may occur from following this guide.  (I have to put some sort of message like this as stated in the sticky.  Nothing personal.  ;___;)[/b]

[SIZE="3"]**Introduction**[/SIZE]
Several people use dual boot configurations, because they need to use Windows for some reason or another.  In order to facilitate file storage on these systems, a separate partition is usually maintained so that you can access your files under Linux and Windows.

In Windows XP, it was possible to use EXT2IFS to integrate EXT2/EXT3 into the system.  This was just great for systems using Ubuntu and Windows XP, but what about those who want or need to upgrade XP to Vista?

This HOWTO aims to outline how to get EXT2IFS to work under Windows Vista.  I haven't found instructions anywhere on how to get EXT3 support in Vista.  If anyone finds one, please post a link below.  It may have some information that is not outlined in this guide!

I've tested the instructions that follow.  However, I did try to get EXT2FSD working first.  I couldn't get it to work at all on my machine (Dell Latitude D600), so I uninstalled it completely.  If you can't get the following instructions to work, please describe your problem in a post below.

[SIZE="3"]**My Specs**[/SIZE]
Here are my machine's specs--just in case someone wants to know:
Dell Latitude D600
1 GB RAM
80 GB HDD
Pentium M (1.7 GHz)
(running Ubuntu 6.10 and Windows Vista Business)

[SIZE="3"]**Getting Started**[/SIZE]
Install Windows Vista (you didn't see that one coming, did you?  ^___~).  Restore grub if you already had Ubuntu installed.  A guide for restoring Grub is located [<here>](http://ubuntuforums.org/showthread.php?t=224351).  I've followed that guide, and it worked just fine for me.

[SIZE="3"]**Installing EXT2IFS**[/SIZE]
1. Download the installer [<here>](http://www.fs-driver.org/download.html).

2. If you try running the installer now, you'll get a nasty [<error message>](http://img521.imageshack.us/img521/1443/compatabilityerrorla5.png).  Instead, right click Ext2IFS_1_10c.exe, and select properties.

3. Click the "Compatibilty" tab.  [<Enable the "Run this program in compatibility mode for" checkbox, and select "Windows XP Service Pack 2".>](http://img68.imageshack.us/img68/1458/propertiesqa0.png)

4. Right click Ext2IFS_1_10c.exe, and select "Run as administrator".

5. The installer will now run as it did in XP.  Yay!   ^___^

6. When going through the installer, just make sure that the enable large files options is enabled.  It should be by default.  Otherwise, this is just a next, next, next, done sort of install.  **[<Make sure to select what drive letters you want to use at the end of the installation.>](http://img510.imageshack.us/img510/4594/rememberthedriverlettersm4.png)**

7. Restart your computer.

8. When you start up again, your files should show up in the drive that you specified during the install.

That's it!  You're done.  This should work just fine unless Microsoft decides to break it with an update.

[SIZE="3"]**Uninstallation**[/SIZE]
If you want to uninstall EXT2IFS, simply remove it normally in the control panel.  Nothing special about this process.

[SIZE="3"]**Changing Drive Letters**[/SIZE]
If you want to change the drive letter assigned to your EXT2/ETX3 partition, use the IFS Drives applet.  In the control panel, there is an icon labelled "Additional Options".  After clicking that icon, a link to the IFS Drives applet is shown.  You can use that applet to change the drive letter of your EXT2/EXT3 partition.  Unlike Windows XP, you need to restart your computer every time you change a drive letter in the IFS Drives applet.  Bummer.

[SIZE="3"]**Issues**[/SIZE]
[LIST]
[*]Attempting to install something on Windows Vista with the installation files on your EXT2/EXT3 partition doesn't seem to work.  I don't know exactly why this is the case.  Maybe it's some new security "feature"?
[*]Files in your EXT2/EXT3 file partition will not be moved to the "/Recycled" directory as they were in Windows XP.  This means that files deleted from EXT2/EXT3 partitions in Windows Vista will bypass the recycling bin completely; whereas in Windows XP, you always had to empty the recycling bin to finally deallocate the space your deleted files were using just sitting in the recycling bin.
[*]If your EXT2/EXT3 file system is not cleanly unmounted, then you won't be able to access it in Windows.  So, if you do something like disconnect all power sources from your computer while running Ubuntu, and then boot into Windows, you won't have access to your EXT2/EXT3 file system.  If you reboot into Ubuntu and unmount the FS, and then boot into Windows, all will be well.  (You can always just boot back into Ubuntu, do a clean restart, and boot Windows to get back access to the EXT2/EXT3 FS if you're having troubles.)
[/LIST]

[SIZE="3"]**Are you that weird guy from ebay/myspace?**[/SIZE]
No.  I'm not.  It looks like two hippies decided to use my handle on ebay and myspace.  I don't like or use ebay or myspace at all.  So there!

I've been asked this on IRC before.  I thought I'd get that out of the way.  0___o

P.S.: I'm not that guy from okcupid.com, either.  That guy so looks like a paedophile.

Great it works well in windows vista, both read and write is possible on a ext3 partition from vista. Many thanks.

sy

---

### Post by paolo.bonavoglia on 2008-03-16
Two weeks ago I bought a new PC with Windows Vista. I installed Ubuntu Linux on the second partition of the first disk and installed my old PATA HD as a second HD.
Then I Installed Ext2 IGS for Windows Vista.

Everything worked fine. With Ext2IFs I assigned letters to all linux partitions from both HD's.
Just for a few days!!

I worked the more with Ubuntu. A few days ago I used Vista again, no crash no power fall in the meantime, and suddenly found myself in a "partition chaos":


1. The last partition of the PATA disk (a fat32) was apparently lost by Vista; Disk manager said a mysterious error telling me it was impossible to visualize the partition and asking to update the page; but updating is completely useless; and the same partition is perfectly Ok under Ubuntu.
2.All linux partitions, but the first, were lost; under Ubuntu they were OK.
3.The card reader I had on a USB port was lost by Vista, same error as above, but perfectly OK under Ubuntu.

I tried to uninstall and reinstall Ext2IFs; an error message appeared: “Impossible to find the specified file”. And so I lost the first Linux partition under Vista too.

Under Ubuntu all partitions are Ok, but a minor problem arose about the same time: in the first days Ubuntu mounted all Linux and Windows partitions, NTFS and FAT, automatically, now it mounts only the first 2 (Windows and Ubuntu boot) and I have to mount the others manually and I'm asked for the password too.

Any idea of what is happening?

---

### Post by cremestar on 2008-03-23
sorry...i have no idea what is wrong, a n00b like me :(

anyways, i have a problem of my own: the installation went fie, and i restarted, but when i double-click on the drive, windows asks me if i want to format it. i didnt format, but does anyone have a clue what MY problem is?

---

### Post by kruzztee on 2008-10-21
I have a problem on my dual boot Ubuntu and Windows XP Tablet PC. I set my /home mount point as a share document volume between windows and Ubuntu as an EXT3 partition and I use IFS EXT2 in the Windows XP.
All the things working right until last night I updated the kernel (I forgot the version coz my computer is at home), I can't no longer access the IFS from XP and the system said "System cannot find the file specified" I tried to reinstall the IFS and boot the linux with older kernel and for what I can remember I always unmount /home volume cleanly.
Can you suggest me a solution for this? 
Lastly, sorry for my bad English.

---

### Post by theacerguy on 2009-05-05
for me this just comes up saying i need to format my ext3 partitions...:guitar:

---

### Post by catfoodgood on 2009-06-13
> **theacerguy said:**
> for me this just comes up saying i need to format my ext3 partitions...:guitar:

Me too. Anyone else's get messed up with a Vista update or anything?

---

