---
title: "[SOLVED] Unclean NTFS volume"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by PoopyTheJ on 2008-09-26
I have an ntfs volume which shows unclean and ubuntu wants me to reboot in windows (which I don;t have a machine to do so on) and reshutdown properly. I have an option to force the mounting that shows this command to use or something similiar "sudo mount -t ntfs-3g /dev/sdd1/media/disk-0 force". Seems pretty straightforward to me however my problem is this, how do I know what the device is or should be mounted as? For instance when I try that command in a terminal I get "Failed to access '/dev/sdd1/media/disk-0': Not a directory". What should the mount point be? Obviously not sdd1, I have two other hard disks on this machine each with 2 partitions on it. This volume is a completely stand alone old volume with 1 partition on it connected via IDE. Any help would be appreciated!

---

### Post by Catalyst2Death on 2008-09-26
I think it should be:

```
sudo mkdir /media/disk-0
sudo mount -t ntfs-3g /dev/sdd1 /media/disk-0 force
```

you may or may not have to do the mkdir command, try it without first and then do it if you get an error...

---

### Post by PoopyTheJ on 2008-09-26
When I try that command I get this...

sudo mount -t ntfs-3g /dev/sdd1 /media/disk-0 force
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


Something must be wrong with the syntax of the command but I'm lost...

---

### Post by prshah on 2008-09-26
> **PoopyTheJ said:**
> 
sudo mount -t ntfs-3g /dev/sdd1 /media/disk-0 force


That -0 is -o (for orange). The correct command is ```

sudo mount -t ntfs /dev/sdd1 /media/disk -o force,defaults,gid=46,umask=007
```

(Note the space between "disk" and "-o" (for orange).

To find out your correct device id for ntfs partition, give the following command in a terminal (Applications-Accessories-Terminal) ```
sudo fdisk -l | grep -i ntfs
```

---

### Post by PoopyTheJ on 2008-09-26
Thank you that got her mounted.

---

