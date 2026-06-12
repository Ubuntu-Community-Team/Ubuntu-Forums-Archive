---
title: "Trying to mount a drive"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by natebenn on 2008-10-10
Hey guys, newb here trying to figure out how to mount an NTFS drive that I used for storage in XP. I am having an issue that the drive wasn't shut down "cleanly" so I am unable to mount it. Here is some fdisk -l results and the issue I'm running into.

"nate@Nate-desktop:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04594009

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7fe97fe9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sdb2            1913        8720    54685260   83  Linux
/dev/sdb3            8721        9352     5076540   83  Linux
/dev/sdb4            9353        9729     3028252+  82  Linux swap / Solaris
nate@Nate-desktop:~$ sudo mount /dev/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/Mr. Storage -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/Mr. Storage ntfs-3g force 0 0
nate@Nate-desktop:~$ "

Is it safe to use choice 2 or do I risk data loss/corruption?

---

### Post by Victormd on 2008-10-10
You can use the "force mount" switch when giving the mount command.
```
sudo mount -t ntfs /dev/sdb1 /media/<drive label> -o force
```

I've had to do it only a couple of times, but didn't have any problems...

---

### Post by natebenn on 2008-10-10
is that safe?

---

### Post by Victormd on 2008-10-10
> **natebenn said:**
> is that safe?

The times I've had to use it, I didn't run into any problems and I don't know anyone who has had any problems either... so I'd say yes, it's safe.

---

### Post by Enternald on 2008-10-10
It should be:
sudo mount -t ntfs-3g /dev/sdb1 /media/<drive label> -o force

---

### Post by natebenn on 2008-10-10
crossing my fingers and giving it a shot then. :) Thanks guys.

---

### Post by Victormd on 2008-10-10
> **Enternald said:**
> It should be:
sudo mount -t ntfs-3g /dev/sdb1 /media/<drive label> -o force

Hardy isn't limited to the ntfs-3g specification anymore, you can use both ntfs-3g and ntfs. On earlier versions of ubuntu you had to install and use ntfs-3g.

---

### Post by natebenn on 2008-10-10
yeah, I'm on hardy 8.04. The drive was working previously but then I reworked my partions on my OS drive and ever since haven't been able to mount this storage drive.

---

### Post by Victormd on 2008-10-10
> **natebenn said:**
> crossing my fingers and giving it a shot then. :) Thanks guys.

Don't worry, you'll be fine! :)

---

### Post by natebenn on 2008-10-10
Not sure what's going on here.

nate@Nate-desktop:~$ sudo mount -t ntfs /dev/sdb1 /media/Mr. Storage -o force
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
nate@Nate-desktop:~$

---

### Post by Victormd on 2008-10-10
> **natebenn said:**
> Not sure what's going on here.

nate@Nate-desktop:~$ sudo mount -t ntfs /dev/sdb1 /media/Mr. Storage -o force

I would avoid the space in the drive name. Instead of using Mr. Storage, try just storage or mrstorage (keep in mind that everything in ubuntu is case sensitive, i.e., Storage is different from storage - not the case in Windows). Also, create the directory under media:
```
sudo mkdir /media/storage
```
Then
```
sudo mount -t ntfs /dev/sdb1 /media/storage -o force
```

---

### Post by natebenn on 2008-10-10
hmmmm...

nate@Nate-desktop:~$ sudo mkdir /media/storage
nate@Nate-desktop:~$ sudo mount -t ntfs /dev/sdb1 /media/storage -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
nate@Nate-desktop:~$

By the way I greatly appreciate your help at this late hour. :) :)

---

### Post by Victormd on 2008-10-10
Looks like it worked... :)
Now if you restart, you shouldn't have problems with it anymore...

---

### Post by natebenn on 2008-10-10
do I have to restart or anything??

I am still getting the same error that it cannot mount.

---

### Post by Victormd on 2008-10-10
> **natebenn said:**
> do I have to restart or anything??

I am still getting the same error that it cannot mount.


You can if you want, just to be on the safe side... :)

If restarting doesn't do the trick, check [this thread]("http://ubuntuforums.org/showthread.php?p=5891205#post5891205").

---

### Post by natebenn on 2008-10-10
k brb then

---

### Post by Victormd on 2008-10-10
Sorry I can't stick around to see if it worked, gotta get up early tomorrow. Post back though with your progress.
Hopefully it did. Otherwise, check the link I posted earlier.

---

### Post by natebenn on 2008-10-10
well no luck but I will do some reading on that thread and see if I can decifer the language. :) I appreciate the help. Many thanks.

---

### Post by ubunny on 2008-10-10
I'm going to guess there's no /media/Mr.Storage directory?  If not make your directory first; ie: sudo mkdir /media/mrstorage  (or whatever name you want, as long as it is in the /media directory), then repeat your mount command as before (with the correct /media/nameyoumade).  The mount command needs a place to refer the drive in /dev to another that exists.

---

### Post by natebenn on 2008-10-10
Victor is the man!! :) Got it working thanks to you. Can't thank you enough for you help!!

---

### Post by kansasnoob on 2008-10-10
I may have missed something, but if this an external usb drive install pmount either from synaptic or:

```
sudo apt-get install pmount
```

If it's either internal or external I prefer using ntfsprogs - but it does provide capability to damage things if you're not paying attention. That is that it will allow you to access even program files in Win!

Another option is ntfs-config. Both are available in synaptic.

---

### Post by Victormd on 2008-10-10
> **natebenn said:**
> Victor is the man!! :) Got it working thanks to you. Can't thank you enough for you help!!

Glad I could help! :)

---

