---
title: "Problem with automounting raided drives in ubuntu."
date: 2011-09-16
forum: New to Ubuntu
---

### Post by ZcRaider on 2011-09-16
Hello guys!

I have a small issue.  I'm slowly starting to get use to ubuntu.  I'm certified to work on windows, but linux is a little difficult for me.

The ubuntu installation that im using as a fileserver via Samba shares has a problem of not automounting my raid drive.  The raided drives are being used for Samba.

That being said, how do I make ubuntu auto load the drives when I startup?  

We have been having some power outages lately.  Hurricanes and fall storms...  Each time the server is shutdown, the raided drive has to be remounted.  Meanwhile if im not on duty, access to the samba shares are broken until i remount the raided drives.

You would think that ubuntu would automatically do this, but it doesnt.

I am new to ubuntu.  I know there are configuration files that have to be spoon fed to make easy operations work.

I was looking on the forums and i read that the fstab file needs to be edited.  However, when i tried to put in the info, the problem still occurs.  So I must be doing something wrong.

Here are the blkid and fdisk -l commands:
> Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30017   241111521   fd  Linux raid autodetect
/dev/sda2           30018       30394     3028222    5  Extended
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30017   241111521   fd  Linux raid autodetect
/dev/sdb2           30018       30394     3028222    5  Extended
/dev/sdb5           30018       30394     3028221   82  Linux swap / Solaris

Disk /dev/md0: 246.9 GB, 246898098176 bytes
2 heads, 4 sectors/track, 60277856 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036801

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1816    14585856   83  Linux
/dev/sdc2            1817        1947     1044481    5  Extended
/dev/sdc5            1817        1947     1044480   82  Linux swap / Solaris
AND....

> /dev/sdc1   *           1        1816    14585856   83  Linux
/dev/sdc2            1817        1947     1044481    5  Extended
/dev/sdc5            1817        1947     1044480   82  Linux swap / Solaris
root@Viewmaster-PC:~# blkid
/dev/sda1: UUID="2e1d7b82-0623-191d-01de-944d0b8744e9" TYPE="linux_raid_member" 
/dev/sda5: UUID="2fc8d598-7e18-46f3-bac3-9c114a3b7de5" TYPE="swap" 
/dev/sdb1: UUID="2e1d7b82-0623-191d-01de-944d0b8744e9" TYPE="linux_raid_member" 
/dev/sdb5: UUID="19111bb4-3094-40a5-8823-d1bfe2110458" TYPE="swap" 
/dev/md0: UUID="d0406e91-f932-4b31-bb01-5cf39f82a51e" TYPE="ext4" 
/dev/sdc1: UUID="31addba2-6422-4e9b-b65e-fb00c68efdc0" TYPE="ext4" 
/dev/sdc5: UUID="5c47552e-4fd4-45db-acb3-af6824c5378a" TYPE="swap" 
and finally the contents of the fstab file:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
UUID=5c47552e-4fd4-45db-acb3-af6824c5378a /media swap default 0 0I would greatly appreciate any assitance.  I know there must be something im typing wrong...

Thanks
Michael

---

### Post by Gone fishing on 2011-09-16
Have a look at these how tos. [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID) or [http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04](http://www.howtoforge.com/how-to-set-up-software-raid1-on-a-running-system-incl-grub2-configuration-ubuntu-10.04)

on your box /dev/sda1 and /dev/sdb1 are part of /dev/md0 raid and the raid isn't /

I think in fstab 

/dev/md0      /mnt/raid     ext4    defaults    1 2

will work

---

### Post by sanderd17 on 2011-09-16
Is this software raid or hardware raid?

And why do you mount something to /media as swap? How did that line get into your fstab file?

You swap line should look like 
```

/dev/sdxy swap swap default 0 0

```

---

