---
title: "where to put mount script on boot?"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by kidd4200 on 2012-11-15
where do i put a simple "mount /dev /media/location" script so it loads on boot?
reason im doing this is because i have ps3mediaserver daemon starting on boot. which, is useless without the external hard drive being mounted before the x system is started...

also, the name of the drive is "FreeAgent Drive". how do i tell the system theirs a space? %20? usually i just say /dev/Free*
help!
thanks!

---

### Post by dgharmon on 2012-11-16
> **kidd4200 said:**
> where do i put a simple "mount /dev /media/location" script so it loads on boot?
reason im doing this is because i have ps3mediaserver daemon starting on boot. which, is useless without the external hard drive being mounted before the x system is started...

also, the name of the drive is "FreeAgent Drive". how do i tell the system theirs a space? %20? usually i just say /dev/Free*
help!
thanks!

Put the mount command in /etc/rc.local, use backslash+space for "FreeAgent\ Drive" ..

---

### Post by newb85 on 2012-11-16
You could also add it using the Startup Applications GUI.

---

### Post by centaurusa on 2012-11-16
> **kidd4200 said:**
> i have ps3mediaserver daemon starting on boot. which, is useless without the external hard drive being mounted before the x system is started...


Another way to do this is to add an entry in the file system table (/etc/fstab) so that the drive is mounted automatically on bootup.  See: [http://linuxnorth.wordpress.com/2011/02/20/mounting-disks-automatically/ ]("http://linuxnorth.wordpress.com/2011/02/20/mounting-disks-automatically/")

Note that recent versions of Ubuntu seem to prefer (require?) using a UUID rather than the /dev/sdb1 construct in fstab.  So, you may have to modify the entry from the format noted in the link to something like:

UUID=ECE4BBC0E4BB8B7A    /media/Data_Disk ntfs users,defaults 0 0

---

