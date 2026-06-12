---
title: "Installed Ubuntu onto a brand new 1tb hard drive and I get a dark blue screen"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by SBTlauien on 2013-06-22
-AMD Athlon 64 bit with NVIDIA GeForce FX 5900 and a brand new 1tb hard drive
-Not dual booting
-Same PC runs Windows XP on a different hard drive
-Only had in the 1tb hard drive while installing

I installed Ubuntu from a DVD(the md5 matched), then took out the DVD and restarted my PC after the install(as instructed). *Once Ubuntu booted, I was able to login on the login screen, but afterwards, it gave me a pure dark blue screen that had a movable cursor, and the cursor changed at certain parts of the screen.

I pressed ALT-CNTRL-DEL and the screen change to a pure white screen.

Can anyone help me get Ubuntu working?

Sorry if this is in the wrong section.

---

### Post by mips on 2013-06-22
Probably a video driver issue.

---

### Post by SBTlauien on 2013-06-22
Do you know how I can fix that?

---

### Post by grahammechanical on 2013-06-22
What did the log in screen look like? Your reference to a dark blue screen after log in is a puzzle to me. Are you sure you installed Ubuntu and not Ubuntu Gnome? Ubuntu has a default purple and orange swirl for a background image for the log in screen and that continues onto the desktop until we set a background image of our choice in System Settings>Appearance.

Do you get a Grub boot menu? If not try holding down the Shift key as the machine loads. At the Grub boot menu select Advanced Options for Ubuntu ( I am assuming that you are using 12.10 or 13.04 - you do not tell us - not my fault if the instructions are wrong) and select Recovery Mode. At the Recovery Mode screen select Resume. That will sometimes get us to a desktop that works.

From there you need to load System Settings and open Software & Updates and go to the Additional Drivers tab and experiment with different video drivers. Give the utility a few seconds to gather it list together.

I think that you have installed Ubuntu Gnome and I cannot direct you on how to change video drivers on Ubuntu Gnome as I have not tried that for about six months.

Regards.

---

### Post by SBTlauien on 2013-06-22
Thank you so much.

So, is holding down the shift key to get this Grub menu basically the same as pressing F8/F10 in Windows to get the menu with safe mode?

---

### Post by oldfred on 2013-06-22
If you have Windows on another drive and after you get system working. Run this.
sudo update-grub

Then you will always get grub menu as you will have the option to boot Ubuntu or Windows.

I have an older nVidia card and have to use nomodeset on first boot after an install. But you have to get to grub menu, press e to edit boot stanza, scroll down to linux line and replace quiet splash with nomodeset.

Screens shown here:
       How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by SBTlauien on 2013-06-22
I'm running 13.04, not sure if I'm running Gnome, but I'm quit sure it was the full install 64 bit download.

The 'Additional Drivers' tab in 'Software & Updates', is empty.  I am connect to the internet.

It only seems to boot through the Grub menu, and it seems slow.

It shows 'VESA: NV35 Board - p172-1n' as my graphics driver, but I'm assuming it's not loading when I boot this way, and it's what's causing this issue.  But I'm not sure.

---

### Post by SBTlauien on 2013-06-22
Alright, did just as you said, and I get the nice boot menu(I also have a 1.55gb hard drive with Windows 98 lol), changed it to 'NOMODESET', and it boots, but it still seems really slow.

I also got an error message.

---

### Post by SBTlauien on 2013-06-22
Actually, it still gives me a pure blank screen but I'm able to move my cursor.  This time it was white until I pressed CNTRL-ALT-DEL, then it turned black.  The cursor can be moved around though.

It did load when I choose those suggested options, but just slow.

---

### Post by sandyd on 2013-06-22
moved to absolute beginners section

---

### Post by oldfred on 2013-06-22
How much RAM do you have? If system is that old it may need Lubuntu not full Ubuntu as that needs a good video system.

You need the older 173.xx series nVidia driver.
[http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precise](http://askubuntu.com/questions/153915/how-to-install-drivers-for-nvidia-geforce-fx-5200-on-precise)

       Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.

[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by SBTlauien on 2013-06-22
Well I have two 512mb sticks of RAM, but one of the four slots is broken on my PC, so I run the two sticks in DIMM 1 and DIMM 2, rather than DIMM 1 and DIMM 3(which is the broken slot).  It's has dual channel for RAM, 1&3 are channel A, and 2&4 are channel B.  So I have them mixed.

---

### Post by SBTlauien on 2013-06-22
Oh yeah, I ran the memory test and it passed at 100%.

---

### Post by SBTlauien on 2013-06-22
I looked on the installation DVD and it had "Wubi" as the launcher.

Is that was it's suppose to be, or did I mess up there?

It's running extremely slow(lagging).

---

### Post by oldfred on 2013-06-22
I think there is a wubi file on the Installer, but the newer versions only install wubi from inside Windows not as full partitioned install. Also the very newest will not have wubi at all. Part is that all new computers are UEFI with gpt partitioning and wubi does not work with gpt partitioned drives.

If you have full Ubuntu are you running Unity. I run fallback or gnome-panel which is more like the old versions with top & bottom panels and menus not the list of icons on the left. Unity needs a good video system to run well. 

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by SBTlauien on 2013-06-23
I don't think I have 'Unity'.  I searched for it and nothing came up.

I'm getting popups that say there is a "System Software Problem", and it's running waaaaay slow.

Could this just be a graphics card, or should I reinstall?

I didn't do anything for partitioning when installing, could that be an issue?  I think I've heard that it's possible to create a partition that acts like memory...

---

### Post by SBTlauien on 2013-06-23
My only two options in the "Additional Drivers" menu are...

-Using NVIDIA binary Xorg driver, kernel module and VDPAU library from NVIDIA-173(propriety, tested)
-Using X.Org X Server - Nouveau display driver from server-xorg-video-nouveau(open source)

It's been on the second one, so I'll try the first.  I've actually tried a few times today but it takes forever and freezes.

This install was done while connected to the internet.

---

### Post by SBTlauien on 2013-06-23
Still got stuck on a pure colored screen with a movable cursor right after entering my password.

---

### Post by oldfred on 2013-06-23
It is some sort of video issue.

You can post this from live installer or if you can get into your system to show partitions.

sudo parted -l
That is an el, not cap I or number 1.

Swap is the partition used as RAM. If you use swap system will be real slow.

I might reinstall with Lubuntu. But you either need to erase existing partition or use manual install to reuse partitions. Or if only system on drive to full drive overwrite will also work.

---

### Post by SBTlauien on 2013-06-23
Is there an option to not use SWAP when I install?  I didn't see an option at the partition screen, I just choose the top option to use the entire drive.

I did notice though, that when it's booting, there is a red "FAILED" noted, but it goes by to fast for me to be able to read.  Is there anywhere I can check that?

I can get into the OS, it's just really slow/laggy.

---

### Post by oldfred on 2013-06-23
All the lines that scroll by if you do not have quiet splash in boot are in a log file dmesg.

I have a Log File Viewer but do not remember if I installed it or was was part of install?

But they all are text files in /var/log. There are a lot of log files.

If you use manual install or something else you can install without swap. Best only if you have a lot of RAM or over 4GB. You can also change swapiness.

 [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by SBTlauien on 2013-06-24
I installed Ubuntu 12.04 this time, it asked me to reboot, and now allot says is...

"error: unknown filesystem
grub rescue>"

---

### Post by SBTlauien on 2013-06-24
I got the Boot-Repair-ISO, wrote the image to a flash drive, ran it, and it fix my Grub menu.

Ubuntu 12.04 is also working, except I can't see any icons in the bar that is on the left(dash?) but it displays options if I move my mouse up and down in the area.

Also, I updated Grub and at the Grub menu, there is "Windows 7(loader) (on /dev/sda1)" but it will not load Windows 7.

What happened to my other OS in this menu(Windows 98 on my 1.55gb hd, Windows XP on my 90gb hd, and Windows 7)?

In Ubuntu, I can see the hard drives, and they were all working before.  Also, my 1tb hard drive is partitioned in two halfs, one for Ubuntu and one for Windows 7.

---

### Post by oldfred on 2013-06-24
If you can see the other drives, run this for grub2's os-prober to find the installs.

sudo update-grub

If that does not add the other installs post the link to a new BootInfo report from Boot-Repair.

I do not know Unity, but think it has settings to auto-hide?
I prefer the old gnome2 style (gnome-panel or fallback) as I have a 4:3 monitor and have more space at top and bottom of screen for panels. Plus oldfred is getting to the point where change is more difficult.

---

### Post by SBTlauien on 2013-06-24
[http://paste.ubuntu.com/5794912/](http://paste.ubuntu.com/5794912/)

It shows the other OS on the other drives, and the Windows 7 on the other partition.  It doesn't show ip in Grub.  I think it's Grub2 that I have, I downloaded the Boot-Repair-Disk from Ubuntu's website.

---

### Post by oldfred on 2013-06-24
What is this?
 /dev/mapper/nvidia_bagbhdhc

It looks like part of an old BIOS RAID install? And the error then stops grub from scanning drives.

Your Windows in sda1 does not have the separate 100MB boot/repair boot partition that is common with Windows 7, but your have the missing Windows boot files in the FAT32 partition sdc1.
It looks like when you installed Windows to sda, you had BIOS set to boot from sdc, so Windows put its boot files into sdc1.

      
 Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

I would move the Windows boot files into the Windows install in sda1, add a Windows boot loader into the MBR of sda and see if from BIOS you can directly boot Windows. Then change BIOS back to boot sdb or reinstall grub to sda to let you dual boot.

---

### Post by SBTlauien on 2013-06-24
The hard drive that Ubuntu and Windows 7 were installed on, was a brand new 1tb hard drive.

My hard drives and the OS on them...

1tb hard drive(New) - Ubuntu 12.04 + Windows 7

90gb hard drive(Original hard drive) - Windows XP

1.55gb hard drive(just recently took out of an old PC) - Windows 98

I guess I could try to unhook the two other hard drives and then update Grub.  I'll admit, I know little about this, and I don't know much about RAID.  From what I understand, RAID is set up in the BIOS(but where at?).

---

### Post by oldfred on 2013-06-24
You do not have matching drives which you would with RAID. Generally BIOS is set to AHCI, or LBA which is large block allocation. The IDE setting is for compatibility with very old systems. IDE was used back when drives were less than 8GB and we had to manually add CHS values. Your old drive and BIOS are not that old are they? Then I would not think new 1TB drive would be boot. Also AHCI may not work with XP. I changed BIOS from LBA to AHCI so my new SSD would work with trim, but XP would not boot. I had to change back in BIOS to boot XP and that was too much hassle and I really wanted SSD to be correct so I stopped booting XP - a good thing.

It may be old system had RAID so you can delete settings from your 74GB drive. Make sure it still is mounted as sdb.
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by SBTlauien on 2013-06-25
At one point, all of the OS worked and were displayed in GRUB.  But since getting rid of 13.04 and installing 12.04, I had to reinstall Grub, and that is causing it not to display all of the OS.

The OS all work, and were displayed in GRUB before I reinstalled Ubuntu.

---

### Post by SBTlauien on 2013-06-25
> **oldfred said:**
> Your old drive and BIOS are not that old are they?

The drive that is 1.55gb with Windows 98, is from a NEC from the mid-1990's.

The PC that it's in, was built in like 2004-2005.  The 74gb hard drive(with XP) is what was originally inside of it.

---

### Post by oldfred on 2013-06-25
They keep updating grub to see more configurations and then if something was not quite right it may now fail, where it may have worked. 
Did you try removing the old RAID settings on your drive?

---

### Post by SBTlauien on 2013-06-25
How do I remove the RAID setting from the drive?

In BIOS, the only place I can find the word "RAID", shows that it's all disabled.

---

### Post by oldfred on 2013-06-25
I posted in #28 the dmraid commands.

---

### Post by SBTlauien on 2013-06-25
I disconnected all hard drives except for my 1tb hard drive, turned on the PC, went into Ubuntu, ran "sudo update-grub" in the terminal, got no errors, rebooted, and Windows 7 doesn't appear...

I can see the files on the hard drive though.  I have register Windows yet though.

---

### Post by oldfred on 2013-06-25
Is your Windows still missing the two boot files. You had to move them from your other drive to get just the 1TB drive to work. See post #26.

---

### Post by SBTlauien on 2013-06-25
So is the Windows 7 boot on the 1.55gb hard drive?

---

### Post by oldfred on 2013-06-25
```
 sdc1: ______________________________

       File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files:        [COLOR=#ff0000]/bootmgr /boot/bcd[/COLOR] /IO.SYS /MSDOS.SYS /COMMAND.COM


```

---

### Post by SBTlauien on 2013-06-25
This is the error I get when trying to update Grub(with all the drives plugged in) and it's listed in the link...

ERROR: nvidia: wrong # of devices in RAID set "nvidia_bagbhdhc" [1/2] on /dev/sdb

Isn't that an error with my graphics card and RAID together?

---

### Post by oldfred on 2013-06-25
No you are using "fakeRAID" which often shows as nvidia driver. But not directly related to video or video modes.

 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by SBTlauien on 2013-06-26
I ran GParted from my Ubuntu Disk, and I don't see the NVIDIA/Raid at all, on any drive.

I just see my two partitions on my 1tb drive(ntfs and ext4) in which the ext4 is the only boot.

I see two areas on my 70gb hard drive(ntfs and unallocated) in which the ntfs is boot.

I see two areas on my 1.56 hard drive(fat32 and unallocated) in which fat32 is boot.

---

### Post by oldfred on 2013-06-26
Hard drives keep RAID meta-data on them even after a RAID set is broken. So any drive that was RAID has RAID meta-data. You have to remove the RAID meta-data. 
Gparted did not used to work with RAID, but very newest has many updates. But since not a full RAID configuration it may not see the meta-data?

Please run the commands I posted in #28, that will remove the RAID meta-data.

---

### Post by SBTlauien on 2013-06-26
Alright, deleted the raid data on sdc.

Now I can boot Windows XP.

I don't see an option in Grub for Windows 98.

Windows 7, shows up as "Windows 7 (loader)" and only takes me to a black screen with a blinking underscore.

---

### Post by oldfred on 2013-06-26
Windows 7 may need chkdsk or other repairs. Does it boot directly from BIOS using sda? Or try f8 to get to its repair console. From grub it usually is too quick to see the f8, and you have to do it from a Windows MBR boot. Otherwise you need the Windows 7 repairCD.

Try this.
sudo update-grub

But I do not know that the os-prober still looks for Windows 98? We may be able to manually add a boot stanza. But Windows usually combines boot files into one bootable system as that is the only way it multi-boots. So does 98 still have its boot files.
Run new BootInfo report.

---

### Post by SBTlauien on 2013-06-26
I think I might just want the while 1tb hard drive for Ubuntu, and the 70gb hard drive for Windows 7.

When I use GParted to change the hard drive partition, will I first need to format the ntfs partition to ext4, and then change the size, or can I just change it and not format?

---

### Post by oldfred on 2013-06-26
Not sure what partition you are taking about. 
Reformatting erases all data. 
Linux can read NTFS partitions, but cannot use NTFS for any system partitions. 

Windows does not even see Linux formatted partitions.

---

### Post by SBTlauien on 2013-06-26
Well, I have my 1tb hard drive split into two partitions, one for Windows, and one for Ubuntu.  The Windows partition is ntfs and has the Windows 7 installation on it, but I want to get rid of it and just use the whole drive for Ubuntu.

So, will I need to reformat that ntfs partition to do this?

---

### Post by oldfred on 2013-06-26
Are you going to have Windows anywhere? If so you can keep the NTFS partition as a data partition. But since NTFS needs chkdsk from Windows occasionally, you need Windows.  If not using Windows at all then use the entire drive for Linux. 

         For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by SBTlauien on 2013-06-27
For this 1tb hard drive, I ONLY want Ubuntu on it.

What's wrong with one giant section in / ?

I don't think I made any sections for Ubuntu, it's all in the same area(no /home and no swap).

---

### Post by oldfred on 2013-06-27
Drives used to be small.
Some BIOS or grub combinations have issues booting from files beyond 100GB on a drive. More prevalent with USB drives. So with those systems a separate /boot or the smaller / (root) with the rest of the drive as /home or what I use just data partition(s). For those systems all boot files must be inside the first 100GB. But we have only found it applies to some users.

I use 25GB for root but have several 25GB / partitions as I also install the next version to see if it works before deleting old version.

---

### Post by SBTlauien on 2013-06-27
Why does Grub show "Previous Linux versions" even though I formatted the drive since the last install(that didn't work - 13.04).  It has "Ubuntu, with Linux 3.5.0-23-generic" and the recovery mode.

The Ubuntu that works/current is 3.5.0-34-generic.

---

### Post by oldfred on 2013-06-27
As it does not delete old kernels when you download new ones, you may have a long list of kernels. I houseclean when it gets to 4 or more and only try to have current plus one older that I know works.

       In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by SBTlauien on 2013-06-27
So, as far as my 1tb drive and deleting the ntfs partition with Windows 7, should I just open with GParted from my live CD, and then drag the bar over so that the partition with Ubuntu takes up the whole drive, or should I format it first before dragging the bar to make it one partition?

---

### Post by oldfred on 2013-06-28
Are you reinstalling or not?

If not reinstalling, it will take a while as it has to move the Linux partition left. If you just reformat the NTFS you can mount it in your Linux install and use as a data partition.

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by SBTlauien on 2013-06-28
I'm not reinstalling.

I would like to keep the partition as a data partition.

Should I keep it as a NTFS, or should I format it to something else?

---

### Post by oldfred on 2013-06-28
Only if you have Windows somewhere should you keep it NTFS. NTFS is best for compatiblity with Windows, but needs chkdsk which you really can only run from Windows or a Windows repair CD or flash drive.
If only Linux on computer better to format as ext4, but you will have to set ownership & permissions and mount with fstab to make it easy to use.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

If not in fstab you can manually mount from terminal. Of course Nautilus may auto mount but it will have defaults and may not have correct ownership & permissions.


 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo fdisk -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown $USER:$USER /mnt/data

---

### Post by SBTlauien on 2013-07-02
Solved.

Thanks for the help.  I like Ubuntu so far.

---

