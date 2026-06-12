---
title: "how do I get Ubuntu and windows to share files?"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by SUperougi on 2012-01-18
I have a Acer, aspire-one, with intell atom processor, na450. There are two drives, C: which seems to contain all the files needed for operation and D: which holds the boot information; How do I get access to both out of the ubuntu side. Windows and ubuntu are dual booted. I need to be able to share a windows printer, and a few other thing that are in windows program to run from ubuntu.

---

### Post by Paqman on 2012-01-18
You should be able to access everything on your Windows partitions from within Ubuntu. Just open up the file manager and click on the Volumes shown on the left (if you installed Ubuntu using Wubi your Windows partition will instead be located at /host).

You can use your Windows printer, just go to the Printers tools and add a new printer. If it's a network printer set it up as a "Windows printer using Samba".

---

### Post by Mark Phelps on 2012-01-18
In terms of > windows program to run from ubuntu, if what you mean is running Windows apps inside Ubuntu, you need to visit the Wine subforum here and read up on that.  You can't run the apps by "sharing" them; instead, you have to install them anew inside Ubuntu -- and even then, only SOME Windows apps will run.  Visit the WineHQ website and look at their Application Compatibility Database to see the ratings for various apps.

In terms of sharing files, it's generally a BAD idea to write to directories and files in one OS partition from any other OS; thus sharing a partition to read files is OK, doing that to write files is not.

If you want to actually share data files, your better approach is to create a shared NTFS data partition.  Both Windows and Linux can read and write such filesystems.  But, do NOT share an OS partition -- doing so can lead to data corruption.

And finally, you should NOT be accessing your Windows boot loader files or the apps (Program Files) from inside Ubuntu.  You can't use those in Ubuntu, anyway, so there's no reason to be accessing them.

As to sharing a Windows printer, you can't install Windows printer drivers inside Ubuntu, so you will have to install the printer separately.

---

### Post by PantherVT on 2012-01-18
Is there anyway to prevent a file manager in Ubuntu from being able to read/write or even see files on the windows partition?

---

### Post by Paqman on 2012-01-19
Well, that partition isn't mounted by default. You could include an entry in /etc/fstab that mounts it, and control the permissions users are given on it. Very fine-grained control over that kind of thing is quite easy with Linux.

---

### Post by Double.J on 2012-01-19
+1 Whilst you can't completely remove all possible access to the partition (short of removing ntfs-3g - not recommended) adding the arguments

noauto
nouser

To the fstab entry will stop the device being automatically mounted at boot; you would have to manually mount it yourself, and then require root privileges to do so. This would leave you with the ability to access it when you want, but remove accidental access.

Edit:
Also I'm off my Ubuntu machine at the mo, but I suspect setting them to mount somewhere other than /media in the fstab will mean that they aren't visable in the nautilous sidebar, you'd have to navigate to the place you mounted them - I'd recommend either /mnt or making your own directory, for example /win7 to mount at :)

---

