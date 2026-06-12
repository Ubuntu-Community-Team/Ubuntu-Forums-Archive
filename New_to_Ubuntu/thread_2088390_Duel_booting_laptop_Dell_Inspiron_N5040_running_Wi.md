---
title: "Duel booting laptop Dell Inspiron N5040 running Windows 7."
date: 2012-11-26
forum: New to Ubuntu
---

### Post by docmech on 2012-11-26
Hey folks, I'm thinking of duel booting my laptop, which of course only has one hard drive, that is running windows 7. Should I have any concerns? Will both systems perform at there best or will it cause issues? Thanks for any info :)

---

### Post by 2F4U on 2012-11-26
The first thing to make sure is that you don't already have 4 primary partitions on the hard disk. This effectively would prevent you from installing Ubuntu. Preinstalled machines often come with 4 primary partitions out of the box.
Next thing you definitely should do is run the liveCD of the variant you intend to install. See if everything works as expected.

---

### Post by oldfred on 2012-11-26
Welcome to the forums.

+1 on 2F4U suggestions. 

Almost all Windows 7 systems use MBR and have used all 4 primary partitions. So some adjustment is required. But only use Windows tools to shrink the Windows partition, but not to create new partitions as it will convert to dynamic partitions. Dynamic partitions are Windows proprietary and do not work with LInux.

Before starting:
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

    
Download the 64bit version and install to CD or USB using directions on Ubuntu site. Desktop install version is also liveCD/USB that you can use to test system to see if everything works.

       Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by LuciferRex on 2012-11-26
> **oldfred said:**
> Welcome to the forums.

+1 on 2F4U suggestions. 

Almost all Windows 7 systems use MBR and have used all 4 primary partitions. So some adjustment is required. But only use Windows tools to shrink the Windows partition, but not to create new partitions as it will convert to dynamic partitions. Dynamic partitions are Windows proprietary and do not work with LInux.
.....

Can't he install 'Alongside' windows?

---

### Post by Mark Phelps on 2012-11-26
> **LuciferRex said:**
> Can't he install 'Alongside' windows?

NOT if he already has 4 partitions because this would require creating at least one more partition -- which is not permitted.

---

### Post by docmech on 2012-11-26
> **2F4U said:**
> The first thing to make sure is that you don't already have 4 primary partitions on the hard disk. This effectively would prevent you from installing Ubuntu. Preinstalled machines often come with 4 primary partitions out of the box.
Next thing you definitely should do is run the liveCD of the variant you intend to install. See if everything works as expected.

Thankx That's the first things I will investigate before preceeding

---

### Post by docmech on 2012-11-27
> **oldfred said:**
> Welcome to the forums.

+1 on 2F4U suggestions. 

Almost all Windows 7 systems use MBR and have used all 4 primary partitions. So some adjustment is required. But only use Windows tools to shrink the Windows partition, but not to create new partitions as it will convert to dynamic partitions. Dynamic partitions are Windows proprietary and do not work with LInux.

Before starting:
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

    
Download the 64bit version and install to CD or USB using directions on Ubuntu site. Desktop install version is also liveCD/USB that you can use to test system to see if everything works.

       Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)


So shrinking the partitions will combined the partitions from 4  partitions to 3 or 2? If not how could I create another partition if I  would still be maxed out with 4? Just a side note: I have PLENTY of hard  drive space as the laptop is fairly new.  Thanks for reply

---

### Post by oldfred on 2012-11-27
While some of these threads discuss HP, the 4 partition configuration seems to be the same for all vendors Windows 7 installs.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

       Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

    If you want to create partitions in advance for to see how Ubuntu installer works as it is similar.
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
    [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 

    Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by docmech on 2012-11-27
Hey my dell's hard drive only has 3 partitions used.
1. OEM 100mb
2, Recovery 14.65 gbs ntfs
3. Os (C): 451 gbs ntfs 

So does that means I got one partition to use as I want?? 
Should I still shrink Os (c) or would I even need to as the Ubuntu installer will make space for me?

---

### Post by oldfred on 2012-11-27
Always best to shrink Windows with the Windows MMC and reboot Windows a couple of times to make sure it has updated itself with its new size. 

Installer usually works but some have had issues on the shrink of Windows as Windows will still want to do the chkdsk an sometimes that just does not work correctly.

---

