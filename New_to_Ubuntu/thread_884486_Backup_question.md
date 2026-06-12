---
title: "Backup question"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Drezard on 2008-08-09
Hello,

I used this guide directly after installation ([http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)) to make a backup of my harddrive with ubuntu on it. Now.... I have been playing round with ubuntu and stuffing round with it alot so... i wana wipe everything so i have a clean install again....

Do i delete EVERYTHING except /proc, /lost+found, /mnt, /sys and the backup file ofcourse, then try and unzip the file... or wouldnt this work?

if this is the case, whats the easiest way to do what i wana do?

Daniel

---

### Post by HermanAB on 2008-08-09
Well, first you should boot off a CDROM, not the hard disk.

Then simply copy the backup tar ball to the root / directory and untar it with: tar -zxvf backupfile

That will overwrite everything and when you reboot the system should be back to normal.  You don't really need to delete anything beforehand.

Then, once you have everything working again, install Vmware or Virtualbox and experiment in a virtual machine - don't screw up your base system again.

Hope that helps!

Herman

---

