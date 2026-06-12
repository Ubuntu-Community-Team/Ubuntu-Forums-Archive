---
title: "Unable to restore image file, disk backup/restore"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by laserman on 2012-04-29
I performed a backup of my hard drive (160 GB) from a live CD to another drive partition (sda with 1 tb available) with the following code:

```
sudo dd if=/dev/sdb of=/media/Elements/minilaptopbkup.iso
```

It took about an hour and the process was complete. When I attempted to write it back, I used the following code:

```
sudo dd if=/media/Elements/minilaptopbkup.iso of=/dev/sdb
```

It took some 7 hours to write back, only to find out that there doesn't appear to be any data or is corrupt. When I tried to reboot my laptop, it only had the black screen indicating grub rescue. I searched for attempts to restore my grub but have come up empty in trying to restore this drive to a bootable condition.

My whole data life has now disappeared as the drive from where it was removed has already been cleaned. I know this violates every law ever preached but it was in my attempt to backup this data, thinking I was doing it right in the first place. 

I tested my process also on a 4 gig stick and had not the first problem using the same code above but changing to adapt to the proper drives. It backed up the stick in an iso. I formated the stick, cleaning the drive and then reversed the command and successfully wrote the data back to the stick, restoring it to its original condition.

I've tried to mount the iso with:

```
sudo mount -o loop /dev/sdb /mnt
```

It would not mount and wonder if I am executing the correct code for this to mount?

So...my question to the community is, is there a way to tell if the image file I have is recoverable and how can I find out?

laserman

---

### Post by laserman on 2012-04-29
> **laserman said:**
> It would not mount and wonder if I am executing the correct code for this to mount?

I wanted to add, this is the error I received when trying to view the hard drive in Nautilus:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I looked at the drive in Gparted and there is 24 GB of space available with the rest consumed by "data". Everything looks like its there in that regard, even the swap partition was visible. 

Thanks.

---

### Post by laserman on 2012-04-29
Y A H O O!

):P

I found this thread:

[http://ubuntuforums.org/showthread.php?t=1328600](http://ubuntuforums.org/showthread.php?t=1328600)

and noted this command:

```
sudo fsck /dev/sdb
```

...but changed the sdb to match my correct drive (sda) and did this from a live CD. After some rolling on the screen and whirring of the drive, it stopped. Still couldn't mount it but shut it down and fired it back up and VIOLA, the hard drive booted and all is intact. The image I made of the drive was good. WHEW! Hopefully, this will help others that have run into a similar problem restoring a drive.

laserman

---

### Post by Michael Dooley on 2012-04-29
Thanks for reporting back laserman! I use clonezilla for this kind of thing but it's nice to know how to get out of trouble if using dd.

---

