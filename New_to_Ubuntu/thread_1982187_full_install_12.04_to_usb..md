---
title: "full install 12.04 to usb."
date: 2012-05-18
forum: New to Ubuntu
---

### Post by newbuntu12 on 2012-05-18
I was curious if this would work...
ive been using 12.04 on a live usb on a hp laptop (vista) cant install to internal hdd so
I installed 12.04 from a live usb to a 4gig usb :] 
 No problems, it boots fine (grub installed to 4gig usb as well) So now im obviously needing more space.. 
is there a way to setup another usb/external drive to work w/ubuntu by default? meaning Auto saving downloads, updates, and more imporanly Swap space.  I formated and partioned another 4gig usb to try and accomplish that..  3gigs for a Ext4 filesys, and 1gig for swap. is this correct? when i look at it in gparted or disk tools it partioned fine, and when i look at it in the filemanager it has a root(?) folder called lost+found.  i know i can sav files on various file systems but is it possible to setup swap space on the 2nd usb?

sorry for the grammer/confusion/newbness

---

### Post by newbuntu12 on 2012-05-18
"is it possible to setup swap space on the 2nd usb?"
in other words setup swap on usb2 for use on usb1(ubuntu)

---

### Post by Vereinfachen on 2012-05-18
yup its possible. :KS

You need to edit your /etc/fstab file to accomplish that.

Please look here on how to do that: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by newbuntu12 on 2012-05-18
Thanks! Exactly what I needed.
At first glance im not sure which of the following is correct.. for my..unique..situation :]

*Im running a full install of 12.04 entirely off of usb1 (4gig)
I configd/partd usb2 w/ 3gigs of ext4 + 1gig swap.*

# Separate Home # /dev/sda7 UUID=413eee0c-61ff-4cb7-a299-89d12b075093  /home  ext3  nodev,nosuid,relatime  0  2 
or
# Data partition # /dev/sda8 UUID=3f8c5321-7181-40b3-a867-9c04a6cd5f2f  /media/data  ext3  relatime,noexec  0  2

they both seem fitting... :/

---

### Post by Vereinfachen on 2012-05-18
Do you want to move your home folder to the new partition or do you want to create a seperate drive where you can store files?
Also, check the UUIDs, they differ.

Also, you need to add your swap partition to that list or else it won't get used. :)

---

### Post by newbuntu12 on 2012-05-18
glad I hit refresh before editing fstab :] 

I was planning on creating a seperate drive to store files + use as swap space.
thanks for the tips, got my uuids and trying to find the little note on Swap space i saw earlier :]

---

### Post by newbuntu12 on 2012-05-18
I was about to proceed w/#Data partition# 

Any recommendation one way or the other? (new home? or data?)

the page i was linked to says "note: swap has no mount point).  Mount points should not have spaces in the names." Does "no mount point" = 0 ? or do i leave it blank?

---

### Post by newbuntu12 on 2012-05-18
heres my edited Fstab. Im trying to do a data partition.. technically 2? (including swap)
how does it look?

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=fe2c5f0e-a1ae-4657-b9a4-08e962b90f4c /               ext4    errors=remount-ro 0       1
/dev/sdc1
UUID=3d95a64a-b226-4c75-84be-ac3f93762f55  /media/data  ext4  relatime,noexec  0  2
UUID=2f2ee278-d049-4ad0-a26e-187e4d3fc93c  /media/data  Swap  relatime,noexec  0  2

---

### Post by Vereinfachen on 2012-05-18
remove /dev/sdc1 and your swap line must look like this:
```

UUID=2f2ee278-d049-4ad0-a26e-187e4d3fc93c none swap sw 0 0
```

oh and why are you using noexec? that doesn't make sense, remove that option ;)

---

### Post by newbuntu12 on 2012-05-18
great, ill fix it up.

remove /dev/sdc1 from all of fstab? or just swap line? or swap + new data line?

[/CODE]oh and why are you using noexec? that doesn't make sense, remove that option ;)[/QUOTE]

'cause Im out of my league here :]  Will do! that  would explain the "unable to load swap
" "noexec" error i got at boot  lol

---

### Post by newbuntu12 on 2012-05-18
All set!  Thanks for the help guys. 
Im somehow bypassing the login screen and being prompted for keyring few min after desktop loads.

---

