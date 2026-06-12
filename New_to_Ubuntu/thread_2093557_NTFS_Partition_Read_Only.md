---
title: "NTFS Partition Read Only"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by nwkegan on 2012-12-11
Hello!

I've been googling for an hour, and I've also searched this site. I have a nasty virus on my windows partition, so I booted up my feisty fawn CD in an effort to remedy the issue.

I've installed avast and started scanning. Ooops! My windows partition is read-only.

I have ntsfprogs but I haven't found anything about modifying write access in its documentation.

ntfs-3g is not found by the apt-get command. I have no idea how to enable write access for this partition so that I can run the scan again and remove the virus.

Could anyone help me out? Thanks!

---

### Post by mastablasta on 2012-12-11
it would be better to use 12.04. fiesty is quite old and might not have all the necessary features.
 
otherwise:
[http://www.pendrivelinux.com/mounting-a-windows-xp-ntfs-partition-in-linux/](http://www.pendrivelinux.com/mounting-a-windows-xp-ntfs-partition-in-linux/)
 
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
 
root user will definatelly have access to it if normal live user doesn't.

---

### Post by NightsShadeQueen on 2012-12-11
I don't think this is an issue of permissions - I ran into this exact issue with my backup drive.

That said - I think the reason why you can't get ntfs-3g is because feisty is so out of date that it's no longer being supported by the repositories. So, yeah, a 12.04 boot drive would definitely work.

---

### Post by nwkegan on 2012-12-11
Yeah, I agree, it's quite outdated - the problem is that the computer I'm posting from lacks a CD drive, and the system that has a burner is out of commission. I really have no option here : /

I'll try out those links and report back. Thanks!

---

### Post by NightsShadeQueen on 2012-12-11
You might be able to boot from USB.

(To create a bootable USB - use Startup Disk Creator from Ubuntu, follow these directions from Windows: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) )

---

### Post by mastablasta on 2012-12-11
if it doesn't boot from USB but you have a floppy driver oyu can load boot manager on floppy (see plop boot manager) to be able to boot from USB dirve.
 
you could also try finding old repositories. i am not sure if thery can be still used for installing programmes, but they can be used for upgrades.
 
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
 
you could just change the repositories (sources) to point to old releases: 
[https://help.ubuntu.com/community/EOLUpgrades/Feisty](https://help.ubuntu.com/community/EOLUpgrades/Feisty)
 
then try to install the necessary file.

---

### Post by Mark Phelps on 2012-12-11
Since you can boot from CD, you should use another PC to go to the Kaspersky or Avira websites, download their free Antivirus Boot CDs, burn those to CD, and boot from those.  They can clean the Windows PC for you.

---

### Post by nwkegan on 2012-12-16
EDIT: Okay, so avast! gives me the error: The package doesn't provide a valid Installed-Size control field. See Debian Policy 5.6.20.

I'll look through the repository for something that's better supported, but does anyone have a suggestion for something with which I could scan my NTFS filesystem for viruses?

Ok, I'm gonna try ClamAV and report back.


Hey guys, thanks so much for the input.

Now that I have some more time, I've loaded up a USB drive with 12.10 and have it running. About to install avast! and see if I can get this handled once and for all. Will report back if I need further assistance.

I forget if this forum has rep, but if it does, you all are getting my java beans.

---

