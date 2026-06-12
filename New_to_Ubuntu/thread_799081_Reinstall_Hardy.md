---
title: "Reinstall Hardy"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Unstuck on 2008-05-18
I recently moved my home partition using **[this]("http://www.psychocats.net/ubuntu/separatehome")** set of directions from Psychocats.  Everything seemed to go pretty well, but after rebooting it wasn't able to find the Home partition.  Running the LiveCD, I was able to determine that all the files did transfer to the new partition, so I thought the easiest way to solve the problem is to reinstall Hardy on the original partition.  I was going to do this anyway (and add OpenSUSE) so I'm not losing any time...

Any thoughts?

---

### Post by kwacka on 2008-05-18
Its easy to install, but you don't learn anything.

Check your /etc/fstab file against the one at the psychocats, making sure that you amend the location of your new /home to your partition - they use hda7 which may well be different to yours.

If you can get it working you will be able to share the /home partition between the two distributions.

---

### Post by Unstuck on 2008-05-18
kwacka inspired me to do this the right way.  here's the problem:

the data on the original partition (sda1) now takes all the storage space given to it.  the psychocats manual suggests i can delete the /home_backup from the partition to free up some room, but after running the command (sudo rm -rf /home_backup) nothing happens...there is no output from terminal, just a new command line/prompt.

Also, I'm not sure what is going on with fstab.  I saved this line
> /dev/sda3 /home ext3 nodev,nosuid 0 2 as per the manual but this is how fstab reads after saving the change and rebooting

FSTAB
> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

...the added line is gone.

---

### Post by rustutzman on 2008-05-18
I suspect you did but did you edit as root? Always make a backup copy first though.

Russ

---

### Post by Unstuck on 2008-05-18
I guess I didn't make changes to it as root...I thought I did.  Opened the file > sudo gedit /etc/fstab added the line, saved the changes and rebooted.  How should I have edited it?

---

### Post by Unstuck on 2008-05-18
bump

---

### Post by meierfra. on 2008-05-18
> unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0 

This looks like the  fstab from the LiveCD. You need  edit the fstab from your Ubuntu partition.

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
gksudo gedit /ubuntu/etc/fstab

```

---

### Post by Unstuck on 2008-05-18
Thanks, meierfra.  I ran the three commands...and fstab was completely blank
:confused:

---

### Post by meierfra. on 2008-05-19
Did you get any error message after "sudo mount -t ext3 /dev/sda1 /ubuntu"?

Maybe /dev/sda1 is not your  root partition?  Post the output of

```
sudo fdisk -l
```
(l is a lower case L)

---

### Post by Unstuck on 2008-05-19
I didn't get any errors after running commands; I was very surprised I had this problem because everything seemed to go smoothly.

Here is the fdisk output
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a62544e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7998    64243903+  83  Linux
/dev/sda2           30120       30401     2265165    5  Extended
/dev/sda3            7999       30119   177686932+  83  Linux
/dev/sda5           30120       30401     2265133+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe25de25d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2434    19551073+   7  HPFS/NTFS


---

### Post by meierfra. on 2008-05-19
Are you sure that sda1 is the root partition? Could it be sda3?

You might try 

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
gksudo gedit /ubuntu/etc/fstab

again. Maybe you just had a typo.

Or try with sda3 in place of sda1.

You could also try to find  "fstab" manually: Go to Places->Computer and double click the icon for the ubuntu root partition. (Actually you might also have an icon for the Ubuntu partition on your desktop)  Browse to /etc and see whether you can find "fstab"

---

### Post by Unstuck on 2008-05-20
I am fairly certain /dev/sda1 is the root directory because it was the partition that originally held /home.  I went to Places > Computer and opened /etc/fstab and it was indeed blank.  

I also entered "sudo mount -t ext3 /dev/sda1 /ubuntu" then "mount" and got the following information.  I don't know what it means or if it is helpful.

> 
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb1 on /media/disk-2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


---

