---
title: "checking for bad sectors"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by chris_wiley on 2013-08-04
Hi all first post I run **lUbuntu 13.04**


I know there is a command to run a scan for bad sectors but I'm new to the command line. Is there a program with a GUI? or something  I can download in the packet manager? Thanks much.

I'm also wondering how to change the time from military to standard thanks.

---

### Post by arpanaut on 2013-08-04
Click on the top icon on the side panel, type in disks, select that icon, on the top right of that prog. is a cog wheel select that and go to smart data and that will give you the info you seek

system settings > Time & Date icon > select Clock and change settings.

System settings is in your side panel or under the cog at top right of desktop screen.

HTH

---

### Post by chris_wiley on 2013-08-04
> **arpanaut said:**
> Click on the top icon on the side panel, type in disks, select that icon, on the top right of that prog. is a cog wheel select that and go to smart data and that will give you the info you seek

system settings > Time & Date icon > select Clock and change settings.

System settings is in your side panel or under the cog at top right of desktop screen.

HTH

thanks but Im running lubunte there is only a option for checking smart not bad sectors.

when I go home I wil try to grab a sceen shot

---

### Post by chris_wiley on 2013-08-04
here is some sceen shots I found Im not sure if this will help or not

---

### Post by arpanaut on 2013-08-04
Under attributes the reallocated sector count would be your bad sectors?  No?

---

### Post by chris_wiley on 2013-08-04
it shows the number of bad sectors marked but no way to scan for more. There is a commanded I tried but it told me the drive was mounted. As It was my only drive I could not unmount it.  I guess I could boot to a live distro and run the command that way. I use lubunte on  computers I give away and it would be nice to show people how to run a scan. I don't think they're going to want to learn how to boot off a live distro and check for bad sectors.

---

### Post by jim Kane on 2013-08-04
Run a live CD of Ubuntu 9:10 and run Disk Utility 
Later versions may have this app but i keep a cd of 9:10 for just that reason.

---

### Post by ricardoeureka on 2013-08-04
The linux command line for checking bad sectors is fsck, BUT please be aware of: 1) you have to run it as root (or sudo) 2) you need to have the filesystem to be checked unmounted in order to make it possible. Therefore, you should reboot your system from a live CD /USB and the run from there. Again BE CAREFULL, and be aware to have a complete fresh backup.  Question: Why do you need to check for bad sectors?

---

