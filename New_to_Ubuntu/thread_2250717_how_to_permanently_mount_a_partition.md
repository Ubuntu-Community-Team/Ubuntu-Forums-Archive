---
title: "how to permanently mount a partition"
date: 2014-10-30
forum: New to Ubuntu
---

### Post by czgirb on 2014-10-30
i have a ext4 partition, which not recognized (not mounted) by ubuntu. how to make it to be permanently mounted partition?
PS:
i've check the partition with gparted, but the mount option is greyed.
please help me ...

---

### Post by nerdtron on 2014-10-30
> i have a ext4 partition, which not recognized (not mounted) by ubuntu

You said not recognized means not mounted? But does the partition still shows on the left pane of Nautilus?
Before we do automatic mounting, can you manually mount the drive?

---

### Post by oldfred on 2014-10-30
To manually mount and set ownership & permissions:

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by czgirb on 2014-10-31
> **nerdtron said:**
>  You said not recognized means not mounted? 
SORRY ... I'm not sure
Maybe **YES** ... cos by select **place > computer >** select the drive - **right click** - **Mount** ... it was [B]Mounted
[/B]
> **nerdtron said:**
>  But  does the partition still shows on the left pane of Nautilus? 
YES! this is another way, open **Nautilus** > select partition - **right click** - **Mount **... it was **Mounted**
the last way is ... in **Nautilus**, directly **double-click** the partition, and what is inside the partition will show-up in right window

---

### Post by oldfred on 2014-10-31
If you want to permanent & automatically mount it, you have to create an entry in fstab. Then everytime you reboot it will be mounted.
You still have to create a mount point. If in /media it will be shown in Nautilus. Or you can mount in /mnt, but it will not be in Nautilus. I then use links to link each folder in the partition into /home.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

Specific commands & example fstab entry:

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by Alireza_Zamani on 2014-10-31
in Command Prompt type this commands and Copy/Paste output here :

> $ fdisk -l
$ mount -l

---

### Post by czgirb on 2014-11-02
> **Alireza_Zamani said:**
> in Command Prompt type this commands and Copy/Paste output here :

as requested:
```
                         [SIZE=2]czgirb@ubuntu:~$ sudo fdisk -l [/SIZE]
 [SIZE=2][sudo] password for czgirb:  [/SIZE]
 
 [SIZE=2]Disk /dev/sda: 250.1 GB, 250059350016 bytes [/SIZE]
 [SIZE=2]255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors [/SIZE]
 [SIZE=2]Units = sectors of 1 * 512 = 512 bytes [/SIZE]
 [SIZE=2]Sector size (logical/physical): 512 bytes / 512 bytes [/SIZE]
 [SIZE=2]I/O size (minimum/optimal): 512 bytes / 512 bytes [/SIZE]
 [SIZE=2]Disk identifier: 0xe05e4f1e [/SIZE]
 
    [SIZE=2]Device Boot      Start         End      Blocks   Id  System [/SIZE]
 [SIZE=2]/dev/sda1   *        2048    39063551    19530752   83  Linux [/SIZE]
 [SIZE=2]/dev/sda2       463673344   488390655    12358656    7  HPFS/NTFS/exFAT [/SIZE]
 [SIZE=2]/dev/sda3        39063552    58595327     9765888   82  Linux swap / Solaris [/SIZE]
 [SIZE=2]/dev/sda4        58595328   463671295   202537984   83  Linux [/SIZE]
 
 [SIZE=2]Partition table entries are not in disk order [/SIZE]
 
 [SIZE=2]Disk /dev/sdb: 500.1 GB, 500107862016 bytes [/SIZE]
 [SIZE=2]1 heads, 63 sectors/track, 15504336 cylinders, total 976773168 sectors [/SIZE]
 [SIZE=2]Units = sectors of 1 * 512 = 512 bytes [/SIZE]
 [SIZE=2]Sector size (logical/physical): 512 bytes / 512 bytes [/SIZE]
 [SIZE=2]I/O size (minimum/optimal): 512 bytes / 512 bytes [/SIZE]
 [SIZE=2]Disk identifier: 0x01bcefcf [/SIZE]
 
    [SIZE=2]Device Boot      Start         End      Blocks   Id  System [/SIZE]
 [SIZE=2]/dev/sdb1              63   976768127   488384032+  83  Linux [/SIZE]
 [SIZE=2]czgirb@ubuntu:~$ sudo mount -l [/SIZE]
 [SIZE=2]/dev/sda1 on / type ext4 (rw,errors=remount-ro) [/SIZE]
 [SIZE=2]proc on /proc type proc (rw,noexec,nosuid,nodev) [/SIZE]
 [SIZE=2]sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) [/SIZE]
 [SIZE=2]none on /sys/fs/cgroup type tmpfs (rw) [/SIZE]
 [SIZE=2]none on /sys/fs/fuse/connections type fusectl (rw) [/SIZE]
 [SIZE=2]none on /sys/kernel/debug type debugfs (rw) [/SIZE]
 [SIZE=2]none on /sys/kernel/security type securityfs (rw) [/SIZE]
 [SIZE=2]udev on /dev type devtmpfs (rw,mode=0755) [/SIZE]
 [SIZE=2]devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) [/SIZE]
 [SIZE=2]tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) [/SIZE]
 [SIZE=2]none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) [/SIZE]
 [SIZE=2]none on /run/shm type tmpfs (rw,nosuid,nodev) [/SIZE]
 [SIZE=2]none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) [/SIZE]
 [SIZE=2]none on /sys/fs/pstore type pstore (rw) [/SIZE]
 [SIZE=2]binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) [/SIZE]
 [SIZE=2]systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd) [/SIZE]
 [SIZE=2]gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=czgirb) [/SIZE]
 [SIZE=2]/dev/sdb1 on /media/czgirb/500GB type ext4 (rw,nosuid,nodev,uhelper=udisks2) [500GB] [/SIZE]
 [SIZE=2]czgirb@ubuntu:~$  [/SIZE]
 
```

---

### Post by nerdtron on 2014-11-02
If /dev/sdb1 does not changes (if this is an internal drive), you can just add the following line on your /etc/fstab file.
```
 /dev/sdb1     /media/czgirb/500GB    ext4      defaults        0       0
```

---

### Post by czgirb on 2014-11-02
> **nerdtron said:**
> If /dev/sdb1 does not changes (if this is an internal drive), you can just add the following line on your /etc/fstab file.
```
 /dev/sdb1     /media/czgirb/500GB    ext4      defaults        0       0
```

SORRY ... for I don't know what when wrong
my problem is the **sda4**, which labelled **207GB**
and not the external, **sdb1**, which labelled [B]500GB

[/B]the output of** /etc/fstab** is as follow:```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=70dc4012-60a0-4aa1-bb8a-675c424fe551 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=482233f6-6ff9-4dbb-97c0-8efcf693c4e9 none            swap    sw              0       0
```

---

### Post by yancek on 2014-11-02
You didn't indicate which partition you wanted mounted until your last post so the earlier suggestion was just an example.  If it is sda4 you want do this in fstab:

> /dev/sda4     /media/czgirb/207GB    ext4      defaults        0       0

You would have to have created the directory named 207GB under /media/czgirb for this to work or rename 207GB to whatever you want.  You could use the blkid command to find the UUID of sda4 and replace the /dev/sda4 part with it in the same manner as your other partitions.

---

### Post by sisco311 on 2014-11-02
In the fstab file, you should use the UUID of the partition instead of its current device name /dev/sda4. Device names are assigned during the boot process in a nondeterministic way. Which means that they can change after a reboot. See: [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by bab1 on 2014-11-02
> **yancek said:**
> You could use the blkid command to find the UUID of sda4 and replace the /dev/sda4 part with it in the same manner as your other partitions.

+1 to @sisco311

---

### Post by czgirb on 2014-11-04
> **sisco311 said:**
> In the fstab file, you should use the UUID of the partition instead of its current device name /dev/sda4. Device names are assigned during the boot process in a nondeterministic way. Which means that they can change after a reboot. See: [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

OK ... this is the output:
```
czgirb@ubuntu:~$ sudo blkid
/dev/sda1: UUID="70dc4012-60a0-4aa1-bb8a-675c424fe551" TYPE="ext4" 
/dev/sda2: LABEL="RECOVERY" UUID="D2BE3BDFBE3BBAB5" TYPE="ntfs" 
/dev/sda3: UUID="482233f6-6ff9-4dbb-97c0-8efcf693c4e9" TYPE="swap" 
/dev/sda4: LABEL="207GB" UUID="8580d3f9-05cf-4b89-b766-12c0e6f43e91" TYPE="ext4" 
/dev/sdb1: LABEL="500GB" UUID="55f0ac78-a4cd-45f6-8c85-7d076012b58c" TYPE="ext4" 
czgirb@ubuntu:~$ 

```
Since I'm a newbie, please guide what i should do
Thank you

---

### Post by czgirb on 2014-11-04
or am I should replace this part:
> 
UUID=70dc4012-60a0-4aa1-bb8a-675c424fe551 /               ext4    errors=remount-ro 0       1
with this part:
> UUID="8580d3f9-05cf-4b89-b766-12c0e6f43e91 /media/czgirb/207GB ext4 defaults 0 0 
if YES, OK i will do it ... and then ...
please guide me ...

---

### Post by oldfred on 2014-11-04
Yes, but you have an extra " in your example, otherwise it should work.

After editing fstab, run this to confirm it works. Make sure you have unmounted it first as it will remount using fstab which will not work if mounted.

       # remount from updated fstab
sudo mount -a

If you have already set ownership & permissions then it should work.

---

### Post by czgirb on 2014-11-04
> **oldfred said:**
> Yes, but you have an extra " in your example, otherwise it should work.

After editing fstab, run this to confirm it works. Make sure you have unmounted it first as it will remount using fstab which will not work if mounted.

       # remount from updated fstab
sudo mount -a

If you have already set ownership & permissions then it should work.

OMG! Can you make it step-by-step? I don't get any
please ...

---

### Post by yancek on 2014-11-04
> UUID="8580d3f9-05cf-4b89-b766-12c0e6f43e91 /media/czgirb/207GB ext4 defaults 0 0 			 		

What oldfred is telling you is that in the example you posted above, you have double quotes (") right after UUID=, remove it so it looks like this:

> UUID=8580d3f9-05cf-4b89-b766-12c0e6f43e91 /media/czgirb/207GB ext4 defaults 0 0 

You do have a directory named 207GB under /media/czgirb, right?  Just reboot to test it if you don't understand the other commands.

---

### Post by monkeybrain20122 on 2014-11-05
Easy gui way: search for disks in the dash and bring up the disk utility (assume you are using Ubuntu or Ubuntu gnome) Locate the partition you want to auto mount, click on it, then click the gear icon on lower left corner of the partition table (not the upper right one) Choose Edit Mount Options (screenshot 1), then turn OFF  "Automatic Mount Options" and make sure the box 'mount at startup' is checked (screenshot 2). 

That's it. Next time when you reboot the partition will be mounted.

---

### Post by sisco311 on 2014-11-06
> **monkeybrain20122 said:**
> Easy gui way: search for disks in the dash and bring up the disk utility (assume you are using Ubuntu or Ubuntu gnome) Locate the partition you want to auto mount, click on it, then click the gear icon on lower left corner of the partition table (not the upper right one) Choose Edit Mount Options (screenshot 1), then turn OFF  "Automatic Mount Options" and make sure the box 'mount at startup' is checked (screenshot 2). 

That's it. Next time when you reboot the partition will be mounted.

Thanks! 

I didn't know about this feature of [s]palimpsest[/s] gnome-disks. ;)

---

