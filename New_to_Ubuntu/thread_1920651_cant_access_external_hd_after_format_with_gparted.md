---
title: "cant access external hd after format with gparted"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by mickyevil on 2012-02-05
I have just formatted an external drive with gparted. This process was completed under the FAT32 file system.However when i plug the hd it is listed under devices but I cannot access it as one normally would

If I right click on the drive and try to safely remove it a  alert box pops up 'daemon inhibited' the same thing happens if I try to reformat with another program

After extensive googling I believe that gparted has formatted the drive so that it can only be accessed under root conditions, this is because the drive was 250gb and the prog assumed it would be for an operating system ? Only a hunch... I need to change the permissions on the drive? 

The program can successfully reformat the drive and it was working perfectly before any.... help would be much appreciated ...Im on ubuntu 11.10 :D

---

### Post by Bartender on 2012-02-05
I don't know about permissions, but it sounds like you've got nothing to lose by trying a few simple things first.  Why not plug the external back in, boot from your installer CD, and re-format that drive as ntfs?  See what happens.  Aldo try formatting as ext4.
I've never had to mess with permissions when formatting an external.

---

### Post by mickyevil on 2012-02-05
> **Bartender said:**
> I don't know about permissions, but it sounds like you've got nothing to lose by trying a few simple things first.  Why not plug the external back in, boot from your installer CD, and re-format that drive as ntfs?  See what happens.  Aldo try formatting as ext4.
I've never had to mess with permissions when formatting an external.
  

the only prog that can now reformat the drive is gparted no other program can access the drive. I will try to reformat to ntfs -  I must say Im not really impressed with gparted for a program with such high reviews on ubuntu software centre...just tried it m8 nothing doin...cant access the harddrive by leftclicking cant format with another prog just get the message 'daemon inhibited' ....gonna try the gparted forums

---

### Post by mickyevil on 2012-02-06
just a quick update...the situation seemed to resolve itself? the drive now mounts ...strange but no doubt I will be back on this forum with more questions soon ;)

---

### Post by Mosome on 2012-02-06
You can use MountManager to change access settings and bootups of other partitioned hard drives.

---

