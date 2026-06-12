---
title: "Dualboot Two Hard Drives"
date: 2006-05-21
forum: Outdated Tutorials &amp; Tips
---

### Post by confused57 on 2006-05-21
This guide only applies to [SIZE="4"][COLOR="Red"]Ubuntu 9.04 and earlier versions[/COLOR][/SIZE], which use legacy grub.  Later versions use grub2, which is significantly different, but grub2 has a much better automated detection of other OSes.  There are several excellent Grub2 guides that you might want to consult, if you're using Ubuntu 9.10 or later:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)
[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)


As a beginner, I wanted to set up a dual boot without installing Grub to windows and was able to find two excellent links for doing this:

[http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://www.ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)
[http://ubuntuforums.org/showthread.php?p=677880#post677880](http://ubuntuforums.org/showthread.php?p=677880#post677880)

The excellent instructions provided by "lha" worked flawlessly for installing on 2 IDE drives.

I also found links to dualboot with a SATA and an IDE drive:

[http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata)
[http://www.ubuntuforums.org/showthread.php?t=192954](http://www.ubuntuforums.org/showthread.php?t=192954)
[http://www.ubuntuforums.org/showthread.php?t=275728&page=3](http://www.ubuntuforums.org/showthread.php?t=275728&page=3)
The above IDE + SATA threads are probably outdated, but I'll leave them FYI.

Hope this helps someone looking for an alternate method of dualbooting with 2 hard drives...

I have my personal computer set up to dualboot using the method described in the first two links, lha has give me his "blessings" to write up a HowTo with his instructions.  This is an alternate method of dualbooting Ubuntu and Windows, using 2 hd, without installing grub to Windows or altering your Windows installation.

First, disconnect your Windows drive, then connect the drive you want to install Ubuntu on as the primary IDE master drive.  After installing Ubuntu, allow the updater to install all the necessary updates, this may take awhile.  Shutdown your computer and reconnect your Windows drive as slave, then restart, your computer will boot into Ubuntu.

You will need to edit your menu.lst file:
(Open a terminal, copy & paste one line at a time, press "enter" each time)

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

The first line changes to the grub directory, the second line makes a backup of your menu.lst file, and the third line opens the menu.lst file using the gedit text editor.

Copy and paste the following lines above the line
###BEGIN AUTOMAGIC KERNEL LIST
```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

If grub gives an error when rebooting, you can try rootnoverify (hd1,0) instead of root  (hd1,0) in the second line.

Note:  If you prefer Ubuntu to boot by default, you can copy & paste the above entry at the very end of your menu.lst, instead of above ###BEGIN AUTOMAGIC....

To automatically display the grub menu at bootup, find the line
```
hidden
```
 
and replace with 

```
#hidden
```

To adjust the time grub is displayed at bootup, change the timeout(in seconds)...I'd suggest 10 seconds(default is 3).

Quit and save settings.

Note:  If for some reason you need to restore your original menu.lst:
```
cd /boot/grub
sudo cp menu.lst_backup menu.lst
```

Reboot your computer, it will automatically boot to Windows, unless you choose Ubuntu within the time grub is displayed.

If you want to uninstall Ubuntu, you can make the Windows drive primary master and reformat or unplug the Ubuntu drive.

If you want to remove Windows, then you can unplug the Windows drive or reformat it,  then open menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and remove the Windows entry in grub.

**Installing on a Dell Dimension 4550**:
I tried the above method trying to set up a dualboot on my Dell Dimension 4550, but when I tried to boot into Windows, I got "Error 21:Selected disk does not exist".
I finally was able to get it to work by:
Boot into Ubuntu, open up a terminal:
```
sudo fdisk -l
```
The -l is a lowercase "L"
```
cat /etc/fstab
```

From these two commands, I was able to determine that hdb, which was the slave drive with windows actually had 2 partitions.  The first partition was a 35 Mb Dell utility and the second partition was Windows, so I changed the Windows root from (hd1,0) to (hd1,1) in the /boot/grub/menu.lst.  However, I continued to get the error21 message...I thought maybe the jumper settings on the slave drive were incorrect.  Fortunately, I entered bios setup by pressing "F2" during bootup and found out that the Primary ide controller for hd1 was turned "off" by default...I changed it to "Auto" detect.  Grub booted directly into Windows and I'm enjoying dualboot of Windows and Dapper on my Dell computer.

It is possible to set up a dualboot with Windows & Ubuntu on separate hard drives, with **both hard drives connected** during the install of Ubuntu:
[http://www.ubuntuforums.org/showpost.php?p=2195398&postcount=47](http://www.ubuntuforums.org/showpost.php?p=2195398&postcount=47)
if you want to be absolutely sure not to overwrite your Windows mbr, then disconnect your Windows drive during Ubuntu installation.

An excellent tool to download before installing Ubuntu is the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
the Super Grub Disk is capable of restoring Windows mbr or reinstall grub...and can boot either Windows or Ubuntu.

---

### Post by confused57 on 2006-05-21
The definitive guide for dualbooting Windows and Ubuntu on a single hard drive, using the alternate cd, can be found at Herman's site:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

For Dapper Desktop CD:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

The guides can be used to install on 2 different hard drives, but Windows would need to be the master drive and Ubuntu the slave drive.  You would select "IDE drive hdb" to install Ubuntu onto and install Grub to Windows(hda) when prompted.   Windows doesn't like it when it's not the first OS in a dualboot system, therefore, it has to be on the master drive when using this method.  (The menu.lst(Grub) Windows entry, provided in the links in my first post method, has a mapping command, which fools Windows into thinking it is the first OS.) 

If you decide to uninstall Ubuntu, heaven forbid,  you'd need to boot up your computer with the Windows installation CD, go to recovery mode and enter **fixmbr**, which restores your Windows mbr(deletes Grub). Then you could reformat the slave drive from Windows.

**Note**:  I would recommend anyone installing grub onto their Windows mbr when setting up a dual boot with Ubuntu to download the Windows 98SE OEM boot floppy from bootdisk.com as described here:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
If for some reason Ubuntu or grub becomes corrupted, you would need to repair your mbr in order to boot Windows, by booting up with the Win98SE boot floppy and enter **fdisk /mbr**.  The boot floppy would be useful for anyone not having a Windows install cd, or as a backup for those that do have one.

I opted to post this method as a reply, rather than editing my first post, since it is a different way of setting up a dualboot with 2 hd.  Any adivce from more experienced Ubuntu Linux users concerning dualbooting would be welcomed.

I feel that having one link with various options concerning dualbooting with 2 hd, most importantly with Herman's guide, would give a beginner alternative methods for setting up a dualboot Windows/Ubuntu system.  My initial intent was to offer only the dualboot method by "lha", but other options would be helpful, in my opinion...so that beginners would have a choice depending on their system, their experience with computers & linux, and their preferences...
Here's a thread with one person's solution to dual boot dual hard drives:
[http://www.ubuntuforums.org/showthread.php?t=259422](http://www.ubuntuforums.org/showthread.php?t=259422)

If your computer supports selecting which drive to boot in bios:
[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

Tip:  Before installing Ubuntu on your system, you should try running the liveCD to ensure that there are no hardware incompatibilities and to familiarize yourself with the Ubuntu OS.

Note:  If you're installing Ubuntu to dualboot with Windows on a single hard drive, Windows **MUST** be on a partition located **prior** to Ubuntu...e.g. Windows on hda1, Ubuntu on hda2.

---

### Post by shoki on 2006-08-02
To everybody that brought this information to this place at this time... Thank you so much!!! What an awesome eloquent way to do this. Virgin Windows Install, Virgin ubuntu Install move one jumper, edit one text file and you are in heaven... ;) (with 2 virgins) sorry I couldn't resist.

Anyway than you very much. This kind of solution is what makes Liniux such a great OS.

--Shoki

---

### Post by confused57 on 2006-08-02
> **shoki said:**
> To everybody that brought this information to this place at this time... Thank you so much!!! What an awesome eloquent way to do this. Virgin Windows Install, Virgin ubuntu Install move one jumper, edit one text file and you are in heaven... ;) (with 2 virgins) sorry I couldn't resist.

Anyway than you very much. This kind of solution is what makes Liniux such a great OS.

--Shoki

Thanks, for me it was the more desirable option, don't have to worry about repairing your Windows mbr,etc and as you mentioned, it's quite easy to set up.  You summed it up nicely.

---

### Post by shakyone on 2006-08-03
Confused57,

     I also want to thank you.  I was trying to figure a method to insulate the wife from ever dealing with the fact that I put Ubuntu on the computer.  Why, because she is dependent on Windows to remote-connect to her place of employment.  She is very wary that I will screw up the computer permanently and for good reason.  

	I have been searching for a method to use NTLDR with a Linux-Ubuntu option, but it was looking procedurally complicated and a little risky, since it involved tinkering with the Windows drive MBR.  

	After reading your method I realized there is the “ever present” Windows recovery option of returning the Windows drive back to the Master IDE position from the slave position.  Last night I demonstrated the recovery option to the wife after following your procedure for installing Ubuntu and modifying GRUB.  She is satisfied since the recovery demonstration gave absolutely ZERO indication that the PC ever functioned using the Linux OS, nor did it indicate a hard drive was ever removed.  All because the MBR in the Windows drive is left intact throughout your method.  My Ubuntu/XP computer works like charm with XP set as the default OS on GRUB.  Wife is happy, and I get to have my fun too.  Have a great day!

---

### Post by Josh_b on 2006-08-17
I'm pretty sure (Me=Linux Newbie) there is a quicker way, without having to change all the files and such as in your how-to. 
This is the way I did it:
I have a SATA drive for Windows XP and and IDE drive for Ubuntu 6.06. In the BIOS, I set the CD-ROM as first device (when installing Linux) and then the IDE drive to be the first hdd to start-up. After that just install Linux (with GRUB) and Bob's your uncle. 

If I go back into BIOS and set the SATA drive as default hdd, then the GRUB doesn't show, and if I set the IDE as default, then GRUB shows, with Linux as default OS.

Hope that helps,
Josh

---

### Post by confused57 on 2006-08-17
> **Josh_b said:**
> I'm pretty sure (Me=Linux Newbie) there is a quicker way, without having to change all the files and such as in your how-to. 
This is the way I did it:
I have a SATA drive for Windows XP and and IDE drive for Ubuntu 6.06. In the BIOS, I set the CD-ROM as first device (when installing Linux) and then the IDE drive to be the first hdd to start-up. After that just install Linux (with GRUB) and Bob's your uncle. 

If I go back into BIOS and set the SATA drive as default hdd, then the GRUB doesn't show, and if I set the IDE as default, then GRUB shows, with Linux as default OS.

Hope that helps,
Josh
Thanks for sharing and your method  has proven to be another method of setting up a 2 hard drive dualboot.
The Desktop Live CD doesn't allow you to select where to install grub, so the "howto" I described ensures that grub doesn't overwrite your Windows mbr...definitely takes a little longer disconnecting and reconnecting drives.  I assumed there were other methods of setting up a dualboot(2 hard drives) without installing grub to the Windows mbr and I welcome anyone adding to this "howto" with an alternate installation option.

Update:  Starting with Ubuntu Feisty 7.04, the Desktop Live CD does allow you to specify where to install grub by clicking on the "Advanced" button during installation & typing in a different location, instead of the default (hd0)...e.g. you could enter /dev/sda, /dev/sdb, etc.

---

### Post by GroverDill on 2006-08-21
```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

This worked great for me, except I orginally had these commands mistyped in grub. It should be noted that there is a SPACE between (hd0) and (hd1) in both the 'map' lines. Otherwise, Grub responds with an error 11: unrecognized device string.

That unix is so literal... :) 

Thanks for the solution, all. It's very cool.

---

### Post by confused57 on 2006-08-22
It's actually better to copy & paste commands and entries, because it is difficult to tell where the spaces are in the typed commands, etc.

---

### Post by mxreader on 2006-09-06
I am trying to find a solution to getting Ubuntu to boot off Grub on the IDE XP MBR (Ubuntu is on SATA).  I am reading here to see if I can learn something that may help.

The early post gave a link
[http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://www.ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata)

but there the commands are: 
6. In Ubuntu go to Applications/System Tools/Terminal. You will need to open a text editor and change the grub menu file:
$cd /boot/grub
$sudo gedit menu.lst
now look for an entry (near the end) that reads like something like this:

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
chainloader +1

and change it to this:

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
chainloader +1

7. save the file
8. reboot and test boot into XP

Notice the difference in the map ..... commands?
man I am confused now.

---

### Post by confused57 on 2006-09-06
I've always entered the mapping commands as shown in my earlier post, which have worked for me...I'm not familiar with entering them the way you pointed out from the link.

I'm assuming you're able to boot Ubuntu and not Windows...when you installed Ubuntu to the SATA drive you had both drives connected?

If you're able to boot Ubuntu, what is your entry in /boot/grub/menu.lst for booting it, e.g. root (hd0,0) or root (hd1,0)?

If you will, post the output of:
```
sudo fdisk -l
```
The -l is a small "L".

As a note, when there is a combination of IDE and SATA drives, Ubuntu usually installs grub to the IDE drive...therefore, it's probably recommended for someone doing fresh installs to install Windows to the SATA drive, then Ubuntu to the IDE drive.

Since you have Windows on the IDE drive, I would think an entry similar to this would boot it:
 ```
title         Windows XP
 root          (hd0,0)
 makeactive
 chainloader   +1
```

---

### Post by mxreader on 2006-09-07
> **confused57 said:**
> 
I'm assuming you're able to boot Ubuntu and not Windows...when you installed Ubuntu to the SATA drive you had both drives connected? 
No, otherway, I can't boot into the installed Ubuntu (eventhough the installation seemed to work fine). Fortunately I can select XP from the GRUB (I'm using XP now).

I can also boot up from the liveCD and then press F6 to boot the liveCD Ubuntu.

> **confused57 said:**
> 
If you're able to boot Ubuntu, what is your entry in /boot/grub/menu.lst for booting it, e.g. root (hd0,0) or root (hd1,0)?

If you will, post the output of:
```
sudo fdisk -l
```
The -l is a small "L".

I got 3 problems with the Ubuntu install. I cannot mount the Ubuntu filesystem. The other prob. is that I cannot get Wireless working... (note: I got the DWL-G520+ working in Breezy by modifying the interfaces file).

Sooo... its not possible to copy and paste commands and outputs.

Anyway, I did the fdisk -l and this is more or less what came up:

Disk /dev/hda: 80.0 G....
Device   Boot   Start....
/dev/hda1 * ...........................HPFS/NTFS
/dev/hda2 .............................W95 Ext'd (LBA)
/dev/hda5 .............................HPFS/NTFS
/dev/hda6 .............................HPFS/NTFS

Disk /dev/sda: 80.0 G....
Device   Boot   Start....
/dev/sda1 * ...........................Linux
/dev/sda2 .............................Extended
/dev/sda5 .............................Linux swap...

I tried the mounting instructions given at "hermanzone" to mount Ubuntu from a liveCD... at least I think I am doing that.

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu

But I got an error message:
"Wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error....".

OK I must be typing wrong mount instruction to mount Ubuntu?

> **confused57 said:**
> As a note, when there is a combination of IDE and SATA drives, Ubuntu usually installs grub to the IDE drive...therefore, it's probably recommended for someone doing fresh installs to install Windows to the SATA drive, then Ubuntu to the IDE drive.
Mine is not a fresh install of XP, but a fresh install of Ubuntu.

---

### Post by confused57 on 2006-09-07
You could install the driver in Windows to read your Ubuntu Linux drive:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

I'm assuming again, but it's probable that Ubuntu installed grub to your IDE drive...so if you removed Ubuntu, you might not be able to boot Windows.  Here's a guide to repairing your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

When the grub menu is displayed, try highlighting your entry to boot Ubuntu and pressing "e" for edit and see what is there(should be root (hd1,0)...I assume the root for booting Windows is (hd0,0).

Here's an excellent guide for reinstalling grub from the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

I don't know how comfortable you are with disconnecting and connecting hard drives, but if it were my system and none of the above methods worked...I'd consider repairing the Windows mbr using the guide above, with the SATA drive disconnected, once I got Windows mbr repaired and booting properly...I'd disconnect the IDE drive, reconnect the SATA drive and install Ubuntu...and if Ubuntu installs and works OK, maybe using bios to determine which drive to boot into.   I've seen other posters use this method for dualbooting, just an option.  Another option, "might" be to set the SATA to boot to first and put a Windows entry in grub to boot the IDE drive similar to the one I mentioned in my first post in this thread.

I'm just throwing out ideas that you may or may not want to try...I don't use SATA drives, so I can't give you any guidance from experience.  Is your SATA controller on your mobo or is it pci, which can be quite problematic?  There is probably a working solution, but you'll just have to try some different things(after backing up any important data you don't want to lose).  Good luck.

Add: Here's a link discussing SATA & Linux issues:
[http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

---

### Post by mxreader on 2006-09-07
Thanks confused57.

I think I will not attempt the driver installation because it says Ext2, and the commands that I've been told to try (for mounting) are Ext3.  Sounds risky.

The answer to the next two questions you asked are yes.

Since I can't seem to mount the installed Ubuntu from the liveCD, there is no point to fixing the GRUB soooo I think your solution to dualbooting using BIOS to select (which I have used before in Breezy) is the one I will attempt next.

I just hope that the fixmbr is going to work OK.  I've got the genuine XP CD so I will use the Recovery Console path.

Cheers mate.

---

### Post by mo79 on 2006-10-12
Hi confused57,

I have a Dell Dim. 4550 and just want to ask/confirm that Dell's boot menu and boot sequence only allow you to choose the master drive don't they? So the only way to dual boot without Grub writing over the WinXP boot record is to follow your instructions at the start of this thread?
Alternatively, do you know if it's possible to have a boot floppy that when read will automatically/manually boot the secondary drive (i.e. in this scenario XP would be master, Ubuntu slave, and unless the boot floppy [or even a boot CD] is in then XP will be the default drive to load)?
I was looking at this [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php) ...

Cheers for any light. ;)

---

### Post by confused57 on 2006-10-12
> **mo79 said:**
> Hi confused57,

I have a Dell Dim. 4550 and just want to ask/confirm that Dell's boot menu and boot sequence only allow you to choose the master drive don't they? So the only way to dual boot without Grub writing over the WinXP boot record is to follow your instructions at the start of this thread?
Alternatively, do you know if it's possible to have a boot floppy that when read will automatically/manually boot the secondary drive (i.e. in this scenario XP would be master, Ubuntu slave, and unless the boot floppy [or even a boot CD] is in then XP will be the default drive to load)?
I was looking at this [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php) ...

Cheers for any light. ;)

My Dell works great set up the way I outlined at the beginning of this thread...it automatically boots into Windows... in fact, if the grub menu wasn't displayed, you'd never know I had Ubuntu installed on another drive.  The mapping commands fool Windows into thinking it is the first hard drive, so it boots with no problems...be sure to also read the section on installing on a Dell Dimension 4550(set hd1 to "auto" and use rootnoverify (hd1,1), since the 1st partition is a Dell utility).  I used rootnoverify by mistake & it worked OK, so I didn't go back and change it to root (hd1,1), as described.

Yes, you could install grub to floppy, using the alternate install cd:
[http://www.ubuntuforums.org/showthread.php?t=188819](http://www.ubuntuforums.org/showthread.php?t=188819)

---

### Post by shoki on 2006-10-17
Is there anyway to have it so ubuntu starts first unless you go into the menu?
I use ubuntu 99 percent of the time and having to catch grub to boot to ubuntu everytime is a pain.

Thanks,
--Shoki

---

### Post by confused57 on 2006-10-17
> **shoki said:**
> Is there anyway to have it so ubuntu starts first unless you go into the menu?
I use ubuntu 99 percent of the time and having to catch grub to boot to ubuntu everytime is a pain.

Thanks,
--Shoki
Yes, just move your Windows entry to the very end of your /boot/grub/menu.lst...just follow the directions at the beginning of this thread to backup your menu.lst, before making changes.

---

### Post by shoki on 2006-10-18
Awesome!

Thanks again. I did do this before getting the reply and it could not be more simple to set up. Really cool.

--Shoki

---

### Post by pcawdron on 2006-11-06
Excellent instructions, just copy and paste and away we go...

Hey, one question, how do I reverse the order? At the moment the default is windows. How do I make it second in the list so the default is Ubuntu?

I wasn't game to play around with the settings in the file without asking.

Many thanks,
Peter

---

### Post by confused57 on 2006-11-06
> **pcawdron said:**
> Excellent instructions, just copy and paste and away we go...

Hey, one question, how do I reverse the order? At the moment the default is windows. How do I make it second in the list so the default is Ubuntu?

I wasn't game to play around with the settings in the file without asking.

Many thanks,
Peter
That's no problem, just move your Windows entry to very end of the menu.lst file...you can copy & paste or retype, then delete the other entry...probably wouldn't hurt to make a backup of your menu.lst, before you make the changes(see instructions at the beginning of this thread).

---

### Post by Village on 2006-11-23
Alright,

I've done as the HowTo suggested and I've got my computer to boot XP first on my Dell 4550 (I also had to do the bit with changing the hd1,0).

Now my question is though;

I have a third IDE Hard Drive, which has all my windows files on it. What's the best and safest way to install that to only be found by my Windows OS?

Currently my Ubuntu 6.10 is on IDE1 and Windows on IDE2, I have a third though a PCI adapter that I was planning on attaching the "storage" HDD on.

Any suggestions?

Thanks in advance,

Village

---

### Post by BarFly on 2006-12-06
Wow, that works nicely.  Thank you all.  I've had the cover off of my computer for quite some time, thinking I will figure out how to dual boot from two HDD's...  Never had the time until now when I am sick as a dog and not at work.

---

### Post by strange_cathect on 2007-01-11
**A little help?**

I followed these directions for dualbooting Ubuntu and XP on two separate Hard Drives.  But it hasn't been successful.  

1. I disconnected the HD with XP on it and hooked up the new drive using the cables from the original drive.  Ubuntu installed perfectly.  I updated and was able to boot into Ubuntu without problems.

2. I then proceeded to edit the menu.lst file as directed in this post.  I used cut-and-paste.

3. On reboot, I initially got an error message that the "drive doesn't exist."  

4. Now my machine boots to windows every time after briefly flashing Grub on startup.  I am unable to boot into Ubuntu.

Any ideas?

---

### Post by confused57 on 2007-01-11
> **strange_cathect said:**
> **A little help?**

I followed these directions for dualbooting Ubuntu and XP on two separate Hard Drives.  But it hasn't been successful.  

1. I disconnected the HD with XP on it and hooked up the new drive using the cables from the original drive.  Ubuntu installed perfectly.  I updated and was able to boot into Ubuntu without problems.

2. I then proceeded to edit the menu.lst file as directed in this post.  I used cut-and-paste.

3. On reboot, I initially got an error message that the "drive doesn't exist."  

4. Now my machine boots to windows every time after briefly flashing Grub on startup.  I am unable to boot into Ubuntu.

Any ideas?
Did you change the timeout in your menu.lst to something like 10(seconds), the default is 3 seconds and you definitely do not want to reduce the time?
If you have enough time when grub briefly flashes, press your arrow down key...hopefully, this will highlight your Ubuntu entry.
   The only thing I can think  is to make sure your hard drive jumper settings are correct and go into your bios setup & make sure both drives are set to "auto" or "enabled".

---

### Post by Haupt on 2007-01-12
I have 2 SATA HD's in my laptop(HP dv8000t). and i dont know how master and slave works with my setup. My windows is on my primary drive and my secondary is only formatted so far to NTFS. and because its a laptop i dont what would happen if i replace the primary drive with the secondary. Plz help.

---

### Post by confused57 on 2007-01-13
> **Haupt said:**
> I have 2 SATA HD's in my laptop(HP dv8000t). and i dont know how master and slave works with my setup. My windows is on my primary drive and my secondary is only formatted so far to NTFS. and because its a laptop i dont what would happen if i replace the primary drive with the secondary. Plz help.
See reply #22 by bulldog, in this thread:
[http://www.ubuntuforums.org/showthread.php?t=275728&page=3](http://www.ubuntuforums.org/showthread.php?t=275728&page=3)
He was able to set his system up without disconnecting his Windows drive by setting his bios to boot first from the drive he was going to install Ubuntu on.  You "might" be able to do this by setting your 2nd hard drive to boot first(drive you're going to install Ubuntu on).  You're right, master & slave doesn't apply to SATA drives, you just have SATA controller 1 with Windows and controller 2 with your other hard drive.  If you want to be absolutely sure that your Windows mbr isn't overwritten, you'd probably need to disconnect your Windows drive...you may be able to leave your other drive connected, as is, select in bios to boot first to this drive & install Ubuntu on it.   Add your Windows entry in /boot/grub/menu.lst, reconnect your Windows drive & bootup with your Ubuntu drive as the first boot device.

If you want to PM bulldog about his method, feel free...he's quite knowledgable with dualbooting and is willing to assist anyone with their setup.

I assume you're using the desktop live cd to test your system, if you are, you might want to boot up the live cd, open a terminal(Applications---Accessories---Terminal),enter:
```
sudo fdisk -l
```
The -l is a small "L".
If Ubuntu detects both your SATA drives, you shouldn't have any problems installing.
The biggest problem Ubuntu has had in the past is detecting some of the newer SATA controllers, but that is improving in newer versions of Ubuntu with newer kernels.

The desktop live cd automatically installs grub to the mbr(if the drive you're installing Ubuntu on is the first boot device, it "should" install on this drive), however the alternate install cd allows you to select where to install grub(mbr, floppy, partition)...I've always installed with the alternate cd.
If you want to consider the alternate cd, here's an excellent guide(with screenshots):
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I know this a lot of info to digest and feel free to ask if anything is unclear.

If you leave your Windows drive connected during install and it's mbr gets overwritten, it can be repaired:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Good Luck...

Added:   The results of "sudo fdisk -l" should show your SATA drive connected to controller #1 as sda, and controller #2 as sdb...if you select in bios to boot first to the drive on controller #2 when installing Ubuntu, it will be designated hd0 in grub and the Windows drive on #1 will be hd1.
If you switched the drive you want to install Ubuntu on to controller #1, set it in your bios to boot first, then sda would be hd0, and sdb with Windows would hd1...sda and sdb just refers to which SATA controller the drive is connected to, but whichever drive is selected to boot first is hd0 in grub...

---

### Post by Haupt on 2007-01-13
My bios only has Notebook Hard Drive as the hard drive in boot order but it sees my other hard drive other places. so i cant change my boot order. next week i'll try taking out the windows HD. Thanks for the help!! :)

UPDATE**
i tried to install today but it keep freezing right when it loading the kernel and my computer started making odd noises. :(  Plz help.

---

### Post by tankhead on 2007-01-17
Hello, 

This sounds fantastic, its exactly what I have been looking for!
I am still learning so my trouble shooting skills are not there yet.

I have set up both my Xubuntu and Win 2000 Pro IDE drives as Master and Slave, respectively.
I have copied and pasted into the script into the menu.lst the following:

title              Windows 2000
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

but whenever i select the Win2000Pro at start up my screen goes blank, but the monitor does not to to rest mode. 
And it does nothing....

If i go into the bios and reslect either of the drives they will boot perfectly.

Does this not work with Xubuntu or win2000 for any reason? or because they are both IDE drives? 

Any suggestions?

Many thanks!

---

### Post by confused57 on 2007-01-17
> **tankhead said:**
> Hello, 

This sounds fantastic, its exactly what I have been looking for!
I am still learning so my trouble shooting skills are not there yet.

I have set up both my Xubuntu and Win 2000 Pro IDE drives as Master and Slave, respectively.
I have copied and pasted into the script into the menu.lst the following:

title              Windows 2000
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

but whenever i select the Win2000Pro at start up my screen goes blank, but the monitor does not to to rest mode. 
And it does nothing....

If i go into the bios and reslect either of the drives they will boot perfectly.

Does this not work with Xubuntu or win2000 for any reason? or because they are both IDE drives? 

Any suggestions?

Many thanks!

It should work fine with Xubuntu, you could try rootnoverify (hd1,0), instead of root (hd1,0).

Also, you might want to post the output of:
```
sudo fdisk -l
```
The -l is a small "L".

This will show your partition tables & might help troubleshoot your problem.

---

### Post by tankhead on 2007-01-17
Thank you for the reply,

I tried the rootnoverify change with no change in behaviour.

here is the fdisk -l output:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9642    77449333+  83  Linux
/dev/hda2            9643        9729      698827+   5  Extended
/dev/hda5            9643        9729      698796   82  Linux swap / Solaris

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3649    29310561    7  HPFS/NTFS


Thank you,

Peter

---

### Post by confused57 on 2007-01-17
The Windows entry in grub "should" boot your Windows drive, based on the output of "sudo fdisk -l".   Make not make a difference, but you can try rearranging the lines in the entry:
```
title            Windows 2000 Pro
rootnoverify       (hd1,0)
map                  (hd0) (hd1)
map                  (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

then maybe try adding **boot** on a separate line below chainloader +1 , if the above doesn't work.

The only other things I can think of would be to make sure your slave drive jumper is correct(which it probably is, since you're able to boot from bios) and maybe check in bios for the slave drive settings(auto or enabled)...I'm just grasping at straws here, because the grub entry looks OK to boot Windows.

I'll check back if I can come up with something else...if you can't get Windows to boot from grub, you might want to start a new thread with a descriptive title in the Installation & Upgrade section of the forum.

---

### Post by Dominicus on 2007-01-20
Tried this method tonight but I'm having problems with it.  I believe I'm almost there.  When GRUB redirects to the WinXP boot, I get:
```
Error 25: Disk read error
```

I then land on the Grub menu and can only boot to Ubuntu.

My **fdisk -l** output:
```
Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+  83  Linux
/dev/hda2            1217        4255    24410767+  83  Linux
/dev/hda3           24079       24321     1951897+  82  Linux swap / Solaris
/dev/hda4            4256       24078   159228247+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19929   160079661    7  HPFS/NTFS

```
My **menu.lst** snippet to load XP is per top instructions:
```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

Here's one that caught my attention: the **device.map** only has one entry:
```
(hd0)	/dev/hda

```

The **fstab** file also seems to be missing the WinXP hdb entry:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1d1f812f-d99a-4c9e-a315-105d374eae4d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=86b9a0aa-ed38-4179-b991-da9c9477da22 /home           ext3    defaults        0       2
# /dev/hda4
UUID=1e1fa41b-1c1a-48c7-b79f-daddcbfaccef /storage        ext3    defaults        0       2
# /dev/hda3
UUID=06254dcd-6b2d-4bcd-991a-088728f48c17 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

```

Is there a way to trigger Edgy to load the WinXP slave hard drive?

---

### Post by confused57 on 2007-01-20
Here's a description of grub error 25 & possible solutions:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#25)

Checking in bios that the slave drive controller is "enabled" or set to "auto", as well as suggestions in the above link, would be the first things that you might need to check.  
If none of the above works, you might need to make sure your slave drive jumper is set correctly & your IDE cable is seated properly.

---

### Post by Dominicus on 2007-01-20
I'm still trying to figure this out.  I'll give a read to your suggestion.

If I boot to Ubuntu, I'm able to mount the WinXP drive and access the files with no problem.  My BIOS has this slave drive properly identified (i.e. lists as "Hard Disk" and reads the correct capacity and model).  The drive jumper is set to C-Sel to allow the BIOS to map as slave following its position in the cable.

So, I don't think this is an access problem, at least not while in Ubuntu.

Thanks for any additional thoughts.  Dominicus

---

### Post by Dominicus on 2007-01-20
I tried changing the "boot" part to "bootnoverify" and I did get different failure.  Now Grub errors out with:
```
Error 5: Partition table invalid or corrupt
```
Hitting any key kicks me to the Grub menu and I'm able to boot Edgy.  Darn!  I'm writing from Edgy now and was able to permanently mount the WinXP hard disk to /media/windows, so Linux can in fact access this drive, but Grub doesn't seem to be able to pass the booting batton to load Windows.
Dual booting by switching IDE cables was not my idea of fun...Dominicus

---

### Post by confused57 on 2007-01-21
You might want to try to boot Windows, using the Super Grub Disk(approx 1 Mb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

There's also a list of grub errors listed in this link that may be helpful.

The Super Grub Disk is a useful utility tool to have around for booting problems.

Add:  You did mean rootnoverify (hd1,0), instead of bootnoverify?
I wouldn't worry about hdb not showing in your device.map, since your slave drive wasn't connected when you installed Ubuntu.

---

### Post by Dominicus on 2007-01-21
I moved my WinXP hard disk to its original spot as master drive.  I was able to boot into XP with no problems.  Doing some fresh data backups before continuing further with the troubleshooting.

Yes, I added the suffix 'noverify' as explained in some posts and the Grub error changed from "Error 25" (disk read error) to "Error 5" (partition table invalid or corrupt).  Neither these errors make sense to me: if Grub can't read the XP drive, why can Ubuntu mount it?  If the partition table is corrupt, why can I boot perfectly?

I just updated my BIOS just in case.

 Another thing I noticed was Grub had four entries for Linux boot options (instead of the normal 2)

-WindowsXP
**-linux-xxxxxxx-386**
-linux-xxxxxxx-386 (safe mode)
**-linux-xxxxxxx-generic**
-linux-xxxxxxx-generic (safe mode)
-memtest...

Selecting the "386" option will actually boot correctly.  Taking the "generic" path results in a broken X-server.  I'll keep searching for solution!

---

### Post by Dominicus on 2007-01-21
Several repairs, even re-installed Edgy into single partition.  This removed the xxx-386 entries I had in the Grub menu, but Grub cannot get past this "Error 25"

I read about the Super Grub Disk, but I couldn't find enough documentation for me to trust myself not to mess my WinXP instead of fixing the boot issue.  I believe the beauty of this method was you pull the XP drive out of the equation while you fiddle with Ubuntu, then just bring XP at the end with no change.  Super Grub disk requires both hard drives installed for  troubleshooting.

This is quite frustrating, what next?!

UPDATE: I did venture creating a Super Grub disk and trying to setup the Windows boot from slave position, but it also reports "Error 25".

UPDATE2: Gave up on this dual-boot setup.  Grub did not cooperate.  I guess I'll never know what was the issue causing the error.  Here's what I ended up doing:
-Switched back the hard drives with WinXP as master and Linux as slave
-[Backed up the MBR]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd") of my XP master drive (just in case)
-Ran the regular Edgy desktop install CD (not the alternate).  Gparted detected both drives and all the partitions I had done before with no problems
-Mapped the master NTFS drive to be mounted as /media/windows and made sure to uncheck format flag
-Mapped the slave partitions, and checked to format both '/' and '/home' partitions
-Grub got installed into the XP MBR and alas! a clean dual boot

Now I'm up...I can finally close the PC case and move to customizing the install.

I've got a dual-boot system.

---

### Post by Village on 2007-01-24
Hi
I've got a Dell Dimension 4550 and I seem to be having problems. I've got two HDDs, one with Ubuntu and one with Windows. Currently Ubuntu is in HD1 and Windows HD2. 
I've followed what you say about your GRUB menu and I've switched the drive to Auto. 

I've been trying to set it up so that Ubuntu boots first and I can use Windows for Games etc, when I select it. 

Now when I switch my computer on it now pops up with;
> 
Primary Had disk drive 1 not found

strike the F1 key to continue, F2 to run the setup utility

I hit F1 and I get to the GRUB, which can boot Ubuntu but if I try to boot Windows I still get the Error 21: Selected disk does not exist message.

Any suggestions?

Thanks, is it just the 4550 that is like this?

Village

---

### Post by Village on 2007-01-26
Ok, thought I would post my sudo fdisk -l if it helps.

> Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       23944   192330148+  83  Linux
/dev/hda2           23945       24321     3028252+   5  Extended
/dev/hda5           23945       24321     3028221   82  Linux swap / Solaris
alex@alex-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=8601ca78-c262-4017-b686-39f49c8d933d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6ba7751a-3ff5-41f6-8223-9dc22cc1c196 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0


Any advice, I'm pulling my hair out!

---

### Post by confused57 on 2007-01-26
> **Village said:**
> Ok, thought I would post my sudo fdisk -l if it helps.



Any advice, I'm pulling my hair out!
Was your hdb with Windows connected when you did fdisk -l?
If it was, then you might want to check the jumper settings & make sure the IDE connector is fully & correctly inserted, as well as, the power connection.

I don't really know what else to look for, setting the slave drive controller to "auto" in bios corrected the grub error 21 for me...you might want to start another thread in the Beginner's section & maybe someone more experienced with computers can give you a solution...Good Luck.

---

### Post by gorilla_king on 2007-01-26
thanks for this guide. i have been using ubuntu solely for the last year and a half and started get butt loads of buissness and need a windows machine to run some of the progs cause vmware was too slow and wine was unrealiable. so i added a 80 gig hard drive i had laying around. so thanks i had success with editing grub the normal way.

---

### Post by Gorlist on 2007-01-27
Hi! right I also posted this else where on the forums encase its not directly Grub related...

Anyhow ive edited my Grub menu as suggested in the first post, rebooted and it loads fine, displays Windows XP and Ubuntu.. I can then boot into Windows with no problems, though if I select Ubuntu it comes up with:

[B]/bin/sh: can't access tty ; job control turned off 
(Along with a number of file or root errors above?)[/B]

If I then turn off the PC, unplug the Windows driver and restart, select Ubuntu from the Grub load it will then goes in fine without any issues.

Both harddrives are SATA.

Couple of side question:

  - Grub doesn't seem to be work with my USB wireless Keyboard (though Legacy is turned on in Bios, & keyboard works fine for Bios.) 

  - How can I change the order displayed on the Grub, and remove old Kernals (I have read up on this though found it confusing). 

Any suggestions would be greatly appreciated!

---

### Post by geek_Man on 2007-01-27
> **Gorlist said:**
> <snip />
 - How can I <snip /> remove old Kernals (I have read up on this though found it confusing). 


Just put double hashes and a whitespace to the left of all the old kernel stuff. That should make it all disappear, but still be in the file in case you need it.

---

### Post by Michl on 2007-02-22
Alexander Grundner on:
[http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)

has a set of very easy instructions for ubuntu on the master and windows on the
slave that does not involve any editing of the menu.lst file.  He writes:

"When you boot up the PC for the first time you'll see the GRUB boot loader shown here. Ubuntu is selected by default and gives you the option to scroll down and boot into Windows if you prefer.

Side note: Ubuntu is actually smart enough during the install process to detect you have Windows installed on your SLAVE drive and configures GRUB for you."

Later he writes that nothing is changed on the windows drive and if you want to
boot into windows directly without grub, you just make that disk the master.

Any views on this?  I am just getting ready to install ubuntu on two disks, want to
make linux first, but don't want to change anything on the windows disk.  ANd
of course, want this to be smooth as silk.  :lolflag: 

Michl

---

### Post by confused57 on 2007-02-22
> **Michl said:**
> Alexander Grundner on:
[http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)

has a set of very easy instructions for ubuntu on the master and windows on the
slave that does not involve any editing of the menu.lst file.  He writes:

"When you boot up the PC for the first time you'll see the GRUB boot loader shown here. Ubuntu is selected by default and gives you the option to scroll down and boot into Windows if you prefer.

Side note: Ubuntu is actually smart enough during the install process to detect you have Windows installed on your SLAVE drive and configures GRUB for you."

Later he writes that nothing is changed on the windows drive and if you want to
boot into windows directly without grub, you just make that disk the master.

Any views on this?  I am just getting ready to install ubuntu on two disks, want to
make linux first, but don't want to change anything on the windows disk.  ANd
of course, want this to be smooth as silk.  :lolflag: 

Michl

Yes, this should work, Ubuntu would be hd0(the "master" drive) and does add an entry to boot Windows without affecting the Windows mbr...when I first wrote the "howto", I was quite unfamiliar with Ubuntu or Linux and I wanted to be absolutely sure the Windows mbr wasn't overwritten...later on, I found out that the method that you found in the link should work...I've read of other people reporting this has worked for them.  Ubuntu installer will automatically install grub to the hd0 mbr(Ubuntu), unless you choose otherwise, which in your case, you'd go with hd0.
As long as you've selected your Ubuntu drive as the first boot hard drive in bios(which would make it hd0), you shouldn't have any problems.

Don't try it, but you could probably install Ubuntu to your slave drive & if it's set in bios as your first booted hard drive, it "should" be recognized as hd0, even though it's connected to hdb.  That's where people get into trouble installing on a pc with multiple hard drives, especially if there is a mix of IDE & SATA...Ubuntu may be installed on the 3rd hard drive set up to boot in bios, but grub is automatically installed to hd0, whichever hard drive is set to boot first.   The Ubuntu installer is quite "adept" at detecting other OS and including entries in grub to boot them...you can't just go changing boot order, or switching hard drive positions after Ubuntu is installed and expect a system to boot...changes can be made to grub, but you have to "jump through hoops" & understand how grub works to get everything reconfigured in grub.
Thanks for bringing this up, let us know how your install went...good luck.

Alexander Grudner's new location for his how'to, thanks to ssican(post #150):
[http://www.alexandergrundner.com/2007/12/17/how-to-dual-boot-windows-and-ubuntu-with-two-drives/](http://www.alexandergrundner.com/2007/12/17/how-to-dual-boot-windows-and-ubuntu-with-two-drives/)

---

### Post by Michl on 2007-02-25
Well, I am installed with ubuntu on the master.  This part seems to
work.  But now I am running into many new questions.   Need to
take it slow.
Michl

---

### Post by beachreader on 2007-04-05
Does any one know if the  above code for a dual boot involving 2 hard drives win 98 (master) and lunix. thanks

---

### Post by beachreader on 2007-04-05
will this dual boot solution also work with WIN 98 ? thks

---

### Post by confused57 on 2007-04-05
> **beachreader said:**
> Does any one know if the  above code for a dual boot involving 2 hard drives win 98 (master) and lunix. thanks
Yes, the mapping commands will work just as well with win98...You can have Ubuntu as master, set it to boot first in bios before installing(you can disconnect the Windows drive when you install, if you want to be sure)...or set your slave to boot first in bios, install Ubuntu to the slave drive.

---

### Post by tech_tronic on 2007-04-16
Whats up, this is my first post and i've been trying to search for someone with a situation similar to my own.  Basically my Windows drive is my 3rd Master and my Ubuntu drive is my 4th Master, both SATA drives... When i installed Ubuntu i disconnected my Windows drive to avoid grub overwriting the mbr and everything was successful.  Today i plug my Windows drive back in and i can boot to that drive just fine using bios selection menu with both drives connected but not Ubuntu, when i disconnect the Windows drive again i can boot to my Ubuntu drive just fine...

With both drives connected Ubuntu starts to load then i get a black screen with this message

/bin/sh: can't access ttyl; Job control turned off
(initramfs)


Sorry if this is a primitive question but im so close to having everything work after the past two weeks with even worse luck, this is the farthest i've gotten.  I would like to achieve this using bios without having to mess with grub because thats how i destroyed my windows partitions before, and fixmbr of course did not work for me, thats why i decided to get a second drive solely for Ubuntu, I appreciate any input anyone has to help me out, Thanks and glad to be a part of the community

Here is an error message....i think the drive is supposed to be mounted where my windows drive currently is since it was unplugged during install

mounting /dev/sda1 on /root failed: no such device
mounting /root/dev on /dev/ static /dev failed: no such file or directory
mounting /sys on /root /sys failed: no such file or directory
mounting /proc on /root /proc failed: no such file or directory
target file system doesn't have /sbin /init

---

### Post by confused57 on 2007-04-16
I just happen to be trying to help someone else in very much the same situation:
[http://ubuntuforums.org/showthread.php?t=409355](http://ubuntuforums.org/showthread.php?t=409355)

I believe your Ubuntu drive is identified differently when your Windows drive is connected vs. when your Ubuntu drive is connected by itself.  See my last reply in the above thread.

With both your drives connected, boot up the live cd, open a terminal, enter:
```
sudo fdisk -l
```
the -l is a small "L"
this should show how your Ubuntu & Window's drives are identified with both connected.

I'll repeat what I suggested in the thread:  remove the live cd, boot your pc, at the grub menu, highlight your Ubuntu entry, press "e", then in the kernel line change the root to whatever "fdisk -l" returns(e.g. root=/dev/sda1), then press "b" to boot.  This change is temporary, but can be made permanent by editing your /boot/grub/menu.lst  & changing your #kopt line in menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

Added:  You may want to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
the SGD download page has been down the past few days, so this may not currently be an option.
Another possiblity, which may or may not work, is to switch the SATA controller connections for the hard drives when both drives are connected?

---

### Post by tech_tronic on 2007-04-16
Confused thanks for the info, i had intentions of switching the sata cables around first before i read your post and decided to give it a shot after you suggested it....well it worked! im guessing because now the Ubuntu drive thinks or is sda1 again(3rd Master)which is where it needs to be mounted in order to boot correctly...each drive connected individually would be sda1 then once i reconnected the windows drive it pushed the ubuntu to sdb1? or whatever, thats why i got the error message.....I'm running xp and vista on one drive and Ubuntu on the other everything is working, it seems i can boot all three of my OS's finally w/o having to reconnect drives, Thanks for your help.

---

### Post by Signpost on 2007-04-17
Been reading over this thread and others like it trying to get as much information as possible before I install Ubuntu.  Unfortunately just about every thread I read refers to one SATA and one IDE drive.  I have 2 SATA drives, 1 320gb that has windows xp  installed and an 80gb that has a 2GB Extended Partition (at the end of the unallocated space) used for a windows pagefile.  I plan to use the first section of the 80gb drive for a Ubuntu install, and maybe a small FAT32 partition for swapping files between windows and linux.  

Currently my 320gb is on SER0 and the 80gb is on SER1 connections on the mobo.  Is the method in the OP still the method I should follow or is there something else I have to do for SATA drives?  

I can't wait till Thursday so I can get the new distribution and finally give Linux a try.

---

### Post by confused57 on 2007-04-17
> **Signpost said:**
> Been reading over this thread and others like it trying to get as much information as possible before I install Ubuntu.  Unfortunately just about every thread I read refers to one SATA and one IDE drive.  I have 2 SATA drives, 1 320gb that has windows xp  installed and an 80gb that has a 2GB Extended Partition (at the end of the unallocated space) used for a windows pagefile.  I plan to use the first section of the 80gb drive for a Ubuntu install, and maybe a small FAT32 partition for swapping files between windows and linux.  

Currently my 320gb is on SER0 and the 80gb is on SER1 connections on the mobo.  Is the method in the OP still the method I should follow or is there something else I have to do for SATA drives?  

I can't wait till Thursday so I can get the new distribution and finally give Linux a try.

One option might be to leave your hard drives connected as they are, but in bios set your 80gb drive to boot before your 320gb Window's drive  before you boot up the live cd to install.  By setting your 80gb drive to boot before your 320gb, grub should recognize this drive as (hd0) & install grub to your 80gb mbr and it "should" automatically add an entry to boot Windows.  
The default is to install grub to (hd0), which should be your 80gb drive(if you reset your bios hd boot order)...you can always type in /dev/sdb as the location to install grub, this is assuming the installer recognizes your 80gb drive as sdb.

---

### Post by Signpost on 2007-04-19
Well, I have tried to install Feisty and haven't had much success.  I have the following partitions setup on my 80gb SATA to install Feisty.  
Partition 1 - 62GB Ext3 Mounted to /home 
Partition 2 - 10GB Ext 3 Mounted to /  set as Active Partition
Partition 3 - 1.5GB Swap 
Partition 4 - 2.5GB NTFS Windows Pagefile.

I go through the entire setup steps, no matter what I set my boot order in my BIOS the installer sees my 320gb as sda and my 80gb sdb.  At the final confirmation screen I click the advanced button and change the Boot Installer location from (hd0) to /dev/sdb and then let it install.  After the install it starts to restart, the bar lowers then when its almost about to restart it ejects the disc then says to remove the disc and hit enter.  When I hit enter nothing happens so I have to hard reset with the reset button on my tower.  After the restart (computer still set to boot first from 80gb; boot order is CD, 80gb, 320gb) the GRUB menu appears and I have all the grub options available plus Windows listed at the bottom.  When I click any Ubuntu option it says it is unable to mount the partition,  and when I click Windows it says invalid exe or something similar.  My only choice is to restart the computer and change BIOS to boot from 320gb first and load Windows.

Anyone have any idea what is wrong or what I am doing wrong, or even what I can do to fix it?

---

### Post by confused57 on 2007-04-19
> **Signpost said:**
> Well, I have tried to install Feisty and haven't had much success.  I have the following partitions setup on my 80gb SATA to install Feisty.  
Partition 1 - 62GB Ext3 Mounted to /home 
Partition 2 - 10GB Ext 3 Mounted to /  set as Active Partition
Partition 3 - 1.5GB Swap 
Partition 4 - 2.5GB NTFS Windows Pagefile.

I go through the entire setup steps, no matter what I set my boot order in my BIOS the installer sees my 320gb as sda and my 80gb sdb.  At the final confirmation screen I click the advanced button and change the Boot Installer location from (hd0) to /dev/sdb and then let it install.  After the install it starts to restart, the bar lowers then when its almost about to restart it ejects the disc then says to remove the disc and hit enter.  When I hit enter nothing happens so I have to hard reset with the reset button on my tower.  After the restart (computer still set to boot first from 80gb; boot order is CD, 80gb, 320gb) the GRUB menu appears and I have all the grub options available plus Windows listed at the bottom.  When I click any Ubuntu option it says it is unable to mount the partition,  and when I click Windows it says invalid exe or something similar.  My only choice is to restart the computer and change BIOS to boot from 320gb first and load Windows.

Anyone have any idea what is wrong or what I am doing wrong, or even what I can do to fix it?

What you can try is boot first to your Ubuntu drive, highlight your Ubuntu entry, press "e", then change the line with root to (hd0,x), then press "b" to boot...this is only temporary if it works.  It can be made permanent in your boot/grub/menu.lst & an entry similar to the one in my first post may boot your Window's drive.
You'll also need to change the #groot line in your menu.lst(if the above works):
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

I'm not sure what's going on with grub recognition of your hard drives, unless Feisty id's drives differently from previous versions of Ubuntu.

---

### Post by Signpost on 2007-04-19
Well, I got it working, I just moved the 80gb to SER0 and the 320gb to SER1 on my mobo and set 80gb to first boot.  Everything is up and running.  Now to figure out how to get sound and network access :lolflag:

---

### Post by tech_tronic on 2007-04-21
Hey Signpost are your OS's time synchronization off at all?

---

### Post by Signpost on 2007-04-22
not that I have noticed.  If they are its only a few seconds.

---

### Post by tech_tronic on 2007-04-24
If i boot into an OS consistently the time remains constant but if i boot into ubuntu then back to windows or visa versa the time and date is off...? i think its because i switched the drives around on the mobo?? anyone got any ideas as to what could be causing it? Thanks

---

### Post by confused57 on 2007-04-24
> **tech_tronic said:**
> If i boot into an OS consistently the time remains constant but if i boot into ubuntu then back to windows or visa versa the time and date is off...? i think its because i switched the drives around on the mobo?? anyone got any ideas as to what could be causing it? Thanks

I had the same problem switching between Windows & Ubuntu, this solved it for me:
[http://ubuntuforums.org/showpost.php?p=698200&postcount=5](http://ubuntuforums.org/showpost.php?p=698200&postcount=5)

---

### Post by simon303 on 2007-05-04
I followed these instructions

> **confused57 said:**
> First, disconnect your Windows drive, then connect the drive you want to install Ubuntu on as the primary IDE master drive.  After installing Ubuntu, allow the updater to install all the necessary updates, this may take awhile.  Shutdown your computer and reconnect your Windows drive as slave, then restart, your computer will boot into Ubuntu.

You will need to edit your menu.lst file:
(Open a terminal, copy & paste one line at a time, press "enter" each time)

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

The first line changes to the grub directory, the second line makes a backup of your menu.lst file, and the third line opens the menu.lst file using the gedit text editor.

Copy and paste the following lines above the line
###BEGIN AUTOMAGIC KERNEL LIST
```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Note:  If grub gives an error when rebooting, you can try rootnoverify (hd1,0) instead of root  (hd1,0) in the second line.

To automatically display the grub menu at bootup, find the line
```
hidden
```
 
and replace with 

```
#hidden
```

To adjust the time grub is displayed at bootup, change the timeout(in seconds)...I'd suggest 10 seconds(default is 3).

Quit and save settings.

Now i have a computer that should boot with either winXP or ubuntu (winXP by default)
But it only boots ubuntu, when i try to boot winXP it goes to the loading windows screen, then very rapidly flashes a blue screen error (at least it looks like a blue screen error) then reboots the computer

any ideas??

---

### Post by confused57 on 2007-05-04
Post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

and the boot entries of:
```
gedit /boot/grub/menu.lst
```

Did you try rootnoverify, instead of root...and possibly remove the savedefault line?  Does your Window's drive boot OK, if selected to boot first in bios when still connected as slave?

---

### Post by simon303 on 2007-05-04
i tried rootnoverify, when i unplug the linux drive and boot XP off its drive (still connected as slave) it boots XP fine

---

### Post by confused57 on 2007-05-04
> **simon303 said:**
> i tried rootnoverify, when i unplug the linux drive and boot XP off its drive (still connected as slave) it boots XP fine
Did "sudo fdisk -l" show your Windows on the first partition?  Have you checked in bios with both hard drives connected to see if both drives are recognized correctly & enabled?

You might want to download the Super Grub Disk & see if it will boot your Windows(both drives connected):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Other than root possibly pointing to the wrong partition or something in bios, I'm not sure what's going on with your system.

---

### Post by simon303 on 2007-05-05
"sudo fdisk -l" does show the windows disk as hdb

It all seems to be working now, I disconnected the ubuntu disk and booted windows off the windows disk leaving it set as primary and it booted fine. Then reconnected the ubuntu disk and booted windows using the grub menu and its working fine. Think windows just needed to 'get used to' running off a slave.

Only problem is that when in one os i cant get at the other's disk

---

### Post by fallencyi on 2007-07-04
I just wanted to say thank you to everyone who has posted helpful info in this thread & confused57 for starting it.

  I have been beating my head against a wall trying to figure this out. I found this thread & it for me with minor changes to the menu.lst file for the drive that windows sits on.

Thanks.

---

### Post by Yellowdog428 on 2007-07-20
I just want to thank you!  

I am new to Linux/ubuntu and after installing on a partition on my laptop I wanted to add it to a old Maxtor 40 Gig I had around on my desktop and it worked FLAWLESSLY!!!!!

Followed the instructions on your first post and I now have Ubuntu on my desktop!

Thanks again!
Cheers!

---

### Post by Shampyon on 2007-08-11
I'm about to buy a second SATA HDD. I already have Feisty installed on my current drive, and I want to install a stripped down gaming-specific version of XP on the new drive. Is there anything I need to know before I plug in the new drive and install XP, or will the instructions in the OP be all I need?

---

### Post by confused57 on 2007-08-12
> **Shampyon said:**
> I'm about to buy a second SATA HDD. I already have Feisty installed on my current drive, and I want to install a stripped down gaming-specific version of XP on the new drive. Is there anything I need to know before I plug in the new drive and install XP, or will the instructions in the OP be all I need?

Yes, I would think so...I personally think it would be advisable to disconnect your Feisty drive and connect your drive you're installing Windows to the SATA1 controller(the one I assume the Feisty drive is now connected).  Once you get Windows installed, updated, & configured, then you should be able to reconnect your Feisty drive to the SATA1 controller and your Window's drive to the SATA2 controller.

Then you should be able to follow the directions in the OP to add an entry to boot Windows from grub.  Good luck.

---

### Post by Shampyon on 2007-08-13
Thanks for the help. It's all set up now, ready to rock! Now I've got my loverly pretty Feisty as my main OS with it's ever so pretty compiz desktop, and my stripped-back XP for running all those wonderful games at super-high quality.

---

### Post by inter4ever on 2007-08-15
Hello

I am new to Ubuntu and finally decided to get it installed on my main PC. I am planing to have it installed in dual boot configuration with Windows XP. I have Windows installed on a HDD connected to SATA 1 port. I plan to install Ubuntu on a HDD connected to the SATA 3 port after unplugging the first HDD so that Ubuntu won't modify anything on that drive. After finishing the install I will be using my bios boot menu to choose which system to boot. Is that possible (I mean using the bios to boot windows and ubuntu and not GRUB). Also, if I needed to use GRUB, what should I modify to make it detect Windows after the install? (Again Windows is on SATA 1 and Ubuntu on SATA3).

My PC specifications are: Gigabyte 965p-DQ6 mobo, Intel Core 2 Duo E6600, Corsair 2GB (2*1GB) DDRII ram, WD Raptor 74 GB and Seagate 7200.10 250 GB.

Thanks in advance for answering my questions.

---

### Post by confused57 on 2007-08-15
> **inter4ever said:**
> Hello

I am new to Ubuntu and finally decided to get it installed on my main PC. I am planing to have it installed in dual boot configuration with Windows XP. I have Windows installed on a HDD connected to SATA 1 port. I plan to install Ubuntu on a HDD connected to the SATA 3 port after unplugging the first HDD so that Ubuntu won't modify anything on that drive. After finishing the install I will be using my bios bios boot menu to choose which system to boot. Is that possible (I mean using the bios to boot windows and ubuntu and not GRUB). Also, if I needed to use GRUB, what should I modify to make it detect Windows after the install? (Again Windows is on SATA 1 and Ubuntu on SATA.

My PC specifications are: Gigabyte 965p-DQ6 mobo, Inter Core 2 Duo E6600, Corsair 2GB (2*1GB) DDRII ram, WD Raptor 74 GB and Seagate 7200.10 250 GB.

Thanks in advance for answering my questions.

You shouldn't have any problem using bios to boot the different drives, but you may want to add an entry to your grub menu as outlined in the first post in this thread to boot Windows.  Then you should be able to leave your computer setup to boot first to your Ubuntu drive, from which you can boot Windows...the Window's menu.lst entry described should work for your setup also.

---

### Post by nuddernuby on 2007-08-16
My appreciation for the efforts by lha and confused57 for this very helpful contribution.  I just completed a dual boot 2HDD installation successfully, following your clear instructions - and I'm a newbie!

Now I have one small question (and I hope I haven't missed it in the thread):  Is it possible to switch the order, in other words, to have Ubuntu as the default instead of Windows?

Hope this is not an entirely idiotic question.
Rgds

---

### Post by confused57 on 2007-08-16
> **nuddernuby said:**
> My appreciation for the efforts by lha and confused57 for this very helpful contribution.  I just completed a dual boot 2HDD installation successfully, following your clear instructions - and I'm a newbie!

Now I have one small question (and I hope I haven't missed it in the thread):  Is it possible to switch the order, in other words, to have Ubuntu as the default instead of Windows?

Hope this is not an entirely idiotic question.
Rgds
You might want to check out page index #2 on this site:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

You can change the default to 1, or move your Window's boot entry to the very bottom of your menu.lst.

---

### Post by nuddernuby on 2007-08-16
Thank you, got it working.

---

### Post by freemantle3 on 2007-08-20
trying to dual boot with two drives ubuntu 7.04 & xp pro have followed instructions but when i go to boot up nothing but flashing cursor then it goes into win safe mode
 screen. i am running on a dell demension 9150 with 2 250 gig sata drives. in the bios i can't change to master or slave, just has dvd rom in pata please help

---

### Post by jai_mantravadi on 2007-08-30
What gives?
Basic story is that dual booting with Ubuntu on a second hard drive loading with grub worked, but now it doesn't after attempting to reload the windows MBR, and I can't figure out why. The post is a little long, but I've gone through this thread and attempted most of the fixes mentioned. 

I have two hard drives (actually 3), a primary IDE which I boot windows off of, and a SATA which I boot ubuntu off of (the third HD is an IDE drive which is on a separate controller). It worked great with the default installation! At this point, my Ubuntu sata disk was secondary in boot order and grub came up (level 1.5) configured with Ubuntu as the default, and windows XP as the second option. 

But, when I followed the excellent instructions for running my windows partition in vmware ([http://oopsilon.com/Running-a-Windows-Partition-in-VMware]("http://oopsilon.com/Running-a-Windows-Partition-in-VMware")), I wound up screwing up my setup. I thought that either a grub install or a fdisk /mbr to my windows partition would fix the problem, but I kept getting Grub errors 13 and 17, then after doing the restore to the MBR, I got it so it would boot straight to windows, but leaving me with no grub menu. So, using Super Grub Disk (live demo [http://forjamari.linex.org/forum/forum.php?forum_id=340]("http://forjamari.linex.org/forum/forum.php?forum_id=340")), I played around with making my NT partition non-bootable and hidden with gparted, and got more grub errors. 

Finally I changed my boot order in BIOS... still no dice, Grub boot error 13 when I tried loading Ubuntu. So, I tried Super Grub Disk again, and it will pull up the Grub menu just fine so long as my Ubuntu disk is second in boot order. Or, if Ubuntu's disk is first in the bios, I can boot from grub by changing the disk in Grub's menu from hd1 to hd0 and it will boot Ubuntu (but windows won't boot off the menu). Can anyone tell me what I had on my Windows MBR/partition before I messed it up? Attached is an abbreviatied version of the "default" menu.lst that Ubuntu generated at first. Any help would be appreciated.


[COLOR="Olive"]
timeout         10

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=56725db0-7e79-4276-a0dd-972e9c1cd75f ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

[/COLOR]

Any ideas of what I can change on my windows MBR and keep the menu.lst the same? At this point I'm more curious than frustrated, but I would like to show that I'm able to keep my windows MBR the same, and still boot using grub.

---

### Post by JawsThemeSwimming428 on 2007-08-30
I am thinking about dual booting Windows Vista Home Premium on a Velocity Micro Promagix system, running a Core 2 Duo 6850 with 2GB of 800MHz memory and a 400GB Hitachi HDD. I just got the system and after some KVM issues with USB I decided I can only have one machine. (I have a separate machine that I built that has been running Ubuntu for 2 years). The Ubuntu machine is running Feisty and my question is, if I take the HDD out of my machine that is running Feisty and put it in the Velocity Micro machine what instructions do I need to follow in order to dual boot and will it even work? Thanks.

---

### Post by jai_mantravadi on 2007-08-31
Jaws,
Check out: 
[http://ubuntuforums.org/showthread.php?t=539316]("http://ubuntuforums.org/showthread.php?t=539316")
 for an index of other dual-disk boot setups. 

On the other hand, I used the default Ubuntu guided partition (fresh SATA as second disk, windows IDE as first disk) and it worked fine for me. If you do that though, be careful about tweaking boot order in the bios though (hard drive boot order, putting a CD first or not doesn't seem to affect it) as you may need to reconfigure your grub install. If that happens. Also check out Super Grub Disk for afterwards if your boot configuration gets corrupted (its a live CD with an advanced set of Grub menus for booting off of exisiting drives with bad boot records). 

I don't think too many people read the bottoms of these posts, so I'm going to repost looking for info on my setup. Good luck!
Jai

---

### Post by static_16 on 2007-09-11
Hey, 

I know I should be able to work out what to do from all the other posts but i'm very new to linux and just can't get it to work.

Setup
I have four hard disks 3 ide disks on a raid controller pci card and a Sata hard drive. The sata drive is my main hard drive and has xp installed on it. I've installed ubuntu onto the primary master of ide drives on the pci card. For you to see here is my fdisk:

[COLOR="Blue"]Disk /dev/hde: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        4787    38451546   83  Linux
/dev/hde2            4788        4998     1694857+   5  Extended
/dev/hde5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/hdg: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/hdh: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1               1        4866    39086113+   7  HPFS/NTFS

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table[/COLOR]

Basically i've followed all the steps, ubuntu was installed without the sata drive plugged in so grub was definatly installed on the ubuntu drive. I've changed the grub file to what you specified, here is how it looks:

title              Windows XP
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Basically if you could help me by telling me what the hd? number should be?

Thank you.

EDIT: The 320 GB is the xp drive that i can't point at

---

### Post by Grellin on 2007-09-11
Ok, first, thanks for all the work that has been put into this thread. 

I have followed the directions (I believe) but I still can't get it to work. My primary drive is a 250 gig dedicated to Ubuntu, and the slave drive is a 80 gig with Windows XP. With both connected I can log into Ubuntu without issue. When I select the Windows option from the GRUB menu the screen clears, and says, starting level 2 and does nothing. When I use just root, the machine just reboots when the Windows option is selected. With the rootnoverify it just gives that message and freezes. 

Each drive will load independently and when I am in Ubuntu I can browse the windows file system.  Here is my fdisk readout:
> 
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30121   241946901   83  Linux
/dev/hda2           30122       30401     2249100    5  Extended
/dev/hda5           30122       30401     2249068+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9455    75947256    7  HPFS/NTFS



And here is the menu.lst read out:


> title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6d7d3e88-73d5-4fd8-a325-7ef827c2ad83 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=6d7d3e88-73d5-4fd8-a325-7ef827c2ad83 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6d7d3e88-73d5-4fd8-a325-7ef827c2ad83 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=6d7d3e88-73d5-4fd8-a325-7ef827c2ad83 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

title   	Windows XP
rootnoverify	(hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader   	+1



And here is my device.map :

> (hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/sda

Any suggestions that don't require major brain surgery? Thanks in advance. Also, I have read all the replies here and tried all of the suggestions that seemed relevant.

---

### Post by Grellin on 2007-09-11
Oh, I just double checked the message it gives me and it was: 
> 
Starting up.
Loading Stage2

Then nothing. Just freezes, no keyboard, nothing.

---

### Post by confused57 on 2007-09-12
I've seen this problem, Windows rebooting when selected in grub, reported by other users; however, I haven't seen a definite solution.

I suspect there may be something in bios(or Windows) that is causing the problem.   All of the info that you've provided look OK and Windows "should" boot with the entry that you have.  It may not work, but the only thing I could suggest for you to try is to connect Ubuntu as slave and Windows as master...leave your Windows grub entry as it is and set your bios to boot first to your Ubuntu drive set up as slave.  You may need to edit your device.map to reflect this change:
```
(hd0) /dev/hdb
(hd1) /dev/hda
```

The above  may not work, since you're able to boot Windows on your slave controller when you set bios to boot it first, so it may not be worth the effort for you.  

What is /dev/sda, I didn't see it listed in your "fdisk -l" output?

Sorry I can't help you more...if I find anything, I'll let you know.

Added:  I have 2 different pc's set up this way and /dev/hda(Ubuntu on hda, Windows on hdb)  is the only entry I have in my device.map:
```
(hd0) /dev/hda
```
thought I'd mention this, if you want to try changing your device.map before your try anything else.

---

### Post by Grellin on 2007-09-12
Thanks for the reply. The /dev/sda is just a flash drive. I've tried removing it to see if it was causing conflicts but no go. 

I'll try the device map trick. Can't hurt, right?:confused:

---

### Post by Grellin on 2007-09-12
I was thinking after something you said about the BIOS. I rechecked the settings and found the problem I was having. I had my flash drive set as second boot option and the windows drive as the 3rd. Since there was no boot loader on the flash drive, that is where it was hanging up. 

It all works now, I didn't have to remove or change any of the settings I have posted above. Thanks everyone for the insight and especially thanks confused57 for giving me the clue that worked. :guitar:

---

### Post by confused57 on 2007-09-12
> **Grellin said:**
> I was thinking after something you said about the BIOS. I rechecked the settings and found the problem I was having. I had my flash drive set as second boot option and the windows drive as the 3rd. Since there was no boot loader on the flash drive, that is where it was hanging up. 

It all works now, I didn't have to remove or change any of the settings I have posted above. Thanks everyone for the insight and especially thanks confused57 for giving me the clue that worked. :guitar:
Good job on your part finding the problem.  With my 20/20 hindsight, I should have thought to have you check your bios boot order. I figured something was amiss  when I saw your device.map with /dev/sda, which was not shown in your "fdisk -l"

---

### Post by static_16 on 2007-09-12
Hi,

Sorry to pester but i have everything working except for the grub, has anyone had any ideas?

cheers.

---

### Post by confused57 on 2007-09-12
> **static_16 said:**
> Hi,

Sorry to pester but i have everything working except for the grub, has anyone had any ideas?

cheers.
It's no bother, it's just that I'm not familiar with Raid configurations.  I'm assuming you're able to boot Ubuntu OK.  If you are, you might try various Windows entries in grub & see if one of them will boot, for example:

```
title Windows XP on hd2
rootnoverify (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

and/or

```
title Windows XP on hd3
rootnoverify (hd3,0)
savedefault
makeactive
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1
```

What you could do is go ahead and add both the additional entries to very end of your menu.lst & try booting Windows...try (hd2) first, then (hd3)...good luck with it.

---

### Post by static_16 on 2007-09-13
It was hd3, everything works perfectly now. If it was just me I'd just have ubuntu but my girlfriend loves the sims so I've got to keep xp.

Anyway thanks again for all your help, cheers.

---

### Post by tomot on 2007-09-27
Thanks for this great tutorial:

It finally gave me the confidence to try Dual Booting: (XP & Ubuntu)

For some reason Ubuntu allowed me to Edit grub using Terminal.
even though several times it had asked for "Password:" after I copy/pasted
 sudo cp menu.lst menu.lst_backup into the Terminal window.

I was attempting the same Dual Booting procedure: (XP & Fedora)
on another HDD.

However this time I was unable to get passed the "Password:" entry.
my root password is not accepted, hence I have not been able to edit
grub.

HELP! :)

---

### Post by Sasquatch2000 on 2007-11-05
I remember years ago (over 10 years ago!), using a commercial program called "Partition Magic" I believe it was called. This allowed one to boot various Microsoft OS's, as well as (at the time), SCO unix.

I was hoping there would be something which worked as easily as that available now, and even preferably, something "open source" (RE:free).

Thanks.

---

### Post by CypherHackz on 2007-12-22
I have read the tutorial about how to make dual boot with two hard drives. Kinda understand how to do it but I have a question that I want to ask. Here is the situation.

I have two hard drives, HD1 (120Gb) and HD2 (320Gb). HD1 contains WinXP and HD2 is new so it is empty. I want to install Ubuntu in HD2 and will allocate 20Gb for it. Then what I will do is follow the tutorial steps and do the installation. M

y question is, how I can make my WinXP (which is HD1) as primary and not Ubuntu?  In the tutorial it said make Ubuntu as primary so it will boot using the Grub. But I don't want that. I want to use WinXP boot menu selection. Is it possible?

Thank you.

-cypher.

---

### Post by confused57 on 2007-12-22
> **CypherHackz said:**
> I have read the tutorial about how to make dual boot with two hard drives. Kinda understand how to do it but I have a question that I want to ask. Here is the situation.

I have two hard drives, HD1 (120Gb) and HD2 (320Gb). HD1 contains WinXP and HD2 is new so it is empty. I want to install Ubuntu in HD2 and will allocate 20Gb for it. Then what I will do is follow the tutorial steps and do the installation. M

y question is, how I can make my WinXP (which is HD1) as primary and not Ubuntu?  In the tutorial it said make Ubuntu as primary so it will boot using the Grub. But I don't want that. I want to use WinXP boot menu selection. Is it possible?

Thank you.

-cypher.
I don't have any experience with modifying the boot.ini to boot Ubuntu, but maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=481240&highlight=boot.ini](http://ubuntuforums.org/showthread.php?t=481240&highlight=boot.ini)

WinGrub was mentioned in the thread, that might be an option:
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

Before you try installing Ubuntu, I would recommend burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you have a floppy drive, a WinXP boot floppy might come in handy:
[http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)

---

### Post by CypherHackz on 2007-12-22
Thanks. I think I have found what I want. Here is the article that describe how to make it:

[http://www.linux.com/articles/113945](http://www.linux.com/articles/113945)

And thanks to you for the nice article on how to dual booting WinXP and Ubuntu. ;)

-cypher.

---

### Post by confused57 on 2007-12-22
> **CypherHackz said:**
> Thanks. I think I have found what I want. Here is the article that describe how to make it:

[http://www.linux.com/articles/113945](http://www.linux.com/articles/113945)

And thanks to you for the nice article on how to dual booting WinXP and Ubuntu. ;)

-cypher.
Sounds like the link you found should work quite well...when you install Ubuntu, you can specify where to install grub by pressing the "Advanced" button(I believe it's on step 7)...you can then type in your root partition in place of the default (hd0), for example you can type in /dev/sdb1, or however your root partition is designated in the partitioning & installation steps.

---

### Post by Aqualung on 2007-12-31
God, this "Missing operating system" error has been killing me! Been trying to install Gutsy on my computer (have 7 HDDs, 4 of which are IDE on a Promise card). At first I've tried to dual boot Gutsy w/my Vista Ultimate x64, but I gave that up as it looked impossible. So I simply removed the Windows HDD (got one of 'em nice hot swappable HDD cages), and I was prepared to rejoice at the very sight of my computer booting in Ubuntu (after, of course, installing Ubuntu as if Windows never existed). It just wouldn't work.

So, been reading the forums, and it looks like Ubuntu/Gutsy was not designed to handle both SATA and IDE drives! Gosh, I'm surprised it was designed to use HDDs at all and not punchcards! After all it's only 1982, right?

Anyway, I'll spare you the cheap sarcasm. Some of the posts in this thread keep making reference to some "dualboot two hard drives" tutorial, and it looks to me that I should spend the better part of the week digging through this thread to find it. Can I get one of youse to please repost the link to that tutorial?

Let me tell you what my particular situation is:

4 IDE legacy HDDs on a Promise IDE card;
3 SATA HDDs, among which two blazin' fast 150Gs WD Raptors: one of the Raptors has my Windows, the other was supposed to host Gutsy Ubuntu.

Now, I'd be happy in a first instance to simply boot Ubuntu w/o Windows present. It is only afterwards that I'll be thinking of figuring out a way to dual boot.

So, it should be simple, right?

Please help. I really want to migrate to Linux as Windows has been giving me troubles.

---

### Post by TimPy on 2008-02-02
alright... I now completely (meaning mostly) understand what I need to do.  I need to recover the windows mbr.  I almost did it using my windows recovery disk- but then I couldn't find my admin password.  I can't get onto the internet  off live, so I can't use the one program I found that does it automatically.

Could you give me the exact commands to enter into the super grub disk to restore the windows mbr? I was having trouble finding exactly what to do, and I didn't want to mess up my computer anymore...  That way I can restore windows, and then follow a dualboot guide and overwrite the previous partition I had, making G: my master first this time before I install.

---

### Post by masingerz on 2008-02-11
hey you know what worked for me:

sudo gedit /boot/grub/menu.lst

and type after 
### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd0,0)
chainloader +1


---o---

when I booted and pressed esc, to select the option that says windows, I typed, "E" for edit at the line "rootnoverify (hd0,0)" and then "B" for boot and tried different combinations (0.1 0.2 1.0 1.1)
and the one that worked was 
"rootnoverify (hd1,0)" that booted into windows, so i let it do a complete boot and the rebooted that and went into ubuntu back again to 

sudo gedit /boot/grub/menu.lst


and change the line

rootnoverify (hd0,0)

to 

rootnoverify (hd1,0)

and now it works

I would like to thank the academy, its an honor to be nominated

PS thanx forum and freenode #ubuntu

---

### Post by tantric132 on 2008-02-13
Thank you for the guides Confused!

---

### Post by malbecar on 2008-03-20
Hi, I readed your post, and copy the code. Just work great!
Many thanks!

---

### Post by gr8gatzb on 2008-04-03
I used this setup with 7.10 and it worked fine (the problem I am posting about didn't come up), but I ended up re-installing with 6.06 because I wanted more stability. It works fine with 6.06 too, but now I am having trouble accessing my Windows drive from Ubuntu. It gives me permission errors whenever I try accessing it after mounting. It says it belongs to root. When I do 'su', I can then access it via the terminal. However, I can't access it any other way. It is read-only and root/root group and owner. Not sure if this is related to this setup or another issue. Any ideas?

---

### Post by confused57 on 2008-04-03
> **gr8gatzb said:**
> I used this setup with 7.10 and it worked fine (the problem I am posting about didn't come up), but I ended up re-installing with 6.06 because I wanted more stability. It works fine with 6.06 too, but now I am having trouble accessing my Windows drive from Ubuntu. It gives me permission errors whenever I try accessing it after mounting. It says it belongs to root. When I do 'su', I can then access it via the terminal. However, I can't access it any other way. It is read-only and root/root group and owner. Not sure if this is related to this setup or another issue. Any ideas?

Maybe this will help you get your Windows mounted with proper permissions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Sasquatch2000 on 2008-04-09
How does Ubuntu 8.04 "Hardy Heron" change any of this?


What I am really looking for is a way to install Ubuntu Linux onto either the same partition or another partition on either the same and/or another hard drive. I want a choice of which OS to boot on when I start up. 

Any ideas?

Thanks.

---

### Post by deafbus on 2008-04-18
My question, after reading all this stuff on dual boot, is this harder to do than dualbooting with Linspire & Windows on seperate harddrives? I want to do Ubuntu with XPPro 64 & XPPrp 32. Each has their own hd. Previously had Vista 64, XPPro 64 & 32. Vista is like Windows ME, a lot of fluff and a lot of trouble.Formated the Vista Harddrive, no more trouble.
            Thanks, Al

---

### Post by VicVega on 2008-04-18
Hi Al,
	I can't tell you how the setup compares to Linspire as I've never used it. I can tell you that I dual boot with Ubuntu 7.10 and XP (Home) 32 on separate hard drives, and it was a straight forward process. I have also set up Ubuntu and XP Pro 32 and it worked the same way. Very easy to set up and both worked flawlessly. I used the same method as gpilkay from this thread [http://ubuntuforums.org/showthread.php?t=717909]("http://ubuntuforums.org/showthread.php?t=717909")  (post #2).

---

### Post by deafbus on 2008-04-20
Thanks for replying. I will use your sugestion. I get into too much trouble when it come to typing a lot of commands.

---

### Post by PhatKat on 2008-05-02
Hi sorry if i am asking a 'duh' kindda question :P Just finished my DIY buntu box over the weekends but my via chipset VGA is giving me resolution problems on 8.04 so while i am getting that fixed via this wonderful forums, i had a spare HDD and installed buntu 7.10 and the IGP works fine! Now i am asking: can i boot from 2 HDDs, one with 7.10 and the other with 8.04?

---

### Post by Shampyon on 2008-05-02
I'm pretty sure it's the same process as dual booting with windows. The only real difference would be the name of the entry in GRUB :)

---

### Post by bfeero on 2008-05-13
I am having troubles getting my computer to dual boot successfully.  I have installed Ubuntu 8.04 on the first drive, with Vista Business on the other drive. 

There is the section of my "menu.lst" that is pertinent:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows Vista x64
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0)   (hd1)
map             (hd1)   (hd0)
chainloader     +1
```

When I attempt to start Windows, the screen says "Starting up..." for a split second, then goes to black, then reboots.  I assure you that Windows will boot when the second drive is attached alone.

Here is the result when I use "fdisk -l":
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23569   189317961   83  Linux
/dev/sda2           23570       24321     6040440    5  Extended
/dev/sda5           23570       24321     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3f850b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24791   199133676    7  HPFS/NTFS
```

... and my /etc/fstab....

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2be1474d-1e57-47e2-974f-e8c501cc068e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f5a6d187-ffc5-49f0-96ac-62649c4b96ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1 /media/VISTA ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

Can anyone help?

-Brett

---

### Post by Fenris_rising on 2008-05-13
hi all
great set of tuts about dual booting. could i just interject with an option i have used. i have 1 sata drive and one ide drive. sata has ubuntu, ide has xp. i did this by removing each drive whilst installing to the remaining one before then refitting both (this would work with 2 ide types to). at boot on my pc i have the option to hit F8 to go into a boot menu which lists all attached drives (floppy,HDD's,CD,DVD) and i can select which one i want to boot from. my default is ubuntu. i don't know if this is a common feature to newer motherboards or bios supplier dependant. but for now it means some of us may be able to get by without having to set the grub up. obviously its down to personel preference how you do it. i have however bookmarked this post for my future reference. 

cheers all

---

### Post by Artess on 2008-05-17
> **CypherHackz said:**
> Thanks. I think I have found what I want. Here is the article that describe how to make it:

[http://www.linux.com/articles/113945](http://www.linux.com/articles/113945)

And thanks to you for the nice article on how to dual booting WinXP and Ubuntu. ;)

-cypher.
Thx for a good link, but is it supposed to work with SATA drives? As I understand, they don't have any 'primary' or 'secondary' drives, and some parts of that guide are based on that difference.

---

### Post by Mr Pockets151 on 2008-05-19
I've been trying to get this to work.  But I have a SATA drive with the windows partition on it.  The grub menu shows the Windows XP title, but when I choose it I get a "press any key to continue...." message.  When I press "any" key I go back to grub menu.  I can keep doing it over and over.  Ofcourse when I choose the Ubuntu partition it loads to ubuntu.

---

### Post by markbuntu on 2008-05-22
I have 2 SATA drives. I bought a new one for Ubuntu and left XP on the old one. All I did was unplug the old drive from SATA1 and plug it into SATA2 on the motherboard and plug the Ubuntu drive in SATA1. 
Then I installed Hardy on the new drive, sda. Grub recognized XP and added it to the menu and XP boots just fine and does not even know the other drive is there.

A single SATA drive is often plugged into the wrong plug during assembly since a SATA bios does not care. The bios searches the plugs in order and trys to boot the first one it sees. It only matters when you add more drives.

---

### Post by Shobuz99 on 2008-06-09
Thanks for this forum.
I'm new to Ubuntu and would like to get away from Windows
as soon as I can kick the habit. Ubuntu is a great start.
I recently installed Ubuntu 8.04. I love it!... but....

What I'm also attempting to do is wean myself off Windows because
cold turkey won't do it for me.
I'm trying to setup dual-boot with Windows on an IDE hard drive and
Ubuntu on a different drive. I think the Ubuntu drive is a SATA drive; 
because when I did a 'sudo fdisk -l', this is what followed:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x96109610

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

so, I changed the loader code in menu.lst from hd1,0 to sd1,0 since it wouldn't even go to the bootloader on the Ubuntu drive before that. 

what it was:

title      Windows XP Home
root      (hd1,0)
savedefault
makeactive
chainloader    +1 
map (hd0)(hd1)   
map (hd1)(hd0)           

What it is now:

title	   Windows XP Home
root	   sd1,0)
savedefault
makeactive
map (sd0)(sd1)
map (sd1)(sd0)
chainloader    +1 
### END DEBIAN AUTOMAGIC KERNELS LIST

I'm still having a problem dual-booting and I'm starting to wonder if IDE and SATA drives cannot be mixed on the same cable?
I've been moving both drives, in and out of the cpu case so many times, and disconnected the disk drive cable so many times and jumpered the Ubuntu drive off and on to the "cable select" setting; 
that I've become lost. 
I've always left the jumper on the XP drive to "master", as well as always used the end of the disk cable (master) to connect to the XP drive. And still I can't get this to work.
The farthest I got was the Ubuntu drive bootloader came up and I tried to boot the XP selection and it failed and gave me an "Error 23 while parsing a number"...??? 
What does this mean? Please help.
I've had this cpu case open and apart for 3 days. 
It's driving me crazy!
Please help and please leave details if you do.
Like I said, I'm new to this and need some step-by-step...
Thank you for any help you may offer.
Shobuz99

---

### Post by confused57 on 2008-06-11
> The farthest I got was the Ubuntu drive bootloader came up and I tried to boot the XP selection and it failed and gave me an "Error 23 while parsing a number"...???
Have you tried just copying & pasting the Windows entry that I listed in my initial post?

Was your Windows drive connected when you ran "sudo fdisk -l"?

You might also want to post the boot entries in your menu.lst:
```
gedit /boot/grub/menu.lst
```

Even though your Ubuntu drive is sata, it's listed in grub as hdx, not sdx.

---

### Post by dksau on 2008-06-20
I want to dual boot Ubuntu 8.04 and windows XP Pro.  I will use two hard drives neither are sata.  I understand that when installing ubuntu with windows already on one drive ubuntu will automatically configure grub.  My problem is that I have a spare hard drive with a working copy of ubuntu 8.04 already installed.  How should I adjust grub so the system boots windows first.  The people in the house who can't use linux want to just turn it on and go.  I don't want to give up ubuntu.:)

---

### Post by confused57 on 2008-06-20
> **dksau said:**
> I want to dual boot Ubuntu 8.04 and windows XP Pro.  I will use two hard drives neither are sata.  I understand that when installing ubuntu with windows already on one drive ubuntu will automatically configure grub.  My problem is that I have a spare hard drive with a working copy of ubuntu 8.04 already installed.  How should I adjust grub so the system boots windows first.  The people in the house who can't use linux want to just turn it on and go.  I don't want to give up ubuntu.:)
See this guide for setting grub to boot Windows first:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

 I use the method of placing the Windows entry above the line ###BEGIN AUTOMAGIC KERNELS LIST...see the instructions in the first post of this thread.

---

### Post by dksau on 2008-06-20
Thank you confused57.  That will be my project for tomorrow:)

---

### Post by Lovok on 2008-06-21
I haven't read too many guides on how to dual boot with two hard drives, but this is how I do it, maybe you guys could tell me if it's dangerous or not :

Enter BIOS
Switch which hard disk the motherboard boots first

If I want to boot Windows, I set that hard drive first. Seems to work fine and is as easy as pie to do.

(This is after I installed Windows and Ubuntu on each hard drive separately.)

---

### Post by dksau on 2008-06-21
I ran into some problems with the preinstalled ubuntu hdd.  Next I reinstalled a hdd that had both windows and ubuntu and worked fine as far as booting goes but windows needed to be redone. After reinstalling and before plugging in the new windows only hdd I formatted the windows partition in the old dual boot hdd to ext3 this was bordered by two ext3 partitions.  Now with either of the two hdd plugged in alone each will boot and run properly in that respective OS.  With ubuntu as master and windows as slave and both hdd plugged in the system doesn't recognize any hdd.  What's next:confused:

---

### Post by confused57 on 2008-06-21
> **dksau said:**
> I ran into some problems with the preinstalled ubuntu hdd.  Next I reinstalled a hdd that had both windows and ubuntu and worked fine as far as booting goes but windows needed to be redone. After reinstalling and before plugging in the new windows only hdd I formatted the windows partition in the old dual boot hdd to ext3 this was bordered by two ext3 partitions.  Now with either of the two hdd plugged in alone each will boot and run properly in that respective OS.  With ubuntu as master and windows as slave and both hdd plugged in the system doesn't recognize any hdd.  What's next:confused:
Does your bios recognize the drives correctly and are you getting a grub boot menu when both drives are connected?

---

### Post by dksau on 2008-06-21
What I get is a message to insert a boot disk.  I'm not fully familiar with this new mobo yet.  After frying my BIOS this week I went to spare and the BIOS works completely different.  I can select a boot disk with f11 but before that hdds are normally displayed during boot up but are not with both hdd plugged into power:)

---

### Post by confused57 on 2008-06-21
> **dksau said:**
> What I get is a message to insert a boot disk.  I'm not fully familiar with this new mobo yet.  After frying my BIOS this week I went to spare and the BIOS works completely different.  I can select a boot disk with f11 but before that hdds are normally displayed during boot up but are not with both hdd plugged into power:)
   I'm not that familiar with different bios configurations & tweaks, so I'd suggest starting a new thread in the "Installation & Upgrades" section, describing what you've done, the issues you're having...be sure to give the thread a descriptive title.
There are plenty of knowledgable people on the forum who may be able to help, maybe even someone who's had the same problem.
Good luck.

---

### Post by dksau on 2008-06-21
The actual message I get goes like this. Reboot and Select proper Boot device or Insert Boot Media selected boot device and press a key.  When the boot device select menu comes up with both hdd plugged in none are shown in the boot device select menu.:confused:

---

### Post by dksau on 2008-06-21
Okay this is how my BIOS looks.


		Advanced

	IDE Configuration

	OnBoard IDE Controler		[Enabled]
	SATA Operation Mode		[RAID]

	> Primary IDE Master		[Not Detected]
	>Primary  IDE Slave			[Hard Disk]
	>Secondary IDE Master		[ATAPI CDROM]
	>Secondary IDE Slave		[Not Detected]
	>SATA1				[Not Detected]
	>SATA2				[Not Detected]

---

### Post by dksau on 2008-06-21
Well pardon my stupidity.  As it turns out my master hdd (Western Digital) requires a different jumper setting for master with slave present and so now I have that solved as the hdd is recognized in BIOS but now there is a different problem. I get the following message when attempting to boot windows.

 Error 13 Invalid or unsupported executable format. Press any key to continue.  Which returns me to GRUB menu.

 Also my objective is to have windows boot by default.

---

### Post by confused57 on 2008-06-21
> **dksau said:**
> Well pardon my stupidity.  As it turns out my master hdd (Western Digital) requires a different jumper setting for master with slave present and so now I have that solved as the hdd is recognized in BIOS but now there is a different problem. I get the following message when attempting to boot windows.

 Error 13 Invalid or unsupported executable format. Press any key to continue.  Which returns me to GRUB menu.

 Also my objective is to have windows boot by default.
Glad you were able to get Ubuntu to boot...to see what the problem may be, please post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"
and
```
gedit /boot/grub/menu.lst
```

---

### Post by dksau on 2008-06-21
confused57

Thank you for all of your help.  My newly configured dual boot system is up and running correct.  I was able to find the solution by googling the problem message and selecting the proper offered ubuntu forum thread.  Just to help clarify something that doesn't pop right out when we read these help messages.  When you want to change the default booting OS go to the top of the grub boot menu and count down to the OS you want to be default. Start with 0. Mine ended up being 10 (that's the 11th one listed).  In my case then I change the line default=0 line to read default=10.  elsewhere in the thread is shown the proper terminal entry to access that menu and line.:)

---

### Post by confused57 on 2008-06-21
> **dksau said:**
> confused57

Thank you for all of your help.  My newly configured dual boot system is up and running correct.  I was able to find the solution by googling the problem message and selecting the proper offered ubuntu forum thread.  Just to help clarify something that doesn't pop right out when we read these help messages.  When you want to change the default booting OS go to the top of the grub boot menu and count down to the OS you want to be default. Start with 0. Mine ended up being 10 (that's the 11th one listed).  In my case then I change the line default=0 line to read default=10.  elsewhere in the thread is shown the proper terminal entry to access that menu and line.:)

Good job getting your dual boot working, always great to hear a success story.

---

### Post by woodbrick on 2008-06-23
I have a slightly different situation. I need to re-install windows onto disk 1, but I want to keep my existing Linux install on disk two. The problem is that grub is currently loaded on the first disk, as when I first installed Ubuntu 8.04, over a (then) working windows system, I just went with all default options., and I hadn&#8217;t come across the great idea of unplugging the disk so that each OS is independently on each disk. 

I have an idea that the way to go about it (after doing a complete back-up) would be to &#8216;unplug&#8217;  disk1 (this can be done through the BIOS with SATA drives), then boot into ubuntu live CD, then load Grub on to the second hard disk. As soon as I can boot into ubuntu  with only the second disk active I can edit the menu.lst file to include the map commands, I can then plug in disk one, unplug disk2 and install windows (with it thinking it is the only OS). Finally, I can then plug in disk2 and I will have the same set up as described at the start of this post!

My question: How do I move grub over from disk one to disk two, and is it possible to move my existing files so that they are not over-written by the newly installed Grub? Any help would be greatly appreciated....

---

### Post by Unix_Slayer on 2008-06-23
> **woodbrick said:**
> I have a slightly different situation. I need to re-install windows onto disk 1, but I want to keep my existing Linux install on disk two. The problem is that grub is currently loaded on the first disk, as when I first installed Ubuntu 8.04, over a (then) working windows system, I just went with all default options., and I hadn’t come across the great idea of unplugging the disk so that each OS is independently on each disk. 

I have an idea that the way to go about it (after doing a complete back-up) would be to ‘unplug’  disk1 (this can be done through the BIOS with SATA drives), then boot into ubuntu live CD, then load Grub on to the second hard disk. As soon as I can boot into ubuntu  with only the second disk active I can edit the menu.lst file to include the map commands, I can then plug in disk one, unplug disk2 and install windows (with it thinking it is the only OS). Finally, I can then plug in disk2 and I will have the same set up as described at the start of this post!

My question: How do I move grub over from disk one to disk two, and is it possible to move my existing files so that they are not over-written by the newly installed Grub? Any help would be greatly appreciated....

Try [http://www.supergrubdisk.org]("http://www.supergrubdisk.org")

---

### Post by EriQ_10 on 2008-06-29
okay so i tried this and it works... kind of 
my cpu starts up and grub gives me the option of booting windows or ubuntu if i tell it to boot to ubuntu it works great but when i tell it to boot to windows it just opens the utility partion thing then when i close that it reboots and i go through the whole process again but it does the same thing So I set the slave drive to off in the bios settings and unplugged my ubuntu drive and plugged in my windows drive in as the master and it boots fine. if anyone can help it would be great i would like to learn to use ubuntu but i really dont want to lose xp.

---

### Post by confused57 on 2008-06-30
> **EriQ_10 said:**
> okay so i tried this and it works... kind of 
my cpu starts up and grub gives me the option of booting windows or ubuntu if i tell it to boot to ubuntu it works great but when i tell it to boot to windows it just opens the utility partion thing then when i close that it reboots and i go through the whole process again but it does the same thing So I set the slave drive to off in the bios settings and unplugged my ubuntu drive and plugged in my windows drive in as the master and it boots fine. if anyone can help it would be great i would like to learn to use ubuntu but i really dont want to lose xp.
With both drives connected, open a terminal & check the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

If Windows is on the 2nd partition, then you would need to change the line with root to (hd1,1):
```
title              Windows XP
root               (hd1,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by EriQ_10 on 2008-06-30
that was the problem it works now thank you so much.

---

### Post by woodbrick on 2008-06-30
> **Unix_Slayer said:**
> Try [http://www.supergrubdisk.org]("http://www.supergrubdisk.org")

Super Grub Disk worked great, thanks. All I did was boot from the SGD with my windows disk (also containing original Grub) deactivated in BIOS and chose to "fix grub." After that I had ubuntu working on just one disk, and everything else was a breeze. The thing I cant understand is how SGD installed grub without effecting the existing ubuntu install?? 

Anyway it all works. I can boot into either OS from the grub menu and I can also bypass grub and boot straight into XP if I set my second disk as the "primary boot device" in BIOS. Thanks to everyone who has contributed to this great post.

A good tip to anyone who gets errors after booting from grub screen: Instead of just hitting [ENTER] on highlighted OS, hit [e] (edit) and just try other partitions on your system. I was about to panic when windows would not load, then I just changed the hard-disk no in the 'root' command from '0' to '1' and it all worked. As far as I can tell, there is no harm in trying and even if it doesn't work the error message you get may shed more light on what's actually going on.

---

### Post by jessejazza on 2008-07-06
I've read this post through several times and somehow it doesn't seem to work for me... but as i'm trying to use windows 2k that might be the problem!

hard drives both standard IDE on a 2.6ghz desktop.
master drive - ubuntu 8.04
slave drive - win2k (no reason other than i don't have a copy of XP... my only reason for wanting to do dualbooting is that i've got several apps and a scanner than i can't run on ubuntu)

Following the beginning of the guide that worked fine - installing win2k on master and then connecting the master for ubuntu carefully switching the win2k disk to slave.

I want ubuntu to load as default. I read through menu.lst carefully taking note of what you said about needing to put the ammendments at the bottom of the file. In 8.04 at the foot of menu.lst IT IS ALREADY THERE - no editing required.

It would seem that 8.04 DOES the necessary!

On rebooting i selected the bottom item i.e windows and it didn't seem to load. I imagine win2k is different somehow from XP.

windows message
"Windows 2000 could not start because of a computer disk hardware configuration problem. Could not read from the selected boot disk. Check boot path and disk hardware"

I'd be very grateful if you put put me right! Menu.lst below 8.04 original no ammendments.

thanks
james


# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4a8cf581-73c8-41dc-a4d0-2bee78c3e5fc ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4a8cf581-73c8-41dc-a4d0-2bee78c3e5fc ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4a8cf581-73c8-41dc-a4d0-2bee78c3e5fc ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4a8cf581-73c8-41dc-a4d0-2bee78c3e5fc ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4a8cf581-73c8-41dc-a4d0-2bee78c3e5fc ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by edemkrimea on 2008-07-07
hello everybody. i am confused- i have two hard disks 320gb=sda & 80gb=sdb.the question-can i get them named vice versa

---

### Post by confused57 on 2008-07-08
jessejazza,
   I found this from MS describing your problem:
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)
Grub is configured correctly to boot your Windows drive, but there's possibly something in your boot.ini(?) or Windows boot files that isn't allowing Windows to boot from the slave drive. Did you change the jumper to slave?  You might want to connect your Windows drive as master, see if Windows will boot, then check how your boot.ini is configured.

edemkrimea,
   It doesn't really matter which drive is sda or sdb...that's determined by which HD controller the drives are connected to.
This should help you understand how grub recognizes HD's:
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)
Grub needs to be installed on the drive that you're booting to first in bios.  Why is it you want to change the drive designations???

---

### Post by jessejazza on 2008-07-08
Many thanks for the suggestion. This disk has only had windows 98 on it - one of my older spare ones. So i don't think it can have more than one partition. Took both drives out and checked jumpers were correct.

What it could be is a compatibility problem... i think one has a choice of formatting the disk with win2k - i think i chose FAT32! I reckon it needs to be NTFS - but this a bit beyond my knowledge. I wonder if its a win2k thing... i've got a copy basically - but earlier this evening i found a winXP recovery disk set (that came with this machine) so i could try XP. 

Just for your interest i posted this on my linux uses group... i got one reply saying forget it and use GRUB. THIS method of yours is a much superior way in my view. [I've been wondering how much that lot actually know]. I've only been using ubuntu for a year but i've got one or two apps and a scanner that i need to use winblows for.

thanks

---

### Post by jessejazza on 2008-07-09
It made sense to put on XP. I'm sure you're right about the boot.ini but not really worth the time.

The recovery disks only took 20 mins and obviously have all the drivers for this machine.

I only need windows for a couple of apps and a scanner. Plus watching the odd video that doesn't play on ubuntu. It seems a couple of the newspaper compilations like a wimbledon world championship one simply don't run on ubuntu.

This dualboot is an excellent method for my needs and i very much appreciate the time and effort you put in to producing it confused 57.

Many thanks

---

### Post by confused57 on 2008-07-09
> **jessejazza said:**
> It made sense to put on XP. I'm sure you're right about the boot.ini but not really worth the time.

The recovery disks only took 20 mins and obviously have all the drivers for this machine.

I only need windows for a couple of apps and a scanner. Plus watching the odd video that doesn't play on ubuntu. It seems a couple of the newspaper compilations like a wimbledon world championship one simply don't run on ubuntu.

This dualboot is an excellent method for my needs and i very much appreciate the time and effort you put in to producing it confused 57.

Many thanks

Glad to hear it worked for you.  I'll probably have to use XP to watch olympic events on nbc_olympics website, nice to have XP in those rare instances that it's necessary.

---

### Post by jessejazza on 2008-07-09
I wish ubuntu would improve their media software. For streaming video i have only ever managed to get RealPlayer working in Firefox. VLC, xine etc with careful adherence to the documentation... not achieved yet.

Shame having to dualboot - means ubuntu hasn't advanced enough to forget windows use totally.

---

### Post by jabba_29 on 2008-07-10
Hi,

Thanks for a great thread! 

It has gone a long way in helping me understand what is needed to set up a dual boot system. 
I will be trying to set this up myself very soon, but there are a few questions that I would appreciate a little help on.

My situation is that I have 4 HDD:

0) XP system
1) Want to install Ubuntu here
2) Music files
3) Empty

First off, the drive with XP is the master. I have been reading about the master/slave stuff and I am still unclear 
as to whether I really need to change XP to be the slave (I would like to leave hardware as is)..

I was going to change the boot order to:
0) CD/DVD drive
1) Ubuntu to be
2) XP as is now

**Will this work like that?**

Secondly, the drive that I want to install Ubuntu on is partitioned. 

**Will the installation join these drives again?**

The partitions are quite small and there seems no real point in having them any more.

If the installation works as detailed above, in menu.lst is the following still correct:```
title              Windows XP
rootnoverify        (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```**What does the second line actually do?**

Thanks in advance..

PS: I am a total newbie to all of this. 
I have installed Ubuntu on my laptop last week,
clean install, and so far I am very impressed.

I would just totally switch over but there are a few programs and hardware related stuff 
that I need that use XP!

---

### Post by confused57 on 2008-07-10
Hi jabba_29,
  This guide explains grub & it's configuration quite well:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

What you're planning on doing "should" work OK...set your bios boot order as you described(cdrom---Ubuntu drive---Windows drive).
The install cd partitioner can delete the partitions on the Ubuntu drive or you can use the entire disk option, just make sure to select the correct hard drive, e.g. sda, sdb, etc.

To ensure that grub is installed to the Ubuntu drive, you can click on the "Advanced" button at or near the end of the installation...change the default (hd0) to /dev/sdb(or however your Ubuntu drive is designated by the partitioner) as the location to install grub.  Grub should recognize & add an entry to boot Windows on your other drive...if it doesn't, then it should be relatively easy to add one manually.

---

### Post by jabba_29 on 2008-07-10
Thanks for the info.

I have almost finished testing on the XP side,
systematically going through my programs to make sure they still work.

After that, I will format the drive completely and join the partitions in XP.
Then comes the install :)

Will probably post back and definately capture the install and post it 
for future reference.

---

### Post by jabba_29 on 2008-07-10
Thanks for the info.

I have almost finished testing on the XP side,
systematically going through my programs to make sure they still work.

After that, I will format the drive completely and join the partitions in XP.
Then comes the install :)

Will probably post back and definitely capture the install and post it 
for future reference.

---

### Post by freeloader105 on 2008-07-16
confused57,

Thanks so much for such a great guide!

---

### Post by ssican on 2008-07-19
Confuse57, on Post 1, Make Reference to:
**both hard drives connected** during the install of Ubuntu:
[http://ubuntuforums.org/showpost.php?p=2195398&postcount=47](http://ubuntuforums.org/showpost.php?p=2195398&postcount=47)

On Post 47, there is a Reference to Alexander Grundner's guide (How-To dual boot Ubuntu) 
"Alexander Grundner on:
[http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)"

The "NEW" How-To of Alexander Grundner (How-To: Dual-Boot Windows and Ubuntu with Two Drives) is on:
[http://www.alexandergrundner.com/2007/12/17/how-to-dual-boot-windows-and-ubuntu-with-two-drives/](http://www.alexandergrundner.com/2007/12/17/how-to-dual-boot-windows-and-ubuntu-with-two-drives/)

EDIT 1 - The **FIRST** HOW TO of Alexander Grundner:
**How-To: Dual-Boot Ubuntu 6.06 (Dapper) Linux Desktop Along Side Windows XP ** is on:
[http://www.ehomeupgrade.com/2006/06/02/how-to-dual-boot-ubuntu-606-dapper-linux-desktop-along-side-windows-xp/](http://www.ehomeupgrade.com/2006/06/02/how-to-dual-boot-ubuntu-606-dapper-linux-desktop-along-side-windows-xp/)

---

### Post by confused57 on 2008-07-19
> **ssican said:**
> Confuse57, on Post 1, Make Reference to:
**both hard drives connected** during the install of Ubuntu:
[http://ubuntuforums.org/showpost.php?p=2195398&postcount=47](http://ubuntuforums.org/showpost.php?p=2195398&postcount=47)

On Post 47, there is a Reference to Alexander Grundner's guide (How-To dual boot Ubuntu) 
"Alexander Grundner on:
[http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu](http://www.ehomeupgrade.com/entry/2622/how-to_dual-boot_ubuntu)"

The NEW How-To of Alexander Grundner (How-To: Dual-Boot Windows and Ubuntu with Two Drives) is on:
[http://www.alexandergrundner.com/2007/12/17/how-to-dual-boot-windows-and-ubuntu-with-two-drives/](http://www.alexandergrundner.com/2007/12/17/how-to-dual-boot-windows-and-ubuntu-with-two-drives/)

Thanks for the heads-up, post 47 has been updated.

---

### Post by RoknRob70 on 2008-07-20
This is an excellent guide.  Thank you.

However, as an excited Ubuntu newbie, I wonder if I can add a level of complexity.  I am interested in having **Dualboot two hard drive **system, since I am sure there will be a learning curve to Ubuntu, and there will likely need to be tweaks before everything runs smoothly. 

My Windows XP runs off a mirroring RAID system. But I have a free 3rd drive that I would like to install Ubuntu to.  How will the two drives in the RAID be perceived by Ubuntu? If they are perceived as separate drives, what will modifications to either of the drives do to the RAID system once I load Windows?  Can I EXCLUDE access (or at least make access read-only) to the RAID hard drives whilst in Ubuntu? Will Grub know how to handle this if I want to boot XP?

Sorry if this as come up before, but I haven't been able to find a mention to this topic in the many pages of this thread.

Thanks in advance.

---

### Post by confused57 on 2008-07-20
> **RoknRob70 said:**
> This is an excellent guide.  Thank you.

However, as an excited Ubuntu newbie, I wonder if I can add a level of complexity.  I am interested in having **Dualboot two hard drive **system, since I am sure there will be a learning curve to Ubuntu, and there will likely need to be tweaks before everything runs smoothly. 

My Windows XP runs off a mirroring RAID system. But I have a free 3rd drive that I would like to install Ubuntu to.  How will the two drives in the RAID be perceived by Ubuntu? If they are perceived as separate drives, what will modifications to either of the drives do to the RAID system once I load Windows?  Can I EXCLUDE access (or at least make access read-only) to the RAID hard drives whilst in Ubuntu? Will Grub know how to handle this if I want to boot XP?

Sorry if this as come up before, but I haven't been able to find a mention to this topic in the many pages of this thread.

Thanks in advance.
You could probably go ahead and install with all 3 drives connected, but set the drive you'll be installing Ubuntu on as the first hard drive booted in bios, before you boot up the Ubuntu live cd for installing.  The partitioner will recognize your Raid as 2 separate drives, for a total of 3 drives.  Make a note of how your Ubuntu drive is designated during installation, e.g. /dev/sdc, /dev/sdb, or /dev/sda...near the end of the installation(step 7?), click on the "Advanced" button in the lower right corner and replace the default (hd0) with /dev/sdc(or however your Ubuntu drive is designated) as the location to install grub.
  
   Ubuntu will mount your ntfs filesystems as read-only, when you boot to XP from grub, it will function as a Raid after you boot into XP, although Ubuntu will see it as 2 separate drives.  You can always change your hard drive boot order to boot Windows from it's own loader.  What you don't want to do is install grub to the mbr of your first drive of your Raid array.

   If for some reason, you get an error 17 when you select to boot into Ubuntu from grub, highlight the first Ubuntu entry in the grub boot menu, press "e", highlight the line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot.

You might want to burn a copy of Super Grub Disk, before you install Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Don't hesitate to ask if you have any questions.  Good Luck.

---

### Post by RoknRob70 on 2008-07-21
Thanks, Confused57.  
A very helpful reply.
While you say I [B]COULD[B] go ahead and install with the 3 drives connected, would I not be better off (read: safer) disconnecting the two RAID drives, or will that cause problems with Ubunutu once I reconnect them?  I would hate to make a mistake and have grub installed to the Raid...

Thanks, again.

---

### Post by confused57 on 2008-07-21
> **RoknRob70 said:**
> Thanks, Confused57.  
A very helpful reply.
While you say I [B]COULD[B] go ahead and install with the 3 drives connected, would I not be better off (read: safer) disconnecting the two RAID drives, or will that cause problems with Ubunutu once I reconnect them?  I would hate to make a mistake and have grub installed to the Raid...

Thanks, again.
Yes, the only way to be sure is to disconnect your Raid drives when you install Ubuntu. You should be able to add an entry to boot Windows to grub.

---

### Post by wysbf2 on 2008-07-22
Hi,

I am about to try something that's a variation on this thread. I want to dual boot from 2 different HDDs (1 is XP, other is Hardy Heron) but both disks currently serve 2 separate machines.

The background: Machine A is an old Dell machine, happily running XP. Currently only has 1 IDE drive, but with cable for 1 more. Machine B is an ancient PC inherited from a neighbour, running Hardy Heron. However, Machine B just died - I thought the BIOS battery had died, but it seems more severe than that. The HDD in Machine B is quite new, so I'm sure it's OK.

So my goal is to install the HDD from Machine B into Machine A alongside the existing drive, and to set Machine A up to dual boot. Additionally, I want to boot into Ubuntu by default, so I guess I'll need to switch the existing HDD in Machine A to be slave, and the old HDD from Machine B to be master.

Other than following the excellent thread here ([http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)) is there anything else I should be careful of? I'm just conscious that the HDD from Machine B was previously running in somewhat different hardware (different motherboard, less memory, different video card etc). I've already burned some LiveCDs (Supergrub etc) in case all goes pear-shaped....

Grateful for any tips before I get started.

Thanks,

SB

---

### Post by confused57 on 2008-07-22
> **wysbf2 said:**
> Hi,

I am about to try something that's a variation on this thread. I want to dual boot from 2 different HDDs (1 is XP, other is Hardy Heron) but both disks currently serve 2 separate machines.

The background: Machine A is an old Dell machine, happily running XP. Currently only has 1 IDE drive, but with cable for 1 more. Machine B is an ancient PC inherited from a neighbour, running Hardy Heron. However, Machine B just died - I thought the BIOS battery had died, but it seems more severe than that. The HDD in Machine B is quite new, so I'm sure it's OK.

So my goal is to install the HDD from Machine B into Machine A alongside the existing drive, and to set Machine A up to dual boot. Additionally, I want to boot into Ubuntu by default, so I guess I'll need to switch the existing HDD in Machine A to be slave, and the old HDD from Machine B to be master.

Other than following the excellent thread here ([http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings](http://ubuntuforums.org/showthread.php?t=124989&highlight=Jumper+settings)) is there anything else I should be careful of? I'm just conscious that the HDD from Machine B was previously running in somewhat different hardware (different motherboard, less memory, different video card etc). I've already burned some LiveCDs (Supergrub etc) in case all goes pear-shaped....

Grateful for any tips before I get started.

Thanks,

SB

I would definitely set the drive with Ubuntu as master, Windows as slave...make sure to have both drives jumpered to cable select, if it's supported in bios.  I have a Dell Dimension 4550, which has the Primary slave controller set to "off" by default...I had to change it to "auto" when I installed the 2nd hard drive.

The new xorg in Hardy does an excellent job of detecting new video hardware, you'll just have to try it to see if the old Ubuntu is compatible with your Dell.  If you have Gutsy installed, you'll need to run:
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by wysbf2 on 2008-07-23
Thought I'd report on a successful venture - the dual-boot part was easy, but I came across some serious issues on the old drive from Machine B. I installed this drive into Machine A (actually a Dell Dimension 2400) and attempted to boot from it. No joy at all, so I booted from a LiveCD and ran gparted on the drive. It turns out that when Machine B had died, it had done some pretty nasty things to the drive. I didn't know it could do it, but the 'Check' option in gparted actually runs

```
e2fsck -f -y -v
```

This did the trick, with all my data apparently intact, so I shunted it all onto a spare external drive to be on the safe side.

I now managed to get the old Dell machine to boot this drive - but my memory was incorrect, I was running Gutsy (not Hardy Heron as I previously mentioned) on the drive from Machine B. So it stubbornly refused to pick the correct video options when I ran through

```
sudo dpkg-reconfigure xserver-xorg
```

from the shell in recovery mode.

The device properties indicated that the on-board Intel graphics should behave as i810 - but this refused to give me anything other than 640x480 resolution, however much memory I allocated to it. Once I installed the xserver-xorg-video-intel package (see section 6, here: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto) ) and re-ran the command above (selecting 'intel' driver instead of 'i810') all was well.

Editing my menu.lst to configure the dual boot operation took 5 mins and worked first time.....actually getting to that point took a little longer.....

Thanks to previous posters (esp confused57) for the great advice in this thread.

SB

---

### Post by Lovok on 2008-07-27
Sorry if this has been asked already, but here is my problem :

Before attempting to dual boot, I would just change boot order in my BIOS to boot into XP or Ubuntu. Now that I've followed this guide, I can do it on the fly in the Grub menu thing.
Only thing is, now Ubuntu doesn't see my XP hdd, whereas it used to (XP never did see Ubuntu).
Ubuntu is on IDE, XP on SATA. At the same time I did this dual boot, I set my SATA hdd to be able to transfer at rates of 3Gb/s, opposed to the 1.5Gb/s it was capped at from when I bought it.

Did the dual booting cause these problems, or did my SATA drive settings?

Thanks.

EDIT : I also just tried booting from a CD, and it just skipped that part..
I don't think that the CD I tried can be booted from... and I restored my menu.lst to it's default settings, and I can access my XP hdd.

---

### Post by tad1073 on 2008-09-17
I installed Ubuntu mount point / on sda2, swap on sda1, /home on sdc2. Windows XP is on sdb and storage for windows is on sdc1. Grub didn't pick up Windows or add it, so I followed your guide and when I tried booting into windows I got the following error:

```
 Missing NTLDR  Press Ctrl+Alt+Delete to restart 
```

---

### Post by earthtux on 2008-09-17
this is my xp section from my /boot/grub/menu.lst
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP (loader)
root		(hd1,1)
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

my fdisk -l
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19d9516a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23849   191567061   83  Linux
/dev/sda2           23850       24321     3791340    5  Extended
/dev/sda5           23850       24321     3791308+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       32098+   6  FAT16
/dev/sdb2   *           5        4862    39021885    7  HPFS/NTFS


```
Ubuntu 8.04 is on my primary master hard disk
XP sp3 is on my primary slave hard disk
I installed ubuntu after the xp
and the grub is on the master hard disk
so xp is not altered by ubuntu at all

my computer is dimension8100
so the first partition on slave hard disk is dell rescue tool partition(or something like that)

my problem is when i select boot xp from grub menu
i got a black screen and no hard disk is reading/writing

can any one help pls?

P.S. if i replace root with rootnoverity, it reboots after i select boot xp!

---

### Post by confused57 on 2008-09-17
> **earthtux said:**
> this is my xp section from my /boot/grub/menu.lst
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP (loader)
root		(hd1,1)
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


```

my fdisk -l
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19d9516a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23849   191567061   83  Linux
/dev/sda2           23850       24321     3791340    5  Extended
/dev/sda5           23850       24321     3791308+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       32098+   6  FAT16
/dev/sdb2   *           5        4862    39021885    7  HPFS/NTFS


```
Ubuntu 8.04 is on my primary master hard disk
XP sp3 is on my primary slave hard disk
I installed ubuntu after the xp
and the grub is on the master hard disk
so xp is not altered by ubuntu at all

my computer is dimension8100
so the first partition on slave hard disk is dell rescue tool partition(or something like that)

my problem is when i select boot xp from grub menu
i got a black screen and no hard disk is reading/writing

can any one help pls?

P.S. if i replace root with rootnoverity, it reboots after i select boot xp!

If you moved the Windows drive from master to slave, did you change the HD jumper to slave or have both drives set to cable select?  Also, you probably read my first post in this thread, but is the slave drive set to "auto" in bios.

You might want to burn a copy of Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
then try booting your Windows drive with SGD...sometimes SGD can show what the problem is, if it's a grub error.  

See if your drives are recognized correctly in your bios setup.

---

### Post by earthtux on 2008-09-18
Thank you for your reply
both hard drives are recognized by bios(both auto, actually if not auto it's off)
the jumpers of both drive are set to cable selected.
will the jumpers be the problem?

i tried the super grub disk
tried all options to boot my xp as well. All i got is black screen
and no hard disk reading/writing........
advanced-->windows advnaced->boot partition of windows-->choose the xp partition
the output on screen
```

set out_device = (hd1,1)
set out_hurd_hd=hd1
set out_linux_letter=b
set out_lide_hd=hdb
set out_lscsi_hd=sdb
set out_part=(hd1,1)
set out_lide_part=hdb2
set out_lscsi_part=sdb2
set out_hurd_part=hd1s2
set out_linux_part=b2
set out_part_n=1
set out_linux_end=b2
back
back
set aux_part=(hd1,1)
rootnoverity (hd1,1)
chainloader +1
boot

```

tried live swap too..it flashed some message but a black screen followed.

I tried to put jumpers on master/slave to test but still failed

I can boot into ubuntu but not xp

P.S.why in my fdisk -l
they both sdx not hdx?
since they are both connected by ide cables

---

### Post by confused57 on 2008-09-18
Cable select for both drives should work fine...Hardy recognizes drives as sdx, regardless if they're IDE or SATA.

Does the Windows drive boot OK, if it is connected as master?  Is this the original install of Windows or if you installed it, did you install Windows to the drive connected as master?

---

### Post by earthtux on 2008-09-18
> **confused57 said:**
> Cable select for both drives should work fine...Hardy recognizes drives as sdx, regardless if they're IDE or SATA.

Does the Windows drive boot OK, if it is connected as master?  Is this the original install of Windows or if you installed it, did you install Windows to the drive connected as master?

oh i see!
yes, if i put xp drive to master it boots!
xp is installed by dell(and it was the only drive when i got the whole computer)
all my settings are the same as you guys posted here
Dont know y it cant work T_T
Is there any other files I should look into?

---

### Post by confused57 on 2008-09-19
> **earthtux said:**
> oh i see!
yes, if i put xp drive to master it boots!
xp is installed by dell(and it was the only drive when i got the whole computer)
all my settings are the same as you guys posted here
Dont know y it cant work T_T
Is there any other files I should look into?
Sorry, but I've about run out of ideas for you to try. The only other thing I can think of is, have you installed SP2 to your XP?  I've read of other posters having problems booting XP from grub with just XP SP1, I'm grasping at straws here, you probably already have SP2 or it probably isn't your problem if you haven't.

I had to upgrade the bios on my Dimension 4500 from A02 to A08, before I could install SP2, which I did about mid-2003.  You may want to start a new thread in the "Installation & Upgrades" section, describing your problem(in as much detail as possible)...maybe someone else has had the same issues & was able to find a solution.
Good luck with it.

Added:  Another possiblity, if you're not able to boot Windows on the slave drive from grub, is to switch the Windows drive to master & boot Ubuntu from Windows:
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)
I've never done this personally, but the howto seems to explain it pretty well.

---

### Post by earthtux on 2008-09-19
> **confused57 said:**
> Sorry, but I've about run out of ideas for you to try. The only other thing I can think of is, have you installed SP2 to your XP?  I've read of other posters having problems booting XP from grub with just XP SP1, I'm grasping at straws here, you probably already have SP2 or it probably isn't your problem if you haven't.

I had to upgrade the bios on my Dimension 4500 from A02 to A08, before I could install SP2, which I did about mid-2003.  You may want to start a new thread in the "Installation & Upgrades" section, describing your problem(in as much detail as possible)...maybe someone else has had the same issues & was able to find a solution.
Good luck with it.

Added:  Another possiblity, if you're not able to boot Windows on the slave drive from grub, is to switch the Windows drive to master & boot Ubuntu from Windows:
[http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723)
I've never done this personally, but the howto seems to explain it pretty well.
my xp is sp3 if my memory serves me right!
Thank you very much for your time, I will try what you suggested.

---

### Post by BPMOU on 2008-09-20
Hey Guys,

Great forum and first post.  I am looking to dual boot from two SATA hard drives.  I currently have a SATA drive that came with the computer with Vista Home Premium SP1.  I want to add another SATA drive with Ubuntu on it.  I see most people setting this up are running XP.  Is there anything that I need to know specifically before I go buy another SATA drive to do this?

Thanks in advance.

---

### Post by confused57 on 2008-09-20
> **BPMOU said:**
> Hey Guys,

Great forum and first post.  I am looking to dual boot from two SATA hard drives.  I currently have a SATA drive that came with the computer with Vista Home Premium SP1.  I want to add another SATA drive with Ubuntu on it.  I see most people setting this up are running XP.  Is there anything that I need to know specifically before I go buy another SATA drive to do this?

Thanks in advance.
Welcome to the forum, it's definitely the best.

You shouldn't have any problems installing Ubuntu on a separate drive, if you follow the instructions in this thread, especially the first post. Having 2 SATA drives shouldn't make any difference, as long as you're booting first to the Ubuntu drive.

Don't hesitate to ask, if you have any questions.

---

### Post by BPMOU on 2008-09-22
Ok, so I just wanted to post up my results.  I followed the instructions on the first post.  Unplugged the HD with Vista.  Plugged in the new drive and installed Heron 8.04 from the Live CD.  Turned off pc and plugged the Vista HD back into it's original slot on the MB as it was orignially configured.  Then plugged in the new Heron HD in SATA slot 3.  

When I power on, I go right into Vista, unless I hit escape and select Ubuntu from the boot order and then Ubuntu loads.  Seems to both be working well.  When I go into ubuntu I can see my Vista HD with the two drives c:/ and d:/, both factory images, but I cannot access.  I don't think that I would want to access them that way any how for fear of damaging any Vista files.

Is there anything else I need to do?  I would evenutally like to move to Ubuntu exclusivly and boot straight to it instead of Windows.  But before I do that I need to figure out how to get all of my pics, docs, music, dvd to ubuntu.  I backed up my Vista HD to a 500 GB external drive, so I do have an extra copy of my Vista drive.  Anythoughts?  I am loving ubuntu, great OS and I think it will be simpler for the wife to us as she has been having issues with Outlook and IE.  

Thanks!

---

### Post by alfy on 2008-09-24
Hi!
I too have two hard disks SATA.
On the first HD there is WinXP, the second is blank.

I would install Ubuntu on the second, and put Grub on it.
I read first post, but I've a question:

My motherboard do not permit to choose which hard disk is "the bootable".

So, if I unplug my first HD (with XP), where I'll plug the second HD (the blank one) before to install Ubuntu, on SATA1 slot or SATA2 slot (this is where it plugged now)?
I think on SATA2, but motherboard will recognize the disk on SATA2?

Excuse me for my english :p and my confusion. :confused:

---

### Post by confused57 on 2008-09-24
> **alfy said:**
> Hi!
I too have two hard disks SATA.
On the first HD there is WinXP, the second is blank.

I would install Ubuntu on the second, and put Grub on it.
I read first post, but I've a question:

My motherboard do not permit to choose which hard disk is "the bootable".

So, if I unplug my first HD (with XP), where I'll plug the second HD (the blank one) before to install Ubuntu, on SATA1 slot or SATA2 slot (this is where it plugged now)?
I think on SATA2, but motherboard will recognize the disk on SATA2?

Excuse me for my english :p and my confusion. :confused:

Unplug your XP drive, then plug the drive you're going to install Ubuntu on SATA1...after you have Ubuntu installed, then you can connect your XP drive to SATA2, then see the first post in this thread for adding an entry to grub for booting XP.

---

### Post by BPMOU on 2008-09-24
Hey Confused:  I read the grub modification on the first post, but admit I am lost.  My Vista drive is in SATA 2 and the Ubuntu is in SATA 4 (this is what is shows when I choose which one to boot) and if nothing is done Vista boots up.  I want Ubuntu to boot if nothing else is selected.  What specially should I put into the grub menu for 2 SATA drives, one with Vista and one with Ubuntu?

Thanks in advance for your help.

---

### Post by confused57 on 2008-09-25
> **BPMOU said:**
> Hey Confused:  I read the grub modification on the first post, but admit I am lost.  My Vista drive is in SATA 2 and the Ubuntu is in SATA 4 (this is what is shows when I choose which one to boot) and if nothing is done Vista boots up.  I want Ubuntu to boot if nothing else is selected.  What specially should I put into the grub menu for 2 SATA drives, one with Vista and one with Ubuntu?

Thanks in advance for your help.
All you need to do is move your grub Vista entry to the very BOTTOM of your menu.lst, instructions are in the first post...make a backup of your current menu.lst first:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
```
then
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by alfy on 2008-09-25
Thanks for your reply, Confused! :)

> **confused57 said:**
> Unplug your XP drive, then plug the drive you're going to install Ubuntu on SATA1...after you have Ubuntu installed, then you can connect your XP drive to SATA2, then see the first post in this thread for adding an entry to grub for booting XP.

Hmmm, so...

Bios look for MBR in the disk on SATA1 slot **first**, and **then**, search in the slot SATA2 ?
For Bios, SATA1 is *"a kind of"* master, and SATA2 *"a kind of"* slave?

Have I got that right?

---

### Post by confused57 on 2008-09-25
> **alfy said:**
> Thanks for your reply, Confused! :)



Hmmm, so...

Bios look for MBR in the disk on SATA1 slot **first**, and **then**, search in the slot SATA2 ?
For Bios, SATA1 is *"a kind of"* master, and SATA2 *"a kind of"* slave?

Have I got that right?
In the context of this thread, you could look at it as SATA1 master & SATA2 slave...your SATA1 is the first hard drive in the boot sequence, which is where you want Ubuntu installed.

I can only boot to the master hard drive(not the slave drive) on my Dimension 4550, therefore I had to set the Ubuntu drive as master in order to boot using grub.

---

### Post by alfy on 2008-09-25
> **confused57 said:**
> In the context of this thread, you could look at it as SATA1 master & SATA2 slave...your SATA1 is the first hard drive in the boot sequence, which is where you want Ubuntu installed.

I can only boot to the master hard drive(not the slave drive) on my Dimension 4550, therefore I had to set the Ubuntu drive as master in order to boot using grub.

Ok, thanks!
I understand now! \\:D/

---

### Post by BPMOU on 2008-09-26
Ok from before.  Where exactly do I make the mentioned change?  I am trying to switch ubuntu as the primary or default boot so that Vista has to be selected.  HEre is my menu.lst.  I am new, so thanks for your patients.

 menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d1bd994f-5ff5-4ce8-804f-269db4d2d604 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d1bd994f-5ff5-4ce8-804f-269db4d2d604 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d1bd994f-5ff5-4ce8-804f-269db4d2d604 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by confused57 on 2008-09-26
BPMOU,
   If you're able to boot into Ubuntu from grub if you boot first to your Ubuntu drive, then all you need to do is add your Vista entry to the bottom of your menu.lst, e.g.:

```
## ## End Default Options ##

title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d1bd994f-5ff5-4ce8-804f-269db4d2d604 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=d1bd994f-5ff5-4ce8-804f-269db4d2d604 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows Vista
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

If Vista is on the second partition, then you would need to use root (hd1,1)...you can check your partition layout, by opening a terminal, enter:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by dayyou on 2008-11-10
Ok I know this sounds like a novice question but, 
this works on vista right? I don't want to go off
and try this before i mess every thing up.

---

### Post by confused57 on 2008-11-10
> **dayyou said:**
> Ok I know this sounds like a novice question but, 
this works on vista right? I don't want to go off
and try this before i mess every thing up.
I don't have Vista, but I haven't heard of this method not working
with Vista.

Another possiblity might be to use EasyBCD to add Linux to the Vista bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by alexeix on 2008-11-13
I'm going to chip in here, because I also have a boot-related problem (see here: [http://ubuntuforums.org/showthread.php?t=981283](http://ubuntuforums.org/showthread.php?t=981283))

Any suggestions?  Both drives are SATA.

"I have 2 hard drives - one with Ubuntu and one with Mythbuntu, however, I want Mythbuntu to be the primary boot disk.

Unfortunately, the Ubuntu disk boots first and I can't see how to change it.

I've tried changing the SATA cables round, so it doesn't seem to be determined by the SATA socket on the motherboard.

I've also checked the BIOS and I can the sequence there reflects the boot sequence, but there's no option to change it.

I can manually change it when booting up, but that's no good, as I need Mythbuntu to boot up when I'm not there (and record TV).

Any ideas how to correct this?"

---

### Post by heyup on 2008-11-14
I have 2 SATA drives. Followed instructions in this thread but when I boot into Windows XP a fatal system error occurs.

Two SATA drives. 
SATA 1 (secondary) Windows XP (original hard drive).
SATA 1 (primary) Ubuntu 7.10 (new hard drive).

This is what I did:-

Disconnected SATA (secondary) Windows XP.
Installed Ubuntu on SATA (primary) Ubuntu. 
Amended menu.lst file as per instructions.
Reconnected SATA (secondary) Windows XP.
Booted up computer. Grub loads properly with menu options.
Select Ubuntu. Ubuntu loads OK. Shut down computer.
Boot up computer. Grubs loads OK.
Select Windows XP. Windows fails to load. Fatal system error c000021a (blue screen)

If I disconnect SATA (primary) Ubuntu and boot up computer, SATA (secondary) Windows XP loads OK.

With both SATA hard drives connected, I can boot into Ubuntu, but if I try to boot into Windows XP it fails to load (fatal system error).

Anyone any ideas as to what the problem might be?

---

### Post by caljohnsmith on 2008-11-14
Heyup, that sounds like it might be a simple problem with your Windows entry in your Grub's menu.lst. In Ubuntu, how about opening a terminal (applications > accessories > terminal) and do:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your Windows entry with:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If that for some reason doesn't work to boot Windows, let me know exactly what happens when you choose it from the Grub menu. Also please post:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by heyup on 2008-11-14
I had already changed the menu.lst file as per the entry you posted.

When I select Window XP from grub menu, I flash message appears (that I missed)something about NTFS, then Windows starts to load but then stops with error message:-

Fatal system error. c000021a (fatal system error).
The session manager initialisation system process terminated unexpectedly with a status of 0xc00003a. The system has been shut down.

Here is what fdisk gives:

[HTML]Disk /dev/sda: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x000719fe



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63    48821534    24410736   83  Linux

/dev/sda2        48821535   951160454   451169460    5  Extended

/dev/sda5        48821598   439442009   195310206   83  Linux

/dev/sda6       439442073   947256659   253907293+  83  Linux

/dev/sda7       947256723   951160454     1951866   82  Linux swap / Solaris



Disk /dev/sdb: 81.9 GB, 81964302336 bytes

255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0xea4735bd



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1              63     7181054     3590496   1c  Hidden W95 FAT32 (LBA)

/dev/sdb2   *     7181055   160071659    76445302+   7  HPFS/NTFS[/HTML]

---

### Post by caljohnsmith on 2008-11-14
OK, I think I see the problem; your Windows partition is on sdb2, not sdb1, so you should use (hd1,1):
```
title	   Windows XP
root       [COLOR="Blue"](hd1,1)[/COLOR]
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Give that shot and let me know how it goes.

---

### Post by heyup on 2008-11-14
OK. I'll give that ago. I may be sometime, but I'll post the result. It maybe tomorrow though.

---

### Post by heyup on 2008-11-14
> **caljohnsmith said:**
> OK, I think I see the problem; your Windows partition is on sdb2, not sdb1, so you should use (hd1,1):
```
title	   Windows XP
root       [COLOR="Blue"](hd1,1)[/COLOR]
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Give that shot and let me know how it goes.

Brilliant. That fixed the problem. I think sdb1 is a hidden partion for Windows XP recovery.

Thanks again for your help.

---

### Post by caljohnsmith on 2008-11-14
> **heyup said:**
> Brilliant. That fixed the problem. I think sdb1 is a hidden partion for Windows XP recovery.

Thanks again for your help.
You're welcome, glad your problem turned out to be simple to fix. Cheers and have fun with your OSes. :)

---

### Post by bigguly on 2008-11-15
Quick noob question.  I want to install Kubuntu.  It should be the same has instaling Ubuntu?  Thanks in advance to all replies.
:KS:KS:KS

---

### Post by confused57 on 2008-11-16
> **bigguly said:**
> Quick noob question.  I want to install Kubuntu.  It should be the same has instaling Ubuntu?  Thanks in advance to all replies.
:KS:KS:KS
Yes, it should be the same for Kubuntu...if you've never used kde before you'll use:
```
kdesu kwrite menu.lst
```
instead of:
```
gksudo gedit menu.lst
```
which is used in gnome.

---

### Post by bigguly on 2008-11-16
> **confused57 said:**
> Yes, it should be the same for Kubuntu...if you've never used kde before you'll use:
```
kdesu kwrite menu.lst
```
instead of:
```
gksudo gedit menu.lst
```
which is used in gnome.

Thanks very much Confused57.  I'm gonna buy a new HDD in the January sales, along with a load of other stuff, and I will be coming back to this thread to take all your advice.  Just make yourselves ready for my nooby questions:wink:

---

### Post by alexeix on 2008-11-18
> **alexeix said:**
> I'm going to chip in here, because I also have a boot-related problem (see here: [http://ubuntuforums.org/showthread.php?t=981283](http://ubuntuforums.org/showthread.php?t=981283))

Any suggestions?  Both drives are SATA.

"I have 2 hard drives - one with Ubuntu and one with Mythbuntu, however, I want Mythbuntu to be the primary boot disk.

Unfortunately, the Ubuntu disk boots first and I can't see how to change it.

I've tried changing the SATA cables round, so it doesn't seem to be determined by the SATA socket on the motherboard.

I've also checked the BIOS and I can the sequence there reflects the boot sequence, but there's no option to change it.

I can manually change it when booting up, but that's no good, as I need Mythbuntu to boot up when I'm not there (and record TV).

Any ideas how to correct this?"

Any advice on this problem?

I just don't see how to set which drive will boot first.
Thanks in advance.

---

### Post by confused57 on 2008-11-18
> **alexeix said:**
> Any advice on this problem?

I just don't see how to set which drive will boot first.
Thanks in advance.
Please post your Ubuntu menu.lst:
```
gedit /boot/grub/menu.lst
```

If you're able to boot Mythbuntu from your Ubuntu menu.lst, this may help:
[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by alexeix on 2008-11-19
I think the problem is down to the fact that I installed Ubuntu and Mythbuntu on the separate SATA drives, with only one drive connected at a time.  Although I still don't see why it always boots to Ubuntu, regardless of whether I swap the drives round.

Anyway, here's my Ubuntu menu.lst file:

(see attachment)

By the way, can anyone tell me how to include long sequences like this in a posting, in one of those small windows?
Thanks.

---

### Post by alexeix on 2008-11-20
Any suggestions on this?

Should I go back to square one and re-install Ubuntu 8.10 with both hard drives connected?

:confused:

---

### Post by confused57 on 2008-11-20
> **alexeix said:**
> I think the problem is down to the fact that I installed Ubuntu and Mythbuntu on the separate SATA drives, with only one drive connected at a time.  Although I still don't see why it always boots to Ubuntu, regardless of whether I swap the drives round.

Anyway, here's my Ubuntu menu.lst file:

(see attachment)

By the way, can anyone tell me how to include long sequences like this in a posting, in one of those small windows?
Thanks.
I'm unable to open your menu.lst attachment, but you can copy & paste your /boot/grub/menu.lst in a window with:
```
your /boot/grub/menu.lst here[/code[

Change what I have above by changing the last bracket from "[" to "]", this will display your menu.lst list in a code window.

Added:  You might also want to post the ouput of:
[code]sudo fdisk -l
```
-l is a lowercase "L"
and
```
sudo grub
find /boot/grub/stage1
quit
```

You shouldn't need to reinstall either OS.

---

### Post by alexeix on 2008-11-23
Okay, here's menu.lst:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=514fa4c4-3176-4489-9af7-b765e3b65d60 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=514fa4c4-3176-4489-9af7-b765e3b65d60

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		514fa4c4-3176-4489-9af7-b765e3b65d60
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=514fa4c4-3176-4489-9af7-b765e3b65d60 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		514fa4c4-3176-4489-9af7-b765e3b65d60
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=514fa4c4-3176-4489-9af7-b765e3b65d60 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		514fa4c4-3176-4489-9af7-b765e3b65d60
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by confused57 on 2008-11-23
I assume this is your Ubuntu menu.lst, so you can use the Ubuntu live cd to install grub's IPL(Initial Program Loader) to the root partition of Mythbuntu:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
When you run "find /boot/grub/stage1", you should get something like:
```
root (hd0,0)
root (hd1,0)
```
this is mainly why I requested that you post the output of this command.  Again assuming (hd1,0) is your Mythbuntu root partition, following the instructions in the above tutorial:
```
sudo grub
find /boot/grub/stage1  <----if Mythbuntu returns (hd1,0), then:
root (hd1,0)
setup (hd1,0)
quit
```

Boot back into your installed Ubuntu & add a chainloader method to boot Mythbuntu:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Add this entry to the very end of your Menu.lst(after ###END DEBIAN AUTOMAGIC...):
```
title Mythbuntu
root (hd1,0)
chainloader +1
```
exit & save

If this enables you to boot Mythbuntu, then you add it's entry just above the line ###BEGIN AUTOMAGIC KERNELS LIST, which make Mythbuntu the default OS booted automatically.

---

### Post by alexeix on 2008-11-23
I realised that the Mythbuntu drive was disconnected when I ran that, so I re-connected it and here's the output (from Ubuntu):

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=514fa4c4-3176-4489-9af7-b765e3b65d60 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=514fa4c4-3176-4489-9af7-b765e3b65d60

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		514fa4c4-3176-4489-9af7-b765e3b65d60
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=514fa4c4-3176-4489-9af7-b765e3b65d60 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		514fa4c4-3176-4489-9af7-b765e3b65d60
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=514fa4c4-3176-4489-9af7-b765e3b65d60 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		514fa4c4-3176-4489-9af7-b765e3b65d60
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by alexeix on 2008-11-23
From sudo fdisk -l:

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d9ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60424   485355748+  83  Linux
/dev/sda2           60425       60801     3028252+   5  Extended
/dev/sda5           60425       60801     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc00bc00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23946   192346213+  83  Linux
/dev/sdb2           23947       24321     3012187+   5  Extended
/dev/sdb5           23947       24321     3012156   82  Linux swap / Solaris

```

---

### Post by alexeix on 2008-11-23
From find /boot/grub/stage1:

(hd0,0)
 (hd1,0)

---

### Post by confused57 on 2008-11-23
Thanks for the additional information, from which I believe that the instructions I mentioned in post #199 "should" work, with both drives connected, Ubuntu as primary boot drive & Mythbuntu as the secondary boot drive.

Please make a note of any error messages, if the instructions don't work.

---

### Post by alexeix on 2008-11-23
Hi,

Thanks for the continued support with this problem.

With both drives connected, if I boot into Ubuntu, and run find /boot/grub/stage1, I get:

hd0,0
hd1,0

If I boot into Mythbuntu and run the command, I get the same.

So I'm a bit confused about what's going on/what I'm doing.

I'd assumed that the results would be different, depending on what I booted from.

---

### Post by confused57 on 2008-11-23
> **alexeix said:**
> Hi,

Thanks for the continued support with this problem.

With both drives connected, if I boot into Ubuntu, and run find /boot/grub/stage1, I get:

hd0,0
hd1,0

If I boot into Mythbuntu and run the command, I get the same.

So I'm a bit confused about what's going on/what I'm doing.

I'd assumed that the results would be different, depending on what I booted from.

Yes, you'd need to set Ubuntu first boot drive for the method I described to work.  Since you can boot boot into Mythbuntu through bios, you might want to post your /boot/grub/menu.lst in Mythbuntu, which I assume is Intrepid 8.10.

Ubuntu & Mythbuntu would both show the same results for "find /boot/grub/stage1" when you boot first to either OS.  In Hardy 8.04, the grub boot entry would show root (hd0,0) for both Ubuntu & Mythbuntu, since you disconnected the other drive when installing each; however, Intrepid 8.10 uses UUID instead of (hdx,y) so each should have a unique UUID for root & switching the position of the drives shouldn't be an issue.  If Mythbuntu uses UUID in the root line, the method I described should work.  However if Mythbuntu uses "root (hd0,0)", I'll need to give you further instructions to boot Mythbuntu from Ubuntu's grub.

---

### Post by alexeix on 2008-11-23
Yes, Mythbuntu is 8.10.

Here's the menu.lst contents:

```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=95b305af-11d8-4e30-8856-8b3b15249bd8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=95b305af-11d8-4e30-8856-8b3b15249bd8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=95b305af-11d8-4e30-8856-8b3b15249bd8 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=95b305af-11d8-4e30-8856-8b3b15249bd8 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=95b305af-11d8-4e30-8856-8b3b15249bd8 ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by confused57 on 2008-11-23
You'll need to do a couple of extra steps, since Mythbuntu 8.10 uses root (hd0,0), instead of UUID.  Set your Ubuntu drive as the first hard drive booted, then follow the instructions I gave you in reply #199.  Once you've done this, try booting to Mythbuntu using Ubuntu's grub; however, when you boot to Mythbuntu you'll see Mythbuntu's grub menu...highlight the first Mythbuntu entry, press "e", highlight the line with root, press "e" again, then change root from (hd0,0) to (hd1,0), press "enter", then "b" to boot.  This change is temporary if it works, but you can make it permanent in your Mythbuntu /boot/grub/menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
you'll also have to change the line with #groot from (hd0,0) to (hd1,0).

EDIT:  Since Mythbuntu uses (hd0,0), you won't need to use the live cd to install grub's IPL to it's root partition, but instead a configfile entry will work, boot into Ubuntu:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Then add this entry to the very end of your menu.lst:
```
title  Mythbuntu
configfile (hd1,0)/boot/grub/menu.lst
```
quit & save

You'll still need to follow the instructions above(press "e" to change root from 0,0 to 1,0) to get Mythbuntu to boot.

---

### Post by phantomme on 2008-11-30
Thank you, confused57, for this clear tutorial:KS. I want to share some of the minor issues I encountered while following your advice.
First I need to mention that I work on a relatively old system so I installed the distro XUBUNTU. 
When using the terminal window, it asked for my password. I realised after a few tries that apparenty in the terminal window, no keystrokes (even no "*") are shown when typing your password, and you do not get any confirmation that the password is correct.
As I tried to open the menu.lst with "gksudo gedit menu.lst", the system did not react. I tried to open the menu.lst file with a wordprocessor, but it refused to save my changes.
Finally I realised (by typing the command "gedit menu.lst" without gksudo that gedit was not installed in xubuntu. Fortunately it was readily downloaded and installed within the terminal window itself.
Hereafter everything went smoothly as you explained (I also had the bios issue)
Nevertheless  a question remains : when starting "windows XP", the system wanted to run a diskcheck on my "G" drive, which I skipped. In windows the G drive is my Linux drive. Is there any risk with running chkdisk from windows XP on the linux drive ?:-s

---

### Post by confused57 on 2008-11-30
> **phantomme said:**
> Thank you, confused57, for this clear tutorial:KS. I want to share some of the minor issues I encountered while following your advice.
First I need to mention that I work on a relatively old system so I installed the distro XUBUNTU. 
When using the terminal window, it asked for my password. I realised after a few tries that apparenty in the terminal window, no keystrokes (even no "*") are shown when typing your password, and you do not get any confirmation that the password is correct.
As I tried to open the menu.lst with "gksudo gedit menu.lst", the system did not react. I tried to open the menu.lst file with a wordprocessor, but it refused to save my changes.
Finally I realised (by typing the command "gedit menu.lst" without gksudo that gedit was not installed in xubuntu. Fortunately it was readily downloaded and installed within the terminal window itself.
Hereafter everything went smoothly as you explained (I also had the bios issue)
Nevertheless  a question remains : when starting "windows XP", the system wanted to run a diskcheck on my "G" drive, which I skipped. In windows the G drive is my Linux drive. Is there any risk with running chkdisk from windows XP on the linux drive ?:-s
Thanks, glad you were able to get your dual boot working.  Yes, gedit isn't installed by default in Xubuntu, which uses the mousepad text editor:
```
gksudo mousepad /boot/grub/menu.lst
or you could use nano:
sudo nano /boot/grub/menu.lst
```

I've never had XP even see any of the ext3 partitions I've installed Ubuntu on.  I'm guessing that you resized a ntfs or fat32 partition to make room for Ubuntu and that is probably what XP is wanting to run chkdisk on.

Windows assigns drive letters to individual partitions rather than to separate hard drives, which you probably already know.
To see how Xubuntu sees your drives & partitions, you might want to run this in a terminal:
```
sudo fdisk -l
```
-l is a lowercase "L"

The links in my signature are excellent resources that you may want to bookmark.

---

### Post by phantomme on 2008-12-14
Indeed, the drive was formerly formatted in NTFS. In XP it still sees the "NTFS" partition, although it has been overwritten by installing Xubuntu.
Any idea how to turn off drive checking on the Linux drive in XP ?
(I'll have a look myself also)

---

### Post by presence1960 on 2008-12-14
I dual boot an IDE and sata hard drive, but set it up differently. I installed Ubuntu on the sata drive and had the IDE drive as a storage drive. My original intention was to get rid of Windows altogether. But my boss gave me some added responsibilities which require me to use Adobe Acrobat professional. So I then repartioned the IDE drive into two partitions , both NTFS. I then put in the Vista install DVD rebooted, entered BIOS and set the IDE as first drive. Installed Vista to the IDE drive. When installed rebooted and back into BIOS again. Set the sata as first drive. Grub did not contain Windows so I edited the grub menu file to add Vista. Pretty simple process and it works just fine. Now both OS show up in my start up menu for grub.

---

### Post by JAID on 2008-12-23
Hello,

You have been doing a great job with this Confused and for a couple years.

Don't let me waste your time if this query is too far from you experience zone but any advice would be appreciated.

I have Ubuntu Hardy set up and running well on an HP DL380 G4 Dual Xeons/6GB with a half dozen U320 SCSI drives. It will be necessary to set up a dual boot arrangement so that Adobe Master Collection CS4 can be used on this machine (which is faster than others here)

The second OS will be Windows Server 2008. It seems ideal to me that the two OS reside on separate drives. Do you think your formula may be adjustable to separate SCSI drives?

Thanks

Ian

---

### Post by JAID on 2008-12-24
Perhaps I should give a bit more background detail (part from another thread):

I need to run Adobe Master Collection CS4 on this otherwise-to-be server to handle some of the more calculation intensive stuff as that slows my PC to a standstill. (Premier pro editing AVCHD particularly) Apparently there has been no thorough success in running it on Ubuntu through Wine.

Installation of the second OS to a another SCSI drive on this system rather than partitioning the Ubuntu drive seems best to me. Currently there are a half dozen U320 hot-plug drives.

Two drives are linked in RAID 1+0 currently dedicated to Ubuntu (unless Ubuntu deletes the RAID connection upon installation - I havent looked.) At Ubuntu installation I let it have the whole drive which would mean both in RAID - probably not too wise but it sounds like something changeable. Ubuntu is on the SCSI drive at location/name SCSI ID0 set in SCSI BIOS to boot first afte the CD. 

Four drives are currently set up as RAID 5. These are already NTFS drives. One will probably get removed from that setup and have WinSrvr2008 and Adobe MC CS4 stuck on it.

The thing I am ignorant of which stands out now is how to get the new Win 2008 boot loader and the Ubuntu loader picked up together and presented for selection at startup.

There are a number of good coverages of dual boot setups here including yours but if concerning separate drives they seem to revolve around using Master and secondary IDE or SATA drives. 

The drives on this machine being hot plug SCSI drives, I was hoping just to:

- Remove an NTFS drive from the present RAID 5 set
- pull the present boot drive with Ubuntu off the system.
- Plug the drive taken from the RAID 5 set into the 0 slot

(These inbuilt SCSI systems allocate SCSI ID's by position and there would be no need even to change the boot order in BIOS that way) 

- Load WinServer2008 on the newly plugged in drive. 
- Pull that and put it back in its own slot
- Re-plug the Ubuntu ext3 drive in the 0 slot
- Boot to ubuntu
- Somehow edit the GRUB menu list or map so that it picks up the other drive and offers it a choice for booting at startup. But I don't know how that will be done as the examples have not dealt with SCSI.

Very appreciative of any advice. Thanks

---

### Post by confused57 on 2008-12-26
> **JAID said:**
> Hello,

You have been doing a great job with this Confused and for a couple years.

Don't let me waste your time if this query is too far from you experience zone but any advice would be appreciated.

I have Ubuntu Hardy set up and running well on an HP DL380 G4 Dual Xeons/6GB with a half dozen U320 SCSI drives. It will be necessary to set up a dual boot arrangement so that Adobe Master Collection CS4 can be used on this machine (which is faster than others here)

The second OS will be Windows Server 2008. It seems ideal to me that the two OS reside on separate drives. Do you think your formula may be adjustable to separate SCSI drives?

Thanks

Ian

Hi Ian,
   Thanks for the compliments.  I'm not familiar with SCSI drives, nor with Raid; however, as long as the Windows drive isn't part of a Raid setup, it should work.  You've probably already found out that Ubuntu recognizes your Raid drives as separate drives and it "should" be just a matter of adding the correct entry in grub to boot Windows.  It may be just a matter of trial & error to find the correct entry, in addition to the entry I gave in my initial post in this thread, you could try:
```
title              Windows 
root               (hd2,0)
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```
or
```
title              Windows 
root               (hd3,0)
savedefault
makeactive
map                (hd0) (hd3)
map                (hd3) (hd0)
chainloader        +1
```

This should give you an idea of additional entries if your Windows drive is recognized as (hd4),(hd5), etc.

Good luck with it & feel free to ask any other questions if you have problems.

---

### Post by JAID on 2008-12-26
[I]Thanks for the reply Confused. 
(You dont think a name change to something more fitting not in order?)

That should do the job. At the moment I have removed the two Ubuntu formatted drives and am having a little problem with Win Server 2008 64-bit which I will have to fix before re-installing those drives.

On RAID, I found I had to configure one single drive as a RAID set (on its own that is) to get it recognised so currently Windows is on a RAID set of one. Hope your comment doesnt mean that will be inaccessible to Grub at start-up.

Thanks again

Regards

Ian

---

### Post by confused57 on 2008-12-27
> **JAID said:**
> [I]Thanks for the reply Confused. 
(You dont think a name change to something more fitting not in order?)

That should do the job. At the moment I have removed the two Ubuntu formatted drives and am having a little problem with Win Server 2008 64-bit which I will have to fix before re-installing those drives.

On RAID, I found I had to configure one single drive as a RAID set (on its own that is) to get it recognised so currently Windows is on a RAID set of one. Hope your comment doesnt mean that will be inaccessible to Grub at start-up.

Thanks again

Regards

Ian

You shouldn't have any problem with grub booting Windows set up the way you're planning.  Actually, grub has no problem booting Windows installed on a Raid array, if Ubuntu is installed on a separate drive that's not part of the array Windows is on...the problem happens when Ubuntu is installed on the same Raid array that Windows is installed on.  It's been awhile since I've helped much on the forum, but after dusting off the "cobwebs" I realized I had misinformed you.

Sounds like you have a lot of experience with Raid, but here's an excellent write-up of Raid setups with Linux:
[http://ubuntuforums.org/showthread.php?t=1019864](http://ubuntuforums.org/showthread.php?t=1019864)

---

### Post by JAID on 2008-12-27
Thanks for that Confused. 

Only one incorrect statement in there: "you have a lot of experience at RAID" 

I think despite fiddling with computers in my firm for a quarter century about the only thing I have a lot of experience at is managing to make all new tasks a drawn out matter of trial, failure and eventual realisation that something simple was missed.

Good that this setup will work though.

What is holding up the process is that windowsSVR2008 64-bit failed to make use of either the inbuilt CD or an LG external DVD and WinServer2008 only comes on DVD. It could see them and judged their drivers the latest, would spin them but do nothing with that. Today I have just had another go at loading over the one that was working (without these drives) yesterday and now I have managed to get it so it wont even install. Will probably need to wait a week to get a thin DVD into the state.

By the way, Ubuntu didnt have any trouble. :-)

Regards

Ian

---

### Post by JAID on 2008-12-27
An update. 

Windows Server 2008 STD 64-bit loaded fine last night. There were several problems, both mine. 

The first that although I installed the latest HP Maintenance update I didnt do the same for HP SmartStart. The second was that the LG external drive I was using which self powers from the USB bus couldn't handle the heat (the heavy use installation makes of it) and it took me far too long to come to the conclusion that they provide a second USB bus power cable for those occasions. With both plugged in - no problems.

So, today it is back to Ubuntu.

Ian

---

### Post by Chaos_Spear on 2009-01-14
So I'm trying to boot Kubuntu by default but have the option to switch to XP on the second drive.  But I keep getting an error 23, parsing a number, when I try to boot XP.  I've looked at it and I can't seem to find where I could have possibly done it wrong, I basically copy-pasted from the site.

```
title              Windows XP Professional
root               (sdb,0)
savedefault
makeactive
map                (sda) (sdb)
chainloader        +1
```
(note: I removed the second map command since I didn't want my XP drive to have access to my Linux drive)

All this at the end of menu.lst

Fdisk lists "sda" as my Linux drive and "sdb" as my XP drive, though I also tried listing the partition sdb1, with no success.

---

### Post by logos34 on 2009-01-14
> **Chaos_Spear said:**
> So I'm trying to boot Kubuntu by default but have the option to switch to XP on the second drive.  But I keep getting an error 23, parsing a number, when I try to boot XP.  I've looked at it and I can't seem to find where I could have possibly done it wrong, I basically copy-pasted from the site.

```
title              Windows XP Professional
root               (sdb,0)
savedefault
makeactive
map                (sda) (sdb)
chainloader        +1
```
(note: I removed the second map command since I didn't want my XP drive to have access to my Linux drive)

All this at the end of menu.lst

Fdisk lists "sda" as my Linux drive and "sdb" as my XP drive, though I also tried listing the partition sdb1, with no success.

grub used '(**h**d?,?)' format

[look here]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") for help with booting windows on second disk

---

### Post by Chaos_Spear on 2009-01-14
Oh, ok.  I must have misread one of the guides.  Thanks!  I'll go see if that works.

---

### Post by domokunrox on 2009-01-23
I have a question regarding the topic subject itself.

How do you dual boot with 2 Sata Hard Drives? Windows setup throws a fit about the other drive and refuses to let GRUB handle the boot process.

I wish it was as easy as starting your computer and it asking you which drive you want to start up. Am I asking for too much?

---

### Post by fuzzywigg on 2009-01-25
I am getting:

[Error 1: File name must be either an absolue pathname or block list.] {Press any key to continue}

:(

My menu.lst is to follow.


[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[[
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		12

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=2ce19ebd-4915-41e6-b996-882244286e7d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2ce19ebd-4915-41e6-b996-882244286e7d ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title              Windows XP

rootnoverify              (hd1,0)

savedefault

makeactive

map                (hd0) (hd1)

map                (hd1) (hd0)

chainloader        +1rf

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2ce19ebd-4915-41e6-b996-882244286e7d ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2ce19ebd-4915-41e6-b996-882244286e7d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		SUSE Linux Enterprise Server 10 SP1 (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.16.46-0.12-smp root=/dev/disk/by-id/scsi-SATA_ST3160023AS_5MT0PWYM-part1 vga=0x31a acpi=off resume=/dev/sda1 splash=silent showopts 
initrd		/boot/initrd-2.6.16.46-0.12-smp
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Failsafe -- SUSE Linux Enterprise Server 10 SP1 (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.16.46-0.12-smp root=/dev/disk/by-id/scsi-SATA_ST3160023AS_5MT0PWYM-part1 vga=normal showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd-2.6.16.46-0.12-smp
savedefault
boot
]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]]

Drive to boot from is #1 and Windows XP is drive #2

Both drives are SATA.  If it makes a difference, I have partitions set up for swap files from both OS's on the opposite drive.

Here is what I have as fdisk -l :


Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed404

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18696   150175588+  83  Linux
/dev/sda2           18697       19452     6072570    5  Extended
/dev/sda5           18697       19452     6072538+   b  W95 FAT32

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045397

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14472   116246308+   7  HPFS/NTFS
/dev/sdb2           14473       19452    40001850    5  Extended
/dev/sdb5           14473       19452    40001818+  82  Linux swap / Solaris

Disk /dev/sdc: 1040 MB, 1040187392 bytes
240 heads, 63 sectors/track, 134 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xfcb8e742

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         135     1015776+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(133, 239, 63) logical=(134, 87, 55)


Can anyone help with an 'Error 1' given this back groundning?

---

### Post by mystikal2k2a on 2009-02-14
Hi

Ok I'm stuck, please can anyone help me with this?

I have 2 sata hard drives - 1 with MS Windows XP Pro and the other with Linux Ubuntu. I have the grub boot loader menu appearing and I can see an entry for Windows. When I try and select the Windows option from the boot loader menu I get an error. I've received different errors each time I have tried configuring the boot/grub/menu.lst file. I can't get into Windows at present but can get into Ubuntu.

This is the contents of fdisk -l -

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x896a4361

Device Boot Start End Blocks Id System
/dev/sda1 * 1 498 4000153+ 82 Linux swap / Solaris
/dev/sda2 499 6334 46877670 5 Extended
/dev/sda5 499 6334 46877638+ 83 Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x457d457c

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 3916 31455238+ 7 HPFS/NTFS
/dev/sdb2 3917 19457 124833082+ 7 HPFS/NTFS

This is the contents of my menu.lst file in boot/grub -

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

I have tried various combinations to get this corrected. I even tried replacing the letters hd1 and hd0 to sd1 and sd0 where applicable because I read it maybe required for SATA discs?

Can anyone help please?

Thanks

---

### Post by ktmom on 2009-03-05
Thank you confused57 for the post.  It was the first dual-boot with two drives post I found and this <shudder> almost 50yo was able to install Ubuntu onto a second SATA drive, configure grub and be off with a choice of whether I am exploring Ubuntu or need to do things *now*they way I know how to do it.



The ease with which this install went, makes me very optimistic that I have found my new operating system. Now to explore the new world.

FWIW: On a Dell 8400, I have three SATA drives. Ubuntu on SATA0, WinXP on SATA1 and Data on SATA2. I physically disconnected WinXP and Data then installed Ubuntu without issue.  I performed all updates, rebooted, modified grub using exactly the instructions in post 1 then rebooted.  Then shutdown again and reconnected the WinXP and Data drives.  Everything works as advertised and I just am amazed at how simple this was.

---

### Post by Jammanuser on 2009-03-05
> **mystikal2k2a said:**
> Hi

Ok I'm stuck, please can anyone help me with this?

I have 2 sata hard drives - 1 with MS Windows XP Pro and the other with Linux Ubuntu. I have the grub boot loader menu appearing and I can see an entry for Windows. When I try and select the Windows option from the boot loader menu I get an error. I've received different errors each time I have tried configuring the boot/grub/menu.lst file. I can't get into Windows at present but can get into Ubuntu.



Hi mystikal2k2a.
Could you please describe the latest error you got with the configuration you posted? I'm thinking the boot.ini file might be configured wrong. Could you also acess your XP partition from within Ubuntu, and please post the contents of "boot.ini"? 

-Jam man

:guitar:

---

### Post by confused57 on 2009-03-07
> **ktmom said:**
> Thank you confused57 for the post.  It was the first dual-boot with two drives post I found and this <shudder> almost 50yo was able to install Ubuntu onto a second SATA drive, configure grub and be off with a choice of whether I am exploring Ubuntu or need to do things *now*they way I know how to do it.



The ease with which this install went, makes me very optimistic that I have found my new operating system. Now to explore the new world.

FWIW: On a Dell 8400, I have three SATA drives. Ubuntu on SATA0, WinXP on SATA1 and Data on SATA2. I physically disconnected WinXP and Data then installed Ubuntu without issue.  I performed all updates, rebooted, modified grub using exactly the instructions in post 1 then rebooted.  Then shutdown again and reconnected the WinXP and Data drives.  Everything works as advertised and I just am amazed at how simple this was.

Thanks for the feedback, glad it worked for you.  Yes, this method works quite nicely for most people & you don't have to worry about your XP install when installing Ubuntu, which I know you'll love using.  

Jammanuser,
   Thanks for helping, I haven't been able to assist anyone much on the forum lately.

---

### Post by youdkelon on 2009-03-29
Hi, I just bought a new desktop, I have to hard drives on it. 1 has 500gb and the other has 1tb. I installed ubuntu, but for some reason I can't use the second hard drive (1tb). I can't mount it. Does anyone know what I should do?

Thanks

---

### Post by Jammanuser on 2009-03-29
> **youdkelon said:**
> Hi, I just bought a new desktop, I have to hard drives on it. 1 has 500gb and the other has 1tb. I installed ubuntu, but for some reason I can't use the second hard drive (1tb). I can't mount it. Does anyone know what I should do?

Thanks

I'm assuming you're trying to access the TB hard drive from Ubuntu? If so, does the hard drive show up at all in "Computer" when it is plugged in and powered on?

---

### Post by youdkelon on 2009-03-30
Yes, it shows up. I was able to mount it, but now I can't put files into it. It has a folder named lost+found.

---

### Post by unutbu on 2009-03-30
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by four o two on 2009-05-28
Hi guys - I've read through the thread but wanted to post my exact setup before I "dive in", start changing things, then regret it later if it doesn't work.

I have 2 SATA drives connected, a 1TB with Windows Vista on it and a 500GB with Ubuntu 9.04 installed. I *believe* that the SATA controller is defaulting to the Ubuntu drive because that's what boots up first, bypassing the Windows drive. GRUB just asks what config to boot up in Ubuntu.

My fdisk -l:
```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46173692

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976758784    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c269c26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       59345   476688681   83  Linux
/dev/sdb2           59346       60801    11695320    5  Extended
/dev/sdb5           59346       60801    11695288+  82  Linux swap / Solaris

```

...and my menu.lst file (just in case)
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=eea71cfd-a540-49f7-8935-7f2a23667f09 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=eea71cfd-a540-49f7-8935-7f2a23667f09

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		eea71cfd-a540-49f7-8935-7f2a23667f09
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=eea71cfd-a540-49f7-8935-7f2a23667f09 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		eea71cfd-a540-49f7-8935-7f2a23667f09
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=eea71cfd-a540-49f7-8935-7f2a23667f09 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		eea71cfd-a540-49f7-8935-7f2a23667f09
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Can anyone point me in the right direction as far as making changes to the entry go so I don't screw it up?

---

### Post by confused57 on 2009-05-28
four o two, 

The Window's entry listed in the first post in this thread should work for you:
```
title              Windows Vista
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

You might want to add the entry at the very bottom of your menu.lst(after the line ###END DEBIAN AUTOMAGIC KERNELS LIST).

Did you have the Vista drive disconnected when you installed Ubuntu, since a Vista boot entry wasn't automatically added to your menu.lst?

---

### Post by BarryGordon on 2009-06-08
I also wish to put up Ubunto as a dual boot but my config is a little strange.  The machine is running windows XP PRO SP@ 32 bit.  I shotly plan to upgrade to XP 64 bit but that should not make a difference.  The drive configuration has me a little concerned.
 
The physical layout is three SCSI drives on a single SCSI controller with SCSI-0 being the boot drive. I also have a 120 GIG PATA drive on the secondary IDE channel.  The primary IDE channel is running a CD ROM drive.
 
Windows reports 4 scsi drives which makes no sense, also the Storage manager seems to thing they are all SCSI drives, but that is definately not the case. Drive capacities are all correct in the storage manager.
 
Questions:
 
Should I disconnect the SCSI drives and then load Ubuntu on the IDE drive, or should I leave them connected and load up Ubuntu on the IDE drive? Does it make a difference?
 
I would like the boot process to always go to Windows unless I intervene in the timeout period. I assume I need to use GRUB to do that which makes me believe I should leave the SCSI drives connected so that GRUB gets put there (SCSI-0) and the Ubunto system goes to the IDE drive.
 
 
I would like to be able to see the scsi drives from Ubunto and the Ubunto drive from Windows.  Will that be the case?  All the windows drives are formatted as NTFS partitions with each drive containing only one partition.
 
Any and All Help appreciated.

---

### Post by confused57 on 2009-06-08
> Windows reports 4 scsi drives which makes no sense, also the Storage manager seems to thing they are all SCSI drives, but that is definately not the case. Drive capacities are all correct in the storage manager.
Not a problem, this is the way Ubuntu recognizes drives, regardless of whether they're SATA or IDE(sda, sdb ,sdc, sdd, etc)

> Should I disconnect the SCSI drives and then load Ubuntu on the IDE drive, or should I leave them connected and load up Ubuntu on the IDE drive? Does it make a difference?
You can leave the SCSI drives connected, that way the Ubuntu installer should automatically enter a Window's grub boot entry.  I would recommend setting your IDE drive as the first hard drive booted in bios, if your system is capable of this, before you boot the live cd to install Ubuntu.  If your system isn't capable of booting first to IDE, then it should be OK to install grub's IPL to the mbr of your current boot drive.  You might want to check out this link for restoring Window's IPL to the mbr, if there is a problem installing Ubuntu and you can't boot into any OS:
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)
I personally would download & burn a copy of the Super Grub Disk, mentioned in the link.

> I would like to be able to see the scsi drives from Ubunto and the Ubunto drive from Windows. Will that be the case? All the windows drives are formatted as NTFS partitions with each drive containing only one partition.
You will be able to see your NTFS partitions in Ubuntu, but you'll need fs-driver installed in Windows XP to recognize Ubuntu(ext3) from XP.

> I would like the boot process to always go to Windows unless I intervene in the timeout period. I assume I need to use GRUB to do that which makes me believe I should leave the SCSI drives connected so that GRUB gets put there (SCSI-0) and the Ubunto system goes to the IDE drive.
A Window's entry should be added automatically to grub, but see these methods for setting which OS you want to boot first:
[http://members.iinet.net.au/~herman546/p15.html](http://members.iinet.net.au/~herman546/p15.html)
See the section on default operating system booted by grub.

---

### Post by BarryGordon on 2009-06-09
Made progress but still confused.  With rgeards to the machine I mentioned two posts above; Thank you for the reply Confused77.  Perhaps you can help me some more.
 
This machine (lets call it Victor)has three drives connected to a PCI controller as SCSI id 0,1,2 (all Fujitsu drives). It has one drive as the Master on a mobo based IDE/SATA controller (Maxtor drive).  
 
I booted the machine from the Ubuntu 9.04 distribution boot disk, and the only hard drive it found was the IDE drive (Maxtor).  I then said what the heck, and decided to just do the install on the Maxtor drive which was what I wanted anyways.  That went very well no issues.  GRUB ended up being loaded onto the Maxtor drive.
 
If I now tell Bios Setup to boot from SCSI-0 it loads windows XP and windows knows nothing about the Maxtor drive, however the Windows Disk manager does know about the Maxtor drive and shows it with two partitions (as i suspect that is what Ubuntu set up). If I alter Bios Setup to boot from the Maxtor drive then GRUB shows up as I suspected it might, but to my surprise it knows about Windows and allows me to chain either to Windows XP on SCSI-0 or to Ubuntu on the Maxtor drive.  
 
The above is actually close to what I want.  All I need to do now is tell GRUB on the Maxtor drive that I want the default OS to be Windows. I intend to install Windows XP 64 bit this weekend and I think it will be superb as I wall have it go to SCSI-0 and all should be well with GRUB, Ubuntu and Windows XP 64.
 
 
Now let me tell you about another system lets call it TEST.  It has Windows XP on drive C (IDE Primary Master 120 G), and has a second drive that Windows sees calling it "D" (IDE Primary Slave 100 Gig).  I booted the same Ubunto distribution disk.  It found both drives but would not let me load Ubunto on the 100 Gig Drive. It stated there was a partition problem, or something to that effect. I was unable to resolve the problem and ended up loading Ubuntu into the 120Gig drive by having Ubunto partition it and split it in half.
 
GRUB is on the 120 Gig drive as it should be and allows me to boot into Windows or Ubuntu.  I fogot to check if Ubuntu can see the 100G drive, but since this is just for testing (this machine gets Windows 7 as soon as I can burn an error free copy) It is not an issue.  However I am curious, why wouldn't Ubuntu let me install onto the 100 Gig Drive that it clearly knew about.
 
I will do some more reading but any assistance will be appreciated.

---

### Post by confused57 on 2009-06-10
Thanks for the update, glad you were able to successfully set up a dual-boot.

On your test computer, open a terminal & post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

There could be partitioning problems if a hard drive already has 4 primary partitions, which is the maximum 
number allowed on a drive...however, you can have an extended primary partition within which you can have numerous logical partitions.

---

### Post by aharp on 2009-06-11
Hope this might help someone: I was in a little different situation than confused57 who wrote the very helpful first message in this thread.  I had installed Hardy on the slave drive (drive 1 in the BIOS) with win98 on the master (hd0).  So I thought I had to modify the map instructions for that reason so as to boot from the Linux drive.  However, win98 would not start after I swapped the drive designations.  I tried the original instructions but they didn't work either.  Here is what did work: 

title Windows 98
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
chainloader +1

---

### Post by android73 on 2009-06-12
Hi everyone,

I too am new to Ubuntu and Linux in general, and am in the process of installing a dual boot system with my existing Windows XP. I have installed Ubuntu on a separate internal SATA drive, after unplugging my other Windows drive which is also a SATA. I have done all the updates and am ready to modify the grub menu and re-plug in my Windows drive, but am still unsure after reading all these posts what lines to add to it based on my setup. I am not sure what the difference is between inserting this:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

...and inserting this is:

title Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
makeactive
chainloader +1

I have found both of these in different threads as solutions. But have no idea if this applies to my setup. Does the "hd" designation apply to an IDE type drive? Does this need to be changed to "sd" designation for SATA drives? Im confused. Below is my fdisk and menu.lst files. Thank you in advance for any assistance you guys could provide. These are really helpful forums!


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004d8e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246       60303   474383385   83  Linux
/dev/sda3           60304       60801     4000185   82  Linux swap / Solaris
andrew@andrew-desktop:~$ 



# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f54083ad-d142-4448-b5ef-22073bdcd61c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f54083ad-d142-4448-b5ef-22073bdcd61c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f54083ad-d142-4448-b5ef-22073bdcd61c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f54083ad-d142-4448-b5ef-22073bdcd61c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f54083ad-d142-4448-b5ef-22073bdcd61c
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f54083ad-d142-4448-b5ef-22073bdcd61c ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f54083ad-d142-4448-b5ef-22073bdcd61c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by confused57 on 2009-06-12
android73,
   I've always used the entry in my first post here for booting Windows on a 2nd hd:
```
title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

If this doesn't work, then you can try the other entry, which I've never used.

"hd" is used for both IDE & SATA drives in grub.

I see you were given the same solution in your other thread:
[http://ubuntuforums.org/showthread.php?t=1185829](http://ubuntuforums.org/showthread.php?t=1185829)

---

### Post by marcvangend on 2009-06-13
I've been reading dozens of pages about dual booting Ubuntu and WinXP with GRUB, but I can't get it working :( 

These are my disks:
```

marc@marc-ubuntu:/$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4a2c4a2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS
/dev/sda2       102398310   488375999   192988845    f  W95 Ext'd (LBA)
/dev/sda5       102398373   488375999   192988813+   7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf4407582

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    76903154    38451546   83  Linux
/dev/sdb2        76903155    80292869     1694857+   5  Extended
/dev/sdb5        76903218    80292869     1694826   82  Linux swap / Solaris

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7d97ed27

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     4209029     2104483+   7  HPFS/NTFS
/dev/sdc2         4209030   160071659    77931315    f  W95 Ext'd (LBA)
/dev/sdc5         4209093   160071659    77931283+   7  HPFS/NTFS

```
SDA is a SATA disk, sda1 contains Windows XP. I didn't change anything on this disk, I can still boot from it into WinXP when I set SDA as primary boot device in my bios.
SDB is an IDE disk with Ubuntu / GRUB. I can boot into Ubuntu with GRUB when I set SDB as primary boot device in my bios.
SDC only contains files.

My menu.lst tries to boot WinXP with these lines:
```

title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
makeactive
map 		(hd0) (hd1)
map 		(hd1) (hd0)
chainloader	+1

```
But when I select this boot option, I get an error message:
```

NTLDR is missing 
Press Ctrl Alt Del to Restart

```
I have tried tweaking the map command and tinkering with Windows' boot.ini, but without succes. I have read somewhere that at least this means that (hd1,0) is correct, but that's not much of a consolation as long as I get this error...

Your help is really appreciated!

---

### Post by confused57 on 2009-06-13
marcvangend,
   I believe grub is pointing to your NTFS partition on sdc1, you might try this entry for XP on sda1:
```
title		Microsoft Windows XP Professional
rootnoverify	(hd2,0)
savedefault
makeactive
map 		(hd0) (hd2)
map 		(hd2) (hd0)
chainloader	+1
```

---

### Post by marcvangend on 2009-06-14
confused57++!

Thank you so much, I remember I already tried hd2, but I must have made some kind of mistake or typo then #-o

So, does this mean that if you're booting from an IDE device, all IDE disks get their number first and the SATA disks are second in line?

Well, at least we learned that the "NTLDR is missing" error does *not* mean that GRUB is pointing to the right disk. Thanks again.

---

### Post by confused57 on 2009-06-14
> **marcvangend said:**
> confused57++!

Thank you so much, I remember I already tried hd2, but I must have made some kind of mistake or typo then #-o

So, does this mean that if you're booting from an IDE device, all IDE disks get their number first and the SATA disks are second in line?

Well, at least we learned that the "NTLDR is missing" error does *not* mean that GRUB is pointing to the right disk. Thanks again.

Glad you were able to get it working...it does seem most of the time IDE drives are numbered before SATA in grub's boot sequence.  Jaunty is the first Ubuntu version that didn't number my 3 hard drives(IDE, 2 SATA) according to bios boot sequence, all previous versions "guessed" it correctly.

---

### Post by Mukumbu on 2009-06-16
I can't seem to get my xp to boot after following your instructions.

here is my fdisk output:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000145d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       54817   440317521   83  Linux
/dev/sda2   *       54818       60800    48058447+   7  HPFS/NTFS

Disk /dev/sdb: 13.6 GB, 13672931328 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000277ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1030     8273443+  83  Linux
/dev/sdb2            1031        1094      514080    7  HPFS/NTFS
/dev/sdb3            1095        1662     4562460    5  Extended
/dev/sdb5            1095        1662     4562428+  82  Linux swap / Solaris

```

and the fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=ac335259-1c06-4f61-9000-a2450c999414 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=71436056-c354-4909-8cdc-08b873c132dd /home           ext3    relatime        0       2
# /dev/sdb5
UUID=1d6d7d36-1416-45e4-8831-2be16a2b1fb0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

This is the entry I added to the bottom of menu.lst:

```

title 		Windows XP Pro SP3
rootnoverify 	(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader +1
```

I get the "NTLDR is missing" message.

Please help.

Thanks.

---

### Post by unutbu on 2009-06-16
Mukumbu, you have two NTFS partitions: sda2 and sdb2.
Judging from the size of the partitions, I am guessing that sda2 contains your Windows XP.

sda2 in GRUB-speak is (hd0,1).

So try the following: Boot Ubuntu. Edit /boot/grub/menu.lst:
```

gksu gedit /boot/grub/menu.lst
```

Add a new boot stanza to the bottom of the file:

```
title		Windows XP Test
root		(hd0,1)
makeactive
chainloader	+1
```

Save and exit gedit. Reboot the machine, get to the GRUB menu, and select the line which says "Windows XP Test". See if that allows you to boot Windows.

---

### Post by Mukumbu on 2009-06-16
That worked!!  So now I just delete my old XP entry and rename test.

Thank you very much.  I've been trying to get this to work since last weekend.

---

### Post by val_u on 2009-06-18
```

sudo fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x407752c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+   7  HPFS/NTFS
/dev/sda2            4463       38913   276727657+   f  W95 Ext'd (LBA)
/dev/sda5            4463       15936    92164873+   7  HPFS/NTFS
/dev/sda6           15937       38913   184562721    7  HPFS/NTFS

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a75d228

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              13       91202   732478132    f  W95 Ext'd (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   *           1           3       24066   83  Linux
/dev/sdb5           14661       40157   204800368+   7  HPFS/NTFS
/dev/sdb6           40157       65654   204800368+   7  HPFS/NTFS
/dev/sdb7           65654       91202   205213648+   7  HPFS/NTFS
/dev/sdb8              13         985     7815559+  83  Linux
/dev/sdb9             986        1958     7815591   82  Linux swap / Solaris
/dev/sdb10           1959        2202     1959898+  83  Linux
/dev/sdb11           2203        3498    10410088+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30bfa281

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1862    14956483+   7  HPFS/NTFS
/dev/sdc2            1863       19457   141331837+   f  W95 Ext'd (LBA)
/dev/sdc5            1863        7727    47110581    b  W95 FAT32
/dev/sdc6            7728       19457    94221193+   7  HPFS/NTFS

```BIOS sees these disks in the order: sdc, sda, sdb.
Window XP is on the sdc1.
GRUB is on the sdb2.


```
cat /boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

``````
menu.lst
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

```And I get
NTLDR is missing
press Ctrl+Alt+Del to restart

every time I choose to load Win in the menu.

I tried to add
makeactive

and only received infinite
Starting up...

So for changing the OS I need every time to go to BIOS, to enter the password and to change which HDD I want to boot from.
Can anybody help me to find the right way with GRUB?

---

### Post by unutbu on 2009-06-18
val_u, try adding these two stanzas to the end of your menu.lst:

```
title        Microsoft Windows XP Professional (hd1,0)
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


title        Microsoft Windows XP Professional (hd0,0)
rootnoverify    (hd0,0)
savedefault
chainloader    +1
```

Then reboot and try booting each of these. Does either work?
If not, what error message(s) do you receive?

---

### Post by val_u on 2009-06-18
Second group gave me infinite Starting up...
And first one actually successfully loaded my Win.

**unutbu**, thank you very much. You broke my 2+ weeks chain of constant rebooting. One of my experiments was with hd1,0, but instead of maps it had makeactive.

Just for curiosity - is there any reasonable explanation why there should be hd1,0 instead of hd2,0?

And again, thanks. You saved me.

---

### Post by unutbu on 2009-06-18
val_u, I'm really glad you've got it working now.

Here is what I think was happening:

When you are booted into Linux, GRUB names the hard drives in the same order that Linux lists the hard drives. 

But when you are booting the computer, GRUB names the hard drives in the order that the BIOS lists the hard drives. 

Usually Linux and the BIOS list the drives in the same order, but that is not always the case. So what looks like sdc or (hd2) while booted into Linux, may be called something else when booting the computer. 

There is a way to use /boot/grub/device.map to force GRUB to name the drives in the order you desire. But instead of messing with that, I suggested the crude method of simply trying all possibilities.

See [http://ubuntuforums.org/showpost.php?p=3518911&postcount=9](http://ubuntuforums.org/showpost.php?p=3518911&postcount=9) for an example of how to use device.map to solve the problem. I think you were almost there, you just needed to do steps 9--14.

---

### Post by val_u on 2009-06-19
And I suspected it has something to do with different HDD order! You didn't only help me, you explained me the cause. Thanks again.

According to device.map... It didn't word for me. But I'm not sure it isn't an off-topic here. And I can't post in the thread pointed to by your link. Where should I ask about different result on step 11 there?

---

### Post by unutbu on 2009-06-19
val_u, I think it would be alright if you posted your question here. 

May I offer you a suggestion, however? If your current boot setup works, don't fix it. If you use mbwardle's instructions wrong, your system may become unbootable. 

As long as you are aware of this, and just want to learn or make your boot setup "perfect", I'm willing to try to help.

The correct command to use in step 11 depends on which drive you've told the BIOS to boot from.

PS. And finally, just so you'll know in the future, it is possible to post in the other thread. I only linked to a single post. To reply, you would need to click in the upper-right corner of the page on "Thread: Grub error 17". That will take you to the thread containing mbwardle's post. From there you could post a reply.

---

### Post by val_u on 2009-06-19
> **unutbu said:**
> val_u, I think it would be alright if you posted your question here. 
Ok, I'll explain what I did.

>  May I offer you a suggestion, however? If your current boot setup works, don't fix it.The question is more interested. I did the instructions how to change mapping. And it works, but in the strange way...
> If you use mbwardle's instructions wrong, your system may become unbootable. Yes, I know that. That's why I don't do advices at once. I want to understand what's going on under the hood. Maybe someday I will help somebody with that.
>  As long as you are aware of this, and just want to learn or make your boot setup "perfect", I'm willing to try to help.Yes, I want to do my system perfect. And I appreciate your help and advices very much.
> The correct command to use in step 11 depends on which drive you've told the BIOS to boot from.BIOS sees in the order sdc, sda, sdb and boots from sdb.
>  PS. And finally, just so you'll know in the future, it is possible to post in the other thread. I only linked to a single post. To reply, you would need to click in the upper-right corner of the page on "Thread: Grub error 17". That will take you to the thread containing mbwardle's post. From there you could post a reply.Yes, I noticed that you gave me the link to a single post. But there is is written:
[B]You are browsing a READ only archive
[/B]:-)
I'm going to explain what I did in the next post...

---

### Post by val_u on 2009-06-19
So I studied the [mbwardle]("http://ubuntuforums.org/member.php?u=31200")'s instructions.
Some details:
three HDD, which BIOS sees in the order sdc, sda, sdb and boots from sdb.
Win is on sdc, Ubuntu is on sdb.
When I was installing Ubuntu, there was the button Advanced. I don't remember clearly, but probably that was about Grub. And I installed it on sdb2. As I understand it should be visible as /boot, but fstab doesn't have such record.

So I booted Ubunty (from HDD, not from LiveCD if it matters) and changed device.map from
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

```to
```
(hd0)    /dev/sdc
(hd1)    /dev/sda
(hd2)    /dev/sdb

```Then I ran grub --device.map=device.map

Step 10 tells: Type "root (hd1,0)" (where hd1,0 is your Linux boot or root partition using the BIOS order)

I typed root (hd2,1)
(I expected my /boot partition there). It answered Ok.

I typed setup (hd2)
It answered that cannot find some files in the /root/boot, (filenames ended on stage-something).

So I returned to the previous step and tried using the root partition instead of boot.
root (hd2,7)
# / was on /dev/sdb8 during installation <= from fstab
Got Ok.

I typed setup (hd2).
From instruction: You should see a message that it's now telling GRUB to load 17+(hd1,0) instead of 17+(hd2,0) or something like that. This is what we want.
But I saw only few OK and Successful. Nothing like in the instruction.

So I quit from grub and added 
```
title        Microsoft Windows XP Professional - reordered
rootnoverify    (hd0,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

```and rebooted. And only sequence to successfull booting Win was the same that you previosly gave me:
```
title        Microsoft Windows XP Professional (hd1,0)
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```After I decided to run from Ubuntu:
grub --device.map=device.map
root (hd2,7)
 setup (hd2,1)
It answered few OK and two "couldn't. It's not fatal".
After this while booting I can see additional text - something about stage 1.5

So for now I have right mapping in the device.map, but in the menu.lst right sequence doesn't work. And I've got additional text while booting from GRUB (stage 1.5)
So I can't understand how mapping could be right, but Win still boots from hd1, instead of hd0 and how can I fix that.

---

### Post by unutbu on 2009-06-19
I'm surprised by the responses GRUB is giving you.
Could you please run boot_info_script ([http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)) and post the RESULTS.txt file?

---

### Post by val_u on 2009-06-19
I've read GRUB message while booting. It says
Loading stage1.5
few empty lines, and
Loading GRUB

Then comes the menu.

Little notice: /dev/sdh is a flash drive
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdh

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb9: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sdb2 and 
                       looks at sector 2273674 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #8 for 
                       /boot/grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdh2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdh3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdh4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x407752c6

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    71,682,029    71,681,967   7 HPFS/NTFS
/dev/sda2          71,682,030   625,137,344   553,455,315   f W95 Ext d (LBA)
/dev/sda5          71,682,093   256,011,839   184,329,747   7 HPFS/NTFS
/dev/sda6         256,011,903   625,137,344   369,125,442   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a75d228

Partition  Boot         Start           End          Size  Id System

/dev/sdb1             192,904 1,465,149,167 1,464,956,264   f W95 Ext d (LBA)
/dev/sdb5         235,520,271   645,121,007   409,600,737   7 HPFS/NTFS
/dev/sdb6         645,121,071 1,054,721,807   409,600,737   7 HPFS/NTFS
/dev/sdb7       1,054,721,871 1,465,149,167   410,427,297   7 HPFS/NTFS
/dev/sdb8             192,906    15,824,024    15,631,119  83 Linux
/dev/sdb9          15,824,088    31,455,269    15,631,182  82 Linux swap / Solaris
/dev/sdb10         31,455,333    35,375,129     3,919,797  83 Linux
/dev/sdb11         35,375,193    56,195,369    20,820,177  83 Linux
/dev/sdb2    *             63        48,194        48,132  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30bfa281

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    29,913,029    29,912,967   7 HPFS/NTFS
/dev/sdc2          29,913,030   312,576,704   282,663,675   f W95 Ext d (LBA)
/dev/sdc5          29,913,093   124,134,254    94,221,162   b W95 FAT32
/dev/sdc6         124,134,318   312,576,704   188,442,387   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 1020 MB, 1020748288 bytes
32 heads, 61 sectors/track, 1021 cylinders, total 1993649 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6f20736b

Partition  Boot         Start           End          Size  Id System

/dev/sdh1     ?   778,135,908 1,919,645,538 1,141,509,631  72 Unknown
/dev/sdh2     ?   168,689,522 2,104,717,761 1,936,028,240  65 Novell Netware 386
/dev/sdh3     ? 1,869,881,465 3,805,909,656 1,936,028,192  79 Unknown
/dev/sdh4     ? 2,885,681,152 2,885,736,650        55,499   d Unknown

/dev/sdh1 ends after the last sector of /dev/sdh
/dev/sdh1 overlaps with /dev/sdh2
/dev/sdh1 overlaps with /dev/sdh3
/dev/sdh2 ends after the last sector of /dev/sdh
/dev/sdh2 overlaps with /dev/sdh3
/dev/sdh3 ends after the last sector of /dev/sdh
/dev/sdh3 overlaps with /dev/sdh4
/dev/sdh4 ends after the last sector of /dev/sdh

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="364C30424C2FFAEF" LABEL="dvd" TYPE="ntfs" 
/dev/sda5: UUID="966C623B6C621671" LABEL="New Volume" TYPE="ntfs" 
/dev/sda6: UUID="2438C4D738C4A8DE" TYPE="ntfs" 
/dev/sdb2: UUID="4db9ad07-be0e-471d-8a07-d1d720db9d96" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="46EC15DBEC15C5D9" TYPE="ntfs" 
/dev/sdb6: UUID="00C83D08C83CFD8A" LABEL="good_humor" TYPE="ntfs" 
/dev/sdb7: UUID="0EE4511BE45105FD" TYPE="ntfs" 
/dev/sdb8: UUID="0fe8321f-06a9-4c7e-9fa1-fe8fc0589071" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb9: UUID="99c2c780-b218-42ce-ad79-515db875c8a3" TYPE="swap" 
/dev/sdb10: UUID="6d651c88-3b9a-4d77-a5c0-d3b0be5e6e1f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb11: UUID="1686d105-25dd-418a-8a02-86ec34d44371" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="1A0854A308547FA5" TYPE="ntfs" 
/dev/sdc5: UUID="8E1E-4E76" TYPE="vfat" 
/dev/sdc6: UUID="0E284AA5284A8BA1" LABEL="New Volume" TYPE="ntfs" 
/dev/sdh: UUID="78EA-ED11" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdh on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sdb8/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0fe8321f-06a9-4c7e-9fa1-fe8fc0589071
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0fe8321f-06a9-4c7e-9fa1-fe8fc0589071
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0fe8321f-06a9-4c7e-9fa1-fe8fc0589071
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

# following lines are made by val
title XP1 (+makeactive)
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


title        Microsoft Windows XP Professional (hd1,0)
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


title        Microsoft Windows XP Professional (hd0,0)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

# these are after changing hdd order
title        Microsoft Windows XP Professional (after reordering)
rootnoverify    (hd0,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071 /               ext3    relatime,errors=remount-ro 0       1
# /tmp was on /dev/sdb10 during installation
UUID=6d651c88-3b9a-4d77-a5c0-d3b0be5e6e1f /tmp            ext3    relatime        0       2
# /usr was on /dev/sdb11 during installation
UUID=1686d105-25dd-418a-8a02-86ec34d44371 /usr            ext3    relatime        0       2
# swap was on /dev/sdb9 during installation
UUID=99c2c780-b218-42ce-ad79-515db875c8a3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


   1.0GB: boot/grub/menu.lst
   1.1GB: boot/grub/stage2
   1.1GB: boot/initrd.img-2.6.28-11-generic
   1.1GB: boot/vmlinuz-2.6.28-11-generic
   1.1GB: initrd.img
   1.1GB: vmlinuz

================================ sdc1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdh

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 20 00  |.X.MSDOS5.0... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  b1 6b 1e 00 98 07 00 00  00 00 00 00 02 00 00 00  |.k..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 11 ed ea 78 4e  4f 20 4e 41 4d 45 20 20  |..)...xNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 08  |{......|.N..V@..|
00000070  cd 13 73 05 b9 ff ff 8a  f1 66 0f b6 c6 40 66 0f  |..s......f...@f.|
00000080  b6 d1 80 e2 3f f7 e2 86  cd c0 ed 06 41 66 0f b7  |....?.......Af..|
00000090  c9 66 f7 e1 66 89 46 f8  83 7e 16 00 75 38 83 7e  |.f..f.F..~..u8.~|
000000a0  2a 00 77 32 66 8b 46 1c  66 83 c0 0c bb 00 80 b9  |*.w2f.F.f.......|
000000b0  01 00 e8 2b 00 e9 48 03  a0 fa 7d b4 7d 8b f0 ac  |...+..H...}.}...|
000000c0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000d0  ee a0 fb 7d eb e5 a0 f9  7d eb e0 98 cd 16 cd 19  |...}....}.......|
000000e0  66 60 66 3b 46 f8 0f 82  4a 00 66 6a 00 66 50 06  |f`f;F...J.fj.fP.|
000000f0  53 66 68 10 00 01 00 80  7e 02 00 0f 85 20 00 b4  |Sfh.....~.... ..|
00000100  41 bb aa 55 8a 56 40 cd  13 0f 82 1c 00 81 fb 55  |A..U.V@........U|
00000110  aa 0f 85 14 00 f6 c1 01  0f 84 0d 00 fe 46 02 b4  |.............F..|
00000120  42 8a 56 40 8b f4 cd 13  b0 f9 66 58 66 58 66 58  |B.V@......fXfXfX|
00000130  66 58 eb 2a 66 33 d2 66  0f b7 4e 18 66 f7 f1 fe  |fX.*f3.f..N.f...|
00000140  c2 8a ca 66 8b d0 66 c1  ea 10 f7 76 1a 86 d6 8a  |...f..f....v....|
00000150  56 40 8a e8 c0 e4 06 0a  cc b8 01 02 cd 13 66 61  |V@............fa|
00000160  0f 82 54 ff 81 c3 00 02  66 40 49 0f 85 71 ff c3  |..T.....f@I..q..|
00000170  4e 54 4c 44 52 20 20 20  20 20 20 00 00 00 00 00  |NTLDR      .....|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader  on sdh1


Unknown BootLoader  on sdh2


Unknown BootLoader  on sdh3


Unknown BootLoader  on sdh4



=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdh1: No such file or directory
hexdump: /dev/sdh1: No such file or directory
hexdump: /dev/sdh2: No such file or directory
hexdump: /dev/sdh2: No such file or directory
hexdump: /dev/sdh3: No such file or directory
hexdump: /dev/sdh3: No such file or directory
hexdump: /dev/sdh4: No such file or directory
hexdump: /dev/sdh4: No such file or directory

```

---

### Post by unutbu on 2009-06-19
[list]
[*] mbwardle's post has a typographical error: the correct command is 
```

sudo grub --device-map=device.map
```

not
```

sudo grub --device.map=device.map
```

Notice the period should be a hyphen.

Did you already notice this typo? If you ran the command with the period you should have gotten an error:
```

% sudo grub --device.map=device.map
grub: unrecognized option '--device.map=device.map'
Try ``grub --help'' for more information.
```

[*]The RESULTS.txt output seems to suggest that sdb2 is not being used as a /boot partition. I don't think this partition contains any boot files. The sdb8 partition contains the /boot directory. That is why "root (hd2,7)" succeeded, but "root (hd2,1)" did not.

[*]Now to fix the device map. Do the following experiment:

```
sudo grub
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
```

You should see something like:

```
grub> geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/**sda**
...

grub> geometry (hd1)
drive 0x81: C/H/S = 60801/255/63, The number of sectors = 976773168, /dev/**sdb**
...

grub> geometry (hd2)
drive 0x82: C/H/S = 243/255/63, The number of sectors = 3915776, /dev/**sdc**
...
```

The details will be different, but notice how (hd0) is associated with /dev/sda,
(hd1) with sdb, and (hd2) is associated with sdc.

Now quit grub and run this:
```

cd /boot/grub
cat device.map
```

Check that you should see:
(hd0)    /dev/sdc
(hd1)    /dev/sda
(hd2)    /dev/sdb

```
sudo grub --device-map=device.map
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)

```
Now you should see
```
grub> geometry (hd0)
drive 0x80: C/H/S = 243/255/63, The number of sectors = 3915776, /dev/sdc
...

grub> geometry (hd1)
drive 0x81: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
...

grub> geometry (hd2)
drive 0x82: C/H/S = 60801/255/63, The number of sectors = 976773168, /dev/sdb
...
```

Notice how the associations are now different:
(hd0) <--> sdc
(hd1) <--> sda
(hd2) <--> sdb

just like you defined them in /boot/grub/device.map.

Verify that you get the right output from the geometry commands.

Once you've got that working, then proceed (again) with mbwardle's instructions:

```
root (hd2,7)
setup (hd2)
quit

```
Now since (hd0) is sdc, you should be able to boot XP with this menu.lst boot stanza:
```

title        Microsoft Windows XP Professional (hd0,0)
rootnoverify    (hd0,0)
savedefault
chainloader    +1
```

If this does not work, but booting (hd1,0) does work, then it means your Windows XP is on sda1, rather than sdc1.
[*]
```
title        Microsoft Windows XP Professional (after reordering)
rootnoverify    (hd0,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1
```

The map commands swap the meaning of (hd0) and (hd2) right before booting Windows.
This is done because Windows expects itself to be on the first boot drive, (hd0).
Since we are using device.map to make (hd0) the Windows drive, you should not need 
the map commands. Indeed, whenever (hd0,Y) is used on the rootnoverify (or root) line in menu.lst,
```

rootnoverify    (hd0,0)
```

you should not use map commands.
[/list]

Hope this helps.

---

### Post by val_u on 2009-06-19
[unutbu]("http://ubuntuforums.org/member.php?u=518895"), I noticed that typo with -/.

One more question: can I do that from Ubuntu on my HDD? Or should I use the LiveCD?

P. S. Win is definitely on sdc1. I'm 100% sure about it.

---

### Post by unutbu on 2009-06-19
You can run all the grub commands while booted into Ubuntu.
Most GRUB instructions say boot from the LiveCD only because most people can't boot by the time they mess with GRUB.

---

### Post by val_u on 2009-06-19
I've tried.
```
valery@val-desktop:~$ cat /boot/grub/device.map
(hd0)    /dev/sdc
(hd1)    /dev/sda
(hd2)    /dev/sdb
valery@val-desktop:~$ sudo grub
[sudo] password for valery: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> geometry (hd0)
geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> geometry (hd1)
geometry (hd1)
drive 0x81: C/H/S = 25665/255/63, The number of sectors = 1465149168, /dev/sdb
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 8,  Filesystem type unknown, partition type 0x82
   Partition num: 9,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 10,  Filesystem type is ext2fs, partition type 0x83
grub> geometry (hd2)
geometry (hd2)
drive 0x82: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is fat, partition type 0xb
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> quit
quit
valery@val-desktop:~$ cd /boot/grub
valery@val-desktop:/boot/grub$ cat device.map
(hd0)    /dev/sdc
(hd1)    /dev/sda
(hd2)    /dev/sdb
valery@val-desktop:/boot/grub$ sudo grub --device-map=device.map

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> geometry (hd0)
geometry (hd0)
drive 0x80: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is fat, partition type 0xb
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> geometry (hd1)
geometry (hd1)
drive 0x81: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> geometry (hd2)
geometry (hd2)
drive 0x82: C/H/S = 25665/255/63, The number of sectors = 1465149168, /dev/sdb
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 8,  Filesystem type unknown, partition type 0x82
   Partition num: 9,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 10,  Filesystem type is ext2fs, partition type 0x83
grub> root (hd2,7)
root (hd2,7)
grub> setup (hd2)
setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+17 p (hd2,7)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
valery@val-desktop:/boot/grub$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        0fe8321f-06a9-4c7e-9fa1-fe8fc0589071
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        0fe8321f-06a9-4c7e-9fa1-fe8fc0589071
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=0fe8321f-06a9-4c7e-9fa1-fe8fc0589071 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        0fe8321f-06a9-4c7e-9fa1-fe8fc0589071
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
rootnoverify    (hd2,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

# following lines are made by val
title XP1 (+makeactive)
rootnoverify    (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1


title        Microsoft Windows XP Professional (hd1,0)
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


title        Microsoft Windows XP Professional (hd0,0)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

# these are after changing hdd order
title        Microsoft Windows XP Professional (after reordering)
rootnoverify    (hd0,0)
savedefault
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1

valery@val-desktop:/boot/grub$ 



```Then rebooted. I chose in the menu item Microsoft Windows XP Professional (hd0,0)
It gave me infinite Starting up....
I chose Microsoft Windows XP Professional (hd1,0)
It successfully loaded Win.
I booted Ubuntu.
```
valery@val-desktop:~$ sudo grub
[sudo] password for valery: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> geometry (hd0)
geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> geometry (hd1)
geometry (hd1)
drive 0x81: C/H/S = 25665/255/63, The number of sectors = 1465149168, /dev/sdb
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 8,  Filesystem type unknown, partition type 0x82
   Partition num: 9,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 10,  Filesystem type is ext2fs, partition type 0x83
grub> geometry (hd2)
geometry (hd2)
drive 0x82: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is fat, partition type 0xb
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> quit
quit
valery@val-desktop:~$ cat /boot/grub/device.map
(hd0)    /dev/sdc
(hd1)    /dev/sda
(hd2)    /dev/sdb
valery@val-desktop:~$ 

```As you can see nothing changed.

And I remembered one detail. While installing Ubuntu, I chose that small /dev/sdb8 as a /boot. And after that button Advanced, I chose it for dual system booting.

---

### Post by unutbu on 2009-06-19
Okay, val_u. I think I understand now that I have been operating under a misunderstanding of what device.map does.

The BIOS decides on an order for the hard drives. We basically do not have control over this (unless you reprogram the BIOS, or physically swap the cables connecting the drives to the computer). GRUB uses the BIOS's drive order to assign a mapping between (hdX) and physical drives. Since this depends on the BIOS, we don't have a choice about this either. 

All that device.map can do for us is tell GRUB (while running Linux) to use a particular mapping between (hdX) and the physical drives. (By the time you are running Linux, GRUB seems to forget the BIOS drive order and instead rely on the order in which Linux lists the drives.)  Although you can use device.map to create any mapping you like, since the BIOS's drive order is immutable, there is only one useful mapping -- the mapping that matches the BIOS's choices. 

In mbwardle's example, he changes his device.map to conform to the BIOS order.
Then his "root (hdX,Y)" and "setup (hdX)" commands can use the same terminology as GRUB would find while booting. That's all it does. 

So the best we can do is edit device.map to

(hd0)    /dev/sda
(hd1)    /dev/sdc
(hd2)    /dev/sdb

Since you already have found this to work,
```

title        Microsoft Windows XP Professional (hd1,0)
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

we can conclude that the BIOS believes sdc is your second drive. I can be wrong, but I now believe this condition is immutable unless you physically swap hard drive cables.

Apologies for leading you on this wild goose chase...

---

### Post by val_u on 2009-06-19
unutbu, there is nothing to apologize for. It was interesting and was getting clearer for me until your last post...

I have a long story with linux. I'm not a big fan of Win, so many years ago I decided to install Linux. I got three different installation (one of them was Red hat) from three different people. And every installation ended with signal 9 while installing. None of these people could resolve that problem. So I stuck up with OS/2 for years (which installed successfully without any signals). So I think Linux again shows its love to me :-)

Now to the HDD order. About 6 months ago I switched cables to get order sdc, sda, sdb.
sdc is IDE, sda and sdb are PATA.
This order is in the BIOS HDD menu, in the boot order menu, while booting PC. And even Win sees disks in this order. So I think we missed something.

Your theory isn't right because of device.map. When is it used? While booting on the GRUB stage? No - it doesn't boot Win from where it is in the device.map.
When Ubuntu is loaded? But why I got:
```
valery@val-desktop:~$ sudo grub
[sudo] password for valery: 
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> geometry (hd0)
geometry (hd0)
drive 0x80: C/H/S = 38913/255/63, The number of sectors = 625142448, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> geometry (hd1)
geometry (hd1)
drive 0x81: C/H/S = 25665/255/63, The number of sectors = 1465149168, /dev/sdb
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type unknown, partition type 0x7
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 8,  Filesystem type unknown, partition type 0x82
   Partition num: 9,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 10,  Filesystem type is ext2fs, partition type 0x83
grub> geometry (hd2)
geometry (hd2)
drive 0x82: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is fat, partition type 0xb
   Partition num: 5,  Filesystem type unknown, partition type 0x7
grub> quit
quit
valery@val-desktop:~$ cat /boot/grub/device.map
(hd0)    /dev/sdc
(hd1)    /dev/sda
(hd2)    /dev/sdb
valery@val-desktop:~$ 

```That's again not the device.map order. And as you could see Microsoft Windows XP Professional (hd1,0) loaded the same Win with two different device.map. We just missed something...

---

### Post by unutbu on 2009-06-19
If you follow the thread after mbwardle's post, there is more discussion about device.map mainly between MQMike and Herman.

Check out Herman's massive experiment:
[http://ubuntuforums.org/showpost.php?p=3650311&postcount=33](http://ubuntuforums.org/showpost.php?p=3650311&postcount=33)

Here he attempts to purposefully messup his device.map, reinstall GRUB, and see if device.map has any affect on his installation. It never does. 

I know I can be wrong on matters of GRUB, BIOS (and most things in general), but as far as I can see my previous explanation is consistent with all the evidence. The device.map is not read at boot time, it does not affect how GRUB names the devices at boot time. It only affects how GRUB names the devices when running "sudo grub" from within Linux.

How the BIOS decides on the order is a mystery to me. I'm not even sure if it is necessarily the same as the BIOS boot order. In fact, it probably is not the same since you can change the order in which the BIOS lists drives by swapping cables (as evidenced by a change in the names GRUB assigns to drives at boot time), and yet preserve the same BIOS boot order. 

Windows, like Linux, may have their own method of ordering and naming drives. By swapping the cables to create a desired order while in Windows does not guarantee that Linux will choose the same ordering. And if Windows is like Linux, then neither order has any relationship to the BIOS order.

Anyway, these are just my speculations. If you find out differently, please let us know!

---

### Post by val_u on 2009-06-19
> **unutbu said:**
> I know I can be wrong on matters of GRUB, BIOS (and most things in general),
Don't say that, please. You gave me the right sequence to boot Win. So with GRUB I can boot into Win or Ubuntu. 
> The device.map is not read at boot time, it does not affect how GRUB names the devices at boot time. It only affects how GRUB names the devices when running "sudo grub" from within Linux.But in my previous post I posted results from "sudo grub" from within Ubuntu (from HDD) and content of device.map. The order wasn't the same.
> Anyway, these are just my speculations. I could be wrong -- I certainly have been wrong about many things before. If you find out differently, please let us know!That is definitely interesting topic for me. I'm going to study the tread that you pointed to. If I find something interesting, I'll write it here.
That was very useful conversation. Thank you, unutbu for your help.

---

### Post by unutbu on 2009-06-19
> But in my previous post I posted results from "sudo grub" from within Ubuntu (from HDD) and content of device.map. The order wasn't the same.

Ah, yes. When I wrote, "It only affects how GRUB names the devices when running "sudo grub" from within Linux." it would have been more accurate to write "It only affects how GRUB names the devices when running "sudo grub **--device-map=device.map**" from within Linux."

You're post #261 shows this.

> 
That was very useful conversation. Thank you, unutbu for your help.

No problem. Enjoy Ubuntu! :p

---

### Post by lupeatx on 2009-12-01
Copy and paste the following lines above the line
###BEGIN AUTOMAGIC KERNEL LIST
```

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```Ok I'm stuck on this. Is this suppose to be copied into the gedit text editor?

I did that already and saved it. When I go to boot up it load straight to Ubuntu. Now I'm doing this after installing Ubuntu 9.10, Should this still work?

I opened terminal and did the whole *sudo fdisk -l* and trhis is what I got

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7749a9e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3493    28057491   83  Linux
/dev/sda2            3494        3649     1253070    5  Extended
/dev/sda5            3494        3649     1253038+  82  Linux swap / Solaris

By the looks of it, it does not see my 2nd HD. I got everything plugged in correct. Jumpers are correct too.

---

### Post by unutbu on 2009-12-01
lupeatx, unfortunately, I don't know the answer to your problem.
As you pointed out, it looks like this is a hard drive detection problem, not (at least at the moment) a dualboot/GRUB problem.

I suggest you start a new thread so people knowledgable about hard drive detection might see it more quickly.

---

### Post by lupeatx on 2009-12-01
Thanks! I got it to see my 2nd HD but having another issue.

---

### Post by robbielink on 2009-12-03
First wanted to say many, many thanks to confused57 for starting this excellent thread and to the many others who contributed along the way. I think the answers to just about any scenario are contained in this thread but there's a lot of reading to be done.

Secondly - if you have a Dell machine you will most likely have problems. I don't know if all models have the Dell Utility Partition but the ones that do present a special case (read the thread) - basically your Dell drive boots from hd0,1 - not hd0,0. If you don't pay attention to this you will be frustrated!

Thirdly - It would be nice if everyone could just follow the instructions in the original post and have everything work out fine. For many folks that's the way it is but there are so many other issues that can crop up. The answers are here - don't give up! I spent several hours with a machine that would not boot anything last night and just kept reading and trying things. Even the SuperGrubDisk couldn't help me out (maybe it could've if I understood it better - perhaps a better English translation would help...). In addition to dealing with the Dell Utility Partition, I think I screwed up by not properly uninstalling Wubi, then probably did some stupid things with SuperGrubDisk (a little knowledge can be a dangerous thing) and it's quite possible that my Grub installation on my fresh Ubuntu9.10 install was corrupted. Who knows. At any rate I finally managed to get into the Ubuntu install, reinstalled Grub, ran update-grub (I highly recommend trying that if you're stuck) and made the adjustments to menu.lst to accommodate my DUP and finally success! So if someone as clueless as me can do it you can, too. Be persistent. 

Thanks again to the Ubuntu community.

---

### Post by Trinity1976 on 2009-12-04
I have no file called 'menu.lst' in my grub directory. Does anyone know if things are different in Karmic?

---

### Post by robbielink on 2009-12-05
> **Trinity1976 said:**
> I have no file called 'menu.lst' in my grub directory. Does anyone know if things are different in Karmic?

I didn't either - and that was why I wasn't able to boot directly into Ubuntu.  I had to reinstall grub and then run "update-grub" which then asked me if I wanted to create a menu.lst which then solved my boot problem (after I edited it to accommodate the Dell Utility Partition on my Windows drive.)

---

### Post by Trinity1976 on 2009-12-05
I think the new equivalent is grub.cfg. I tried lots of different combinations of master and slave with my drives and couldn't even get Windows to boot up if I selected the drive manually in the Boot menu.

So I've given up on dual-booting and am going to set up a Virtual Box instead. Windows was on a very old 20GB hard-drive anyway, and it's probably best I get rid of it.

---

### Post by natgab on 2010-01-04
I wanted to add my set-up to the information in this tutorial, and thank Confused57 for making this tutorial.  

I was able to use the information here in this thread to make a dual boot set-up of Ubuntu Studio 9.04 and Haiku.  

I will describe my HD set-up:

Master SATA 160GB HD / SDc / ubuntu / start-up

Master SATA  80GB HD / SDb / blank  / non-formated

Slave  IDE   10GB HD / SDa / haiku  / 2nd system

Please note that Ubuntu 9.10 and later use GRUB-2 and this is only for Ubuntu 9.04 or older.

Below is my GRUB list.  

```
Notes for GRUB errors:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-17-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

__________________________________

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

### timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#
#

# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fad67457-b54e-46e4-8540-613cce54dcdc ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fad67457-b54e-46e4-8540-613cce54dcdc

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-17-generic
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-17-generic root=UUID=fad67457-b54e-46e4-8540-6$
initrd          /boot/initrd.img-2.6.28-17-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-17-generic root=UUID=fad67457-b54e-46e4-8540-6$
initrd          /boot/initrd.img-2.6.28-17-generic

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=fad67457-b54e-46e4-8540-6$
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=fad67457-b54e-46e4-8540-6$
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, kernel 2.6.28-3-rt
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=fad67457-b54e-46e4-8540-613cce5$
initrd          /boot/initrd.img-2.6.28-3-rt
quiet

title           Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=fad67457-b54e-46e4-8540-613cce5$
initrd          /boot/initrd.img-2.6.28-3-rt

title           Ubuntu 9.04, memtest86+
uuid            fad67457-b54e-46e4-8540-613cce54dcdc
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Haiku OS
rootnoverify    (hd2,0)
chainloader     +1



```

Also if this is helpful, here is the info from fdisk:

```

Disk /dev/sda: 10.2 GB, 10242957312 bytes
255 heads, 63 sectors/track, 1245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006bce6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1245    10000431   83  Linux

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed385

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18716   150336238+  83  Linux
/dev/sdc2           18717       19457     5952082+   5  Extended
/dev/sdc5           18717       19457     5952051   82  Linux swap / Solaris
```

Hopefully this will help someone and also encourage more linux users to also test Haiku. :lolflag:

---

### Post by trickpat on 2010-01-13
HI. this post has been really helpful so thanks.  i've had problems doing this before, and i managed to get it working once so i'm fairly confident i can do it again... but something isn't quite working right.. so i could really use some help.  Thanks in advance for any tips :) 

Right now, i've got windows 7 installed on a slave 500 Gig IDE drive and ubuntu 9.10 freshly installed on a 250 Gig Sata drive.  I installed them both seperately with only one hard drive connected at a time.   when i boot with both hard drives connected it's not giving me the option to boot either, it just automatically boots into ubuntu. which is great because it means i can just go into terminal and change the boot bios right?  so here's my drive configureation when i type :

sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x283f283e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30027   241191846   83  Linux
/dev/sda2           30028       30401     3004155    5  Extended
/dev/sda5           30028       30401     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x48cb4d3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      969018   488385040+   7  HPFS/NTFS
patrick@patrick-desktop:~$ 


So i think i just need to tweek the line that i put in the edited menu.lst 
gksudo gedit /boot/grub/menu.lst
title                Windows XP Professional
root                (hd1,0)
savedefault
makeactive
chainloader        +1
map (hd0) (hd1)
map (hd1) (hd0)


replace windows xp professional with Windows 7

and change the Hd0 HD 1 Lines but.. i cant figure what i need to change.  any tips?  or anything else i need to change?  i tried putting it in unchanged just the way i pasted it there and i thought it would work.. but it didn't seem to do anything.  I used to have XP and ubuntu running like this on 2 hard drives and it worked great so i hope i can figure this out.  Thanks for your time!

---

### Post by ssican on 2010-01-16
[B]TIP

-BOOTING XP ON A NON-FIRST HARD DRIVE-[/B]

SOURCE:
KubuntuForums.net
GRUB 2 A Guide for Users
AUTHOR: Qqmike

[http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)

On Reply #1 -POST 2-
[http://kubuntuforums.net/forums/index.php?topic=3106368.msg195829#msg195829](http://kubuntuforums.net/forums/index.php?topic=3106368.msg195829#msg195829)

Qqmike Recommend:
- Run First: grub install
  [B]sudo grub-install
  before running
  sudo grub-mkconfig -o /boot/grub/grub.cfg[/B]


(Qqmike wrote:
**grub-mkconfig   Detecting other OSs**
grub-mkconfig automatically runs os-prober to detect other OSs on your PC (assuming os-prober is installed, which it will be in any normal installation).

**grub-mkconfig:  Is grub.cfg in sync with core.img?**
=> **Run first: grub-install**
To be sure you get the best and the correct grub.cfg file, especially if there's been a change/update to core.img, it would be safe to run
[B]sudo grub-install
before running
sudo grub-mkconfig -o /boot/grub/grub.cfg [/B]


**XP on a non-first hard drive: (hdx,y), x > 1**
Qqmike recommend:
See the following section titled  "**Booting XP on a non-first hard drive: The _drivema_p command in GRUB 2.**"  

=> => Fact is, **_you might be able to use the GRUB 2  utility grub-mkconfig or grub-install to do this work for you_**:  **_they might detect Windows properly and adjust for Windows being on a non-first HD (by implementing the drivemap commands automatically_**).  (For the commands grub-mkconfig and grub-install, see Notes about some of the new GRUB 2 commands (in Reply #1 above); also see SECTION 3: Fixing Things)


**Booting XP on a non-first hard drive The _drivemap_ command in GRUB 2**
Qqmike wrote: "I will present you with safe options that will not harm your GRUB 2 or dual-booting setup.

For a more compact Method 2 and **for technical notes and other useful details** about how drivemap works, see Reply #17.   (Later, Reply # 17 may be incorporated here.)

The Quick-and-Dirty Solution

Method 1
To boot Windows XP installed to (hd1,1), use the following menuentry (in a script you write as a text file (and make executable) in the folder /etc/grub.d):

#  Method 1 -- a safe, sure way to do it
# This method applies to Windows and to FreeDOS
# Windows XP on sdb1 (= (hd1,1)
menuentry “Windows XP on sdb1, by chainloader”  {
drivemap (hd0) (hd1)
drivemap (hd1) (hd0)
set root=(hd0)
chainloader  (hd1,1)+1 }


=> **_The drivemap command in GRUB 2 replaces the map command in GRUB Legacy_**.
=> That's all you need to know to make your grub.cfg work.

=> => Fact is, **_you might be able to use the GRUB 2  utility grub-mkconfig or grub-install to do this work for you_**:  **_they might detect Windows properly and adjust for Windows being on a non-first HD (by implementing the drivemap commands automatically_**).  (For the commands grub-mkconfig and grub-install, see Notes about some of the new GRUB 2 commands (in Reply #1 above); also see SECTION 3: Fixing Things"

EDIT 1
USING -sudo grub-install- **Herman** recommend to specify the Disk you wish to Install Grub:

**sudo grub-install /dev/sda**

Where: /dev/sda is the disk you wish to install GRUB to, (boot.img to first hard disk MBR), otherwise use '/dev/sdb' for second hard disk or '/dev/sdc' for third hard disk
How to Install, update and repair GRUB:
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#install_update_and_repair](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#install_update_and_repair)

---

### Post by betterspud on 2010-03-23
Ok. I am a complete noob with linux systems and have no real clue what I'm doing.

Have read through many posts about changing Grub and am having no luck.

Whenever I try to save an edited version of grub.cfg I get a 'could not save the file' error because it is read only and I do not have permission. I thought that using sudo would allow me to save it?

What am I doing wrong?

EDIT: Just discovered that on 9.10, it uses Grub2.0 and that you CANNOT edit grub.cfg, but have to change the default within /etc/default/grub instead.

Have just installed startup manager from the package list and am configured through that. Hopefully, it will do the job...

---

### Post by eljefe on 2010-04-19
I havent had any luck here with my dual HD booting, as per this tutorial:
[http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives#References](http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives#References)

I got the required details into the grub menu and it all comes up great, the only problem is that when I hit the "Windows" option it says:

Error 21: Selected disc does not exist
Press any key to continue.....

When I do this Mint 7 loads as expected.

I have the HD1 cable plugged into the Linux HD and the HD2 cable plugged into the XP HD. The XP install was acatually done on this box, so I know it goes.

Normally in this machine HD1 cable goes to the XP HD, and the Mint HD is not there at all.

Both HDs were set with cable select positions for the jumpers, which is how the XP drive was installed too.

I then dicked about with the Jumpers.

Cable select for both HD's (Error 21)
Mint on cable select, Windows on slave (Error 21)
Mint on master, window on slave (No grub menu, just Error 21)

Has anyone got any clues on how to trouble shoot from here?

My bios says:

```
SATA Primary drive    OFF
SATA Seconday drive         OFF
Primary Master drive        HARD DRIVE
Primary Slave drive         OFF
Secondary master drive      cdrom device
Secondsary slave drive      OFF 

IDE drive  UDMA             ON
```

This is for my daughter. I want her to keep using Linux but want to have the windows boot as a last resort.

---

### Post by confused57 on 2010-04-19
Hi eljefe,

You might see if there is an option in your bios to turn on your primary slave controller:
```
SATA Primary drive    OFF
SATA Seconday drive         OFF
Primary Master drive        HARD DRIVE
Primary Slave drive         [COLOR="Red"]OFF[/COLOR]
Secondary master drive      cdrom device
Secondsary slave drive      OFF
```

I had a Dimension 4550, which would show grub error 21 if the primary slave controller was set to off...had to set it to "auto" to get Windows to boot properly.   

Here's an excellent explanation of error 21 & possible causes:
[http://members.iinet.net.au/~herman546/p15.html#21](http://members.iinet.net.au/~herman546/p15.html#21)

---

