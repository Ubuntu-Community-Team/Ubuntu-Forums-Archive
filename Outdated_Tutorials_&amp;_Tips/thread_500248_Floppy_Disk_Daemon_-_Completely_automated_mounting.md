---
title: "Floppy Disk Daemon - Completely automated mounting/umounting of floppies."
date: 2007-07-13
forum: Outdated Tutorials &amp; Tips
---

### Post by psych787 on 2007-07-13
I've tried /etc/fstab, KDE's enable/disable mount point, and fdmount -d. All of these were unreliable at best, and fdmount -d only seemed to work when the sun was out.

To fix this, I wrote my own little script. It reads from /dev/fd0 every few seconds. If it gets output, then there's a floppy in there, and it automatically mounts the floppy disk. If it doesn't get any output, then the drive's empty, and it unmounts the floppy drive so it can be mounted again.
[B]
How to use the script:[/B]
First, I recommend you comment anything in /etc/fstab that might interfere. To do this type
```

gksu gedit /etc/fstab

```
in a terminal, and put a pound sign (#) in front of any lines with "fd" or "floppy" in them.

Second, I recommend you put this file in an autostart directory. In KDE this is "~/.kde/Autostart". To autostart in GNOME and other desktop environments, see [http://gentoo-wiki.com/HOWTO_Autostart_Programs#GNOME](http://gentoo-wiki.com/HOWTO_Autostart_Programs#GNOME)

Finally make sure you run this on the file when you're done:
```

chmod u+x floppy\ automount.sh

```

**The script:**
Paste this into your favorite text editor and save it as something like "floppy automount.sh".
```

#!/bin/bash
#===============================================================================
#
#          FILE:  floppy.sh
# 
#         USAGE:  ./floppy.sh 
# 
#   DESCRIPTION:  Automatically mounts floppy disks, superior to fdmount -d.
# 
#       OPTIONS:  ---
#	REQUIREMENTS:  fdutils,sleep,renice
#	BUGS:  Programs accessing /media/floppy0 without disk inserted dies.
#	NOTES:  fdmount must run root (or setuid)
#		/media/floppy0 must be accessable
#		Any floppy entries in fstab should be commented out.
#	AUTHOR:  psych787
#	COMPANY:  ---
#	VERSION:  1.0
#	CREATED:  07/03/2007 11:58:31 AM EDT
#	REVISION:  ---
#===============================================================================

renice 19 -p ${$} #This task requres very little CPU time to work perfectly.

while [ true ] ; do #We want an infinite-loop since this is a daemon.

sleep 3 #Cut down our CPU usage a little more, and reduce duty cycle.

floppy_dump=$(head -5 /dev/fd0)

if [ "$floppy_dump" ]
	then
fdmount fd0 /media/floppy0 #Disk exists, now mount it.
	else
#Kill programs owning the floppy disk (ex bash with pwd=/media/floppy0. Does NOT include konquror.
fuser /media/floppy0 -k 
fdumount #Disk does not exist, so unmount it.
fi

done

```
**DISCLAIMER!**
This script will cause your floppy drive to check for a disk every few seconds. I am NOT responsible if this causes your floppy drive to fail sooner as a result. I have used this script myself for a few days, but I make no guarantees. If you're feeling cautious, then increase the number of seconds for the program's sleep command (this will reduce usage of the floppy drive, at the cost of decreased response time).

EDIT: After several months, this script has not caused my floppy disk drive to fail. Of course, that doesn't gurantee that it won't or that you will be as fortunate.

EDIT2: My floppy drive is now flaky. I'm not sure its related to my use of this script, but given this fact, I must strongly recommend anyone using it to increase the sleep command's argument to at least 30.

---

