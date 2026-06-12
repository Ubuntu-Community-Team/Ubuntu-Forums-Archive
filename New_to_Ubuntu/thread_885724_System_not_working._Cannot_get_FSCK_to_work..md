---
title: "System not working. Cannot get FSCK to work."
date: 2008-08-10
forum: New to Ubuntu
---

### Post by penguinbreath on 2008-08-10
I was doing a backup of a computer in my home that was having some problems. It looked like I had enough free space in my primary computer to copy the entire hard drive, so I tried to copy the entire hard drive to a folder in my primary computer through my network. I left the computer for a few hours.
   For some reason, I completely ran out of space. Realizing this, I deleted the folder and emptied the trash.

I rebooted my primary computer and I can only get to the log-in screen. If I try to log in, I get a black screen and it returns me to the log-in screen.

I am able to get to the command line, but I cannot seem to run FSCK. and I also keep getting errors saying something about python missing.

I think I really messed up something...... Any ideas on what I can do?

---

### Post by RealPSL on 2008-08-10
I think the python error you are getting might be key to solving the problem. Can you provide the text of the error message(s)?

What trouble are you having when you attempt to run fsck? Keep in mind that you should never run fsck on a mounted file system.

---

### Post by Paqman on 2008-08-10
> **RealPSL said:**
> Keep in mind that you should never run fsck on a mounted file system.

+1

To be safe, do it from a LiveCD.

---

### Post by penguinbreath on 2008-08-10
I tried starting my computer without the Live CD and I got error 17 when the GRUB was loading.

I do not know how to access (if possible) my hard drive through the live cd to do some backups before trying anything. Any ideas?

After I get the backups made (if I can) what should I do? :confused:

---

### Post by penguinbreath on 2008-08-10
I cannot find my hard drive from the live CD (Kubuntu 8.04) 

Tried fdisk -l from the LiveCD:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6951

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aa54a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081   8e  Linux LVM

```

The 80-gigabyte is my primary drive. The 40gb is not being used.

I tried mounting the hard drive but I get this:
```
mount: can't find /dev/sda1 in /etc/fstab or /etc/mta
```

I cannot seem to find or access my hard drive to make backups. Am I doing something wrong? :confused:

---

### Post by RealPSL on 2008-08-10
When you run your mount command you should specify both the device and the mount point. As when booted from the liveCD those will not exist in /etc/fstab e.g.
```
-o ro
mkdir /tmp/root
sudo mount -t ext3 -o ro /dev/sda1 /tmp/root

```

This should mount your ext3 file system read-only. This will allow you to take your backups. Remember to unmount it before running the fsck.

Once the fsck is done the next things we should do is fix the master boot record by [reinstalling grub]("http://http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by penguinbreath on 2008-08-10
> When you run your mount command you should specify both the device and the mount point. As when booted from the liveCD those will not exist in /etc/fstab e.g.
Code:

-o ro
mkdir /tmp/root
sudo mount -t ext3 -o ro /dev/sda1 /tmp/root

This should mount your ext3 file system read-only. This will allow you to take your backups. Remember to unmount it before running the fsck.

Once the fsck is done the next things we should do is fix the master boot record by reinstalling grub. 


```

ubuntu@ubuntu:~$ mkdir /tmp/root

ubuntu@ubuntu:~$ sudo mount -t ext3 -o ro /dev/sda1 /tmp/root
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by y@w on 2008-08-10
Are you sure it's ext3? Don't specify the type and see if the system mounts it.

---

### Post by penguinbreath on 2008-08-11
> **y@w said:**
> Are you sure it's ext3? Don't specify the type and see if the system mounts it.

It gave me a help-page output
```
ubuntu@ubuntu:~$ sudo mount -t /dev/sda1 /tmp/root
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
ubuntu@ubuntu:~$    
```

I also tried running fsck -n to see what was wrong with my filesystem (but not letting it fix anything until I make backups)
This is my output:
```
ubuntu@ubuntu:~$ sudo fsck -n
fsck 1.40.8 (13-Mar-2008)
```


Is there anything else I can try?

---

### Post by y@w on 2008-08-11
In your mount command you'll have to drop off the -t. When you use the -t flag, it's expecting you to specify the type. Do you remember changing the fielsystem type when you originally did the install? The default is ext3, but it can be changed. I'm just throwing out possibilities on why it's not mounting.

---

### Post by penguinbreath on 2008-08-11
> **y@w said:**
> In your mount command you'll have to drop off the -t. When you use the -t flag, it's expecting you to specify the type. Do you remember changing the fielsystem type when you originally did the install? The default is ext3, but it can be changed. I'm just throwing out possibilities on why it's not mounting.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /tmp/root
mount: you must specify the filesystem type

```

I never remember changing my filesystem type. I believe I just used the use-entire-disk option when I installed.

Edit:

I should mention the hard-drive I copied was from a Mac that was not working properly. If it was (somehow?) carrying a virus, is it possible I caught it and it infected/destroyed my system? I personally highly doubt it, but I do not know much about *ubuntu (and macs).

---

### Post by y@w on 2008-08-11
Uh, I've never had to specify the filesystem.. '-t' is listed as optional in the manpage for mount. Anyway, if you went with the default, it's ext3. You're right, there's not really any sort of malware that would be trasnferring like that.. 

You said you tried to fsck the disk right away.. Did you try to do that while it was mounted? Did it ever start running?

---

### Post by penguinbreath on 2008-08-11
> Uh, I've never had to specify the file system.. '-t' is listed as optional in the manpage for mount. Anyway, if you went with the default, it's ext3. You're right, there's not really any sort of malware that would be transferring like that..

You said you tried to fsck the disk right away.. Did you try to do that while it was mounted? Did it ever start running? 

I typed fsck in recovery mode before I came here for help. I do not know if it actually ran ( I think I got an error). Then I rebooted and posted this thread from the LiveCD. After posting the thread I rebooted without the LiveCD to get some more information on the errors, but I could not get back into my system as before because I got the GRUB error.

During this current live session I typed ```
sudo fsck -n
``` to scan for problems without fixing anything. I did not get any output except the version information of FSCK.

I first just want to get some data off of my hard drive before attempting to fix anything.

---

### Post by penguinbreath on 2008-08-12
I am thinking of just re-installing Kubuntu instead of attempting to fix it. 

However I still cannot figure out how to access my hard-drive to make some backups. Is it still possible to retrieve data from my disk or is it too damaged to be mounted?  :confused:

---

### Post by penguinbreath on 2008-08-12
I ran fdisk and got this. Is this output normal?




```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 9729.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):    

```

List:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e6951

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aa54a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4865    39078081   8e  Linux LVM
ubuntu@ubuntu:~$
                     
```

I plan to re-install the OS soon, however I first wish to know if I can salvage any of my files before doing so. 

Any advice on what to do next would be highly appreciated :)

---

### Post by y@w on 2008-08-12
No, that error message is fine. It's just telling you that you need to make sure the boot loader is in the MBR or in a partition at the beginning of the disk since you have a "large" disk. I get the same message when I run fdisk on all my machines as well.

Is your data that you wish to recover on the same partition as you would put your / partition? If not, go ahead and reload the OS and you can deal with the recovery stuff once it's done. 

Here's a good place to start with data recovery on a failed partition or drive: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by penguinbreath on 2008-08-13
> **y@w said:**
> No, that error message is fine. It's just telling you that you need to make sure the boot loader is in the MBR or in a partition at the beginning of the disk since you have a "large" disk. I get the same message when I run fdisk on all my machines as well.

Is your data that you wish to recover on the same partition as you would put your / partition? If not, go ahead and reload the OS and you can deal with the recovery stuff once it's done. 

Here's a good place to start with data recovery on a failed partition or drive: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I was able to pull some of my pictures off the hard-drive with recoverjpeg. I got Kubuntu re-installed and it seems to be working well.

Thanks for the help everyone!

---

