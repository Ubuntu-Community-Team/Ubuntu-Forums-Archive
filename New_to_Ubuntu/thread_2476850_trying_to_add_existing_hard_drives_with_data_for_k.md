---
title: "trying to add existing hard drives with data for kodi"
date: 2022-07-09
forum: New to Ubuntu
---

### Post by englandr753 on 2022-07-09
Ok, I'm green behind the ears with ubuntu.  I've set up windows 10 64bit on my system that I'm trying to use as a media server and will be dual booting with Kubuntu 20.4 with Kodi installed as the media host program.

Here are the following specs:
2990WX Threadripper
Gigabyte Aorus X399 Gaming 7 motherboard
64g Corsair memory (4x16g)
512g 950 evo m.2 boot drive (for Win 10 64bit)
2tb 970 Evo m.2 boot drive (for Kubuntu 20.4)
Asus 1080ti 11g video card
RM1000X Corsair power supply

I'm using two separate controller cards to add sata slots to be able to add additional NAS drives for larger storage for the music and movie collection and for future expansion.  I had trouble trying to get windows 10 to install with the add on cards installed so I unplugged them and all extra drives and the install went smooth from there.  Then I went to install Kubuntu on my Kingston 250g SSD but forgot that it was connected to the controller cards that I had removed so I chose to install on the 2tb already in my rig.

After getting windows and kubuntu installed the way I wanted I shut down and connected the controller cards and all of the hard drives.  When I boot into Kubuntu I see a LOT of string errors then it boots into Kubuntu just fine but when I try to update to get drivers for the controller cards manually I don't think anything is happening.  I go into Kodi and try to choose the hard drives to pull the music and movie info to load into Kodi and there are no drives visible.  Also, it doesn't see the drives that I plugged directly into the motherboard sata ports either.

I see instructions online on how to add and format a new drive but not much info on how to add an existing drive with data.  The drives I'm trying to add are formatted to NTFS and range in size from 4tb to 16tb.

Is it worth the time to try and plug these drives into the OS after the install or would I be better served to redo the kubuntu installation with the controllers and drives installed and let it try and pick them up and configure during the initial OS install?

Any help is appreciated!

---

### Post by oldfred on 2022-07-10
Windows fast boot issue?
That is the most common reason for your issues. 
Windows uses fast boot. That sets hibernation flag on all NTFS partitions. And when hibernation flag is set, the Linux NTFS driver will not normally mount the NTFS partition to prevent damage & loss of data. You often can force mount read only. 

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Are drives seen in UEFI/BIOS? If not, no system can use them.

Are mounting in fstab?
[https://ubuntuforums.org/showthread.php?t=2467566](https://ubuntuforums.org/showthread.php?t=2467566)
[https://ubuntuforums.org/showthread.php?t=2464668](https://ubuntuforums.org/showthread.php?t=2464668)


Kodi may need some special settings which I do not know about. Added that to your title, so those who know kodi can add info.

---

