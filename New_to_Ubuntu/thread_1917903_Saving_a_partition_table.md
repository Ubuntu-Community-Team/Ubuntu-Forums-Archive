---
title: "Saving a partition table"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Resplendent Raven on 2012-01-30
I am currently running Parted Magic and backing up my hdd with Clonezilla, after i am done i will try to shrink my Vista partition as i explained [here]("http://ubuntuforums.org/showthread.php?t=1915302").

My question is, do i need to backup my current partition table somehow if i want to use the backup image later on?
And what do i need to do to restore a previous partition table?

---

### Post by oldfred on 2012-01-31
You can use sfdisk to backup partition table, but once you have changed it you have to be very careful on replacing it as that will revert to the old table which then is not correct.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt
Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)

You should use Vista's partitioning tools to shrink Vista's partition. NTFS partitions have internal data in the PBR - partition boot sector that has to have the correct size. Reboot Vista after the change a couple of times before doing anything else as it will want to run chkdsk (which I think does some of the update in the PBR).

Shrinking a Windows 7/Vista partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

If your Vista is up to date:
Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Resplendent Raven on 2012-01-31
Thanks for all that info oldfred, some of it will certainly come in handy.

My dvdrom drive is a little buggy though, but i think that when i download the iso on someone else's system it should be compatible with my Vista ? (i think i have sp1, not sure how i check that).

I think there might be also an option in CloneZilla to rebuild the partition table, so could i use that too?

I found something weird btw in my partition table 
> /dev/sda4       587770216   625137344    18683564+   5 
/dev/sda5       587770218   623482649    17856216   83
Or is this normal? perhaps i misunderstood the 63byte gap and this doesn't apply for between extended and logical partitions.

Btw would you think that as suggested in my linked thread, that backing up my recovery partition with Clonezilla should result in a working recovery partition backup ??

---

### Post by oldfred on 2012-01-31
The extended partition is just a container for all the logicals. So the rules are a bit different.

I have not used clonezilla, but have seen reports where it has worked well. But not sure about your specific case. I prefer just to backup /home and a few other things so a clean install can easily be reconfigured to my preference.

---

### Post by Resplendent Raven on 2012-01-31
Thanks again, guess i can mark this as solved ;)

---

