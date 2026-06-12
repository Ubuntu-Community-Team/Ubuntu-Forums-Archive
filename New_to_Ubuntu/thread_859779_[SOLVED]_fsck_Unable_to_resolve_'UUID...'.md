---
title: "[SOLVED] fsck Unable to resolve 'UUID...'"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Rohag on 2008-07-14
I recently installed Wine 1.0.0 in Ubuntu 8.04 (AMD64) using the Synaptic Package Manager (0.61ubuntu9). Encountering too many difficulties and finding it did not meet my needs, I uninstalled Wine also using Synaptic. Shortly thereafter I tried to run fsck and got the following error:

```
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=3979e44f-e96a-4d49-ba11-13139309d4b3'
```

I can boot and reboot normally. I have so far failed to understand 'sudo mkdir /path/to/mountpoint', and 'sudo mount -a' does not resolve the problem. I have no idea if what's happening is related to my Wine experience.

Is this “unable to resolve” issue simply due to the system being up and running off the drive in question (sda1)? How can I command the system to shutdown nicely and reboot with a fsck?

Here are the results of what I hope are a few relevant terminal commands; note that the volume UUID of /dev/sda1 is consistent:

```
sudo blkid
/dev/sda1: UUID="3979e44f-e96a-4d49-ba11-13139309d4b3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="a72ee817-bb78-4bfa-b61c-c41176d0feac"
``` 

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3979e44f-e96a-4d49-ba11-13139309d4b3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a72ee817-bb78-4bfa-b61c-c41176d0feac none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

```
sudo fdisk -l
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a7c0a7c

   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       23946   192346213+  83  Linux
/dev/sda2           23947       24321     3012187+   5  Extended
/dev/sda5           23947       24321     3012156   82  Linux swap / Solaris
```

```
sudo mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```

Regards and Hopeful Thanks!

---

### Post by iaculallad on 2008-07-14
> **Rohag said:**
> 
```
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=3979e44f-e96a-4d49-ba11-13139309d4b3'
```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
[COLOR="Red"]UUID=3979e44f-e96a-4d49-ba11-13139309d4b3[/COLOR] /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a72ee817-bb78-4bfa-b61c-c41176d0feac none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```



Try substituting /dev/sda1 for UUID=3979e44f-e96a-4d49-ba11-13139309d4b3 in your fstab file.

---

### Post by mcduck on 2008-07-15
Icould indeed be true that this is because you are trying to run fsck on mounted partition. The partitions should never be mounted when you check them.

To force fsck to check the partitions on next boot run this command (& reboot):

```
sudo touch /forcefsck
```

---

### Post by Rohag on 2008-07-15
@mcduck: Thank you! Where or how do I read the fsck exit code or results once the check is complete? Will the same 'mount' command syntax also work for 'e2fsck'?

---

### Post by mcduck on 2008-07-15
> **Rohag said:**
> @mcduck: Thank you! Where or how do I read the fsck exit code or results once the check is complete? Will the same 'mount' command syntax also work for 'e2fsck'?

You should see the results during the boot when fsck is running. It's probably also stored in some log file, but I haven't got access to any Linux machine right now so I can't check which one.

I didn't quite understand the question about 'mount' and 'e2fsck'. They are two completely different things. Anyway, you don't need to run e2fsck or any other individual fsck command. Simple 'fsck' will automatically detect what file system the partition has and then runs the correct check.. See "man fsck" for more details & instructions. ("sudo fsck /dev/nameofthedevice" would be the basixc syntax for fsck. And of course the partition shouldn't be mounted when you check it..)

THe commmand I gave just creates a file called "forcefsck" on the root partition. The system detects that file during boot and runs fsck. The file is removed after that automatically.

---

### Post by mngsailing on 2009-11-08
I seem to have two different UUIDs for my /home partition /dev/sda5.
When I boot, grub says it cannot resolve the UUID  It shows me UUID "A" b423d14d-....  
If I change the UUID using tune2fs into b423d14d..., the next boot says it cannot resolve the UUID "B", which is 5dcf8eaa-....

If now I do tune2fs -U 5def8eaa-... /dev/sda5, on the next boot grub say it cannot resolve UUID b423d14d-....   That is the one I though I had got rid of.

Questions: Is the UUID shown by grub in the partition superblock with the /dev or is it something in grub's memory bank?  What does tune2fs actually change?

---

