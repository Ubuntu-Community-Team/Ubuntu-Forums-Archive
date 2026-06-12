---
title: "SimpleDrive Mounting Issues"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by logosinvictus on 2008-05-11
So... yeah. I know a similar thread has been posted before [here]("http://ubuntuforums.org/archive/index.php/t-599017.html"), but I'm getting a different message than that person did. When I go into Terminal and enter the command string:

mount -t ntfs-3g/dev/sdb1/media/simpledrive -o force

I get this:

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

Here is the entire error message I get when trying to mount the drive through Places:

*$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sdb1': Operation not supported Mount is denied becasue NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g/dev/sdb1/media/SimpleDrive -o force Or add the option to the relevant row in the /etc/fstab file: dev/sdb1/media/SimpleDrive ntfs-3g force 0 0*

Eh?

---

### Post by appoloin on 2008-05-11
I had this problem few days ago and what i did was i plugg in my external USB storage on my friends laptop using windows and unnount it. then when i plugg it back in my system with ubuntu it worked..

---

### Post by logosinvictus on 2008-05-11
*headdesk* Such a simple answer to such a complicated question... Thanks!!

---

### Post by Schlomy on 2011-08-02
Three years later, this solution still works. Awesome. Thanks!

---

