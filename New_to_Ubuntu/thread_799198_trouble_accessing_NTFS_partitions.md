---
title: "trouble accessing NTFS partitions"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by hemajith on 2008-05-18
I have recently installed Ubuntu 6.06. I have a dual boot system with Windows and Ubuntu. My Problem is that I can see the NTFS partitions on GUI and can mount them from the terminal too but when trying to access, it says 'permission denied!". In the GUI mode when I try to access it says "unable to mount". I was using Fedora before and I could access these partitions without any difficulties. Please help!

---

### Post by teaker1s on 2008-05-18
something quick and simple to try

panel
right click 
add to panel
select
disk mounter

---

### Post by hemajith on 2008-05-18
I'm a bit new to Linux. Please tell me what "panel"?

---

### Post by teaker1s on 2008-05-18
bar at top and bottom of desktop with clock volume etc etc

---

### Post by akiratheoni on 2008-05-18
> **hemajith said:**
> I'm a bit new to Linux. Please tell me what "panel"?

He is referring to the panel that says 'Applications Places System'.

Although 6.06 is an old version of Ubuntu, I advise you upgrade directly yo 8.04, which you can do because both of the releases are LTS.

---

### Post by hemajith on 2008-05-18
Tried adding Disk mounter, but it does not work! When I select Disk mounter and click "+Add"...nothing happens!

---

### Post by teaker1s on 2008-05-18
odd try dragging the icon onto panel

---

### Post by hemajith on 2008-05-18
That does not work too! Sheeesh! lol

---

### Post by teaker1s on 2008-05-18
very strange, this should work as a normal user, may be worth using a new login to see if your user account profile is corrupted

---

### Post by hemajith on 2008-05-18
Tried a new profile too. Still it happens. I gave the new profile admin rights too.

---

### Post by spiderbatdad on 2008-05-18
Pretty good guide to 6.06 here:[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

---

### Post by hemajith on 2008-05-18
this is what I get when I try to mount it through GUI

error: device /dev/sda3 is not removable

error: could not execute pmount

With terminal I can mount the volume but can't access as it says "permission denied"!

---

### Post by spiderbatdad on 2008-05-18
can you copy/paste the contents of /etc/fstab

---

### Post by hemajith on 2008-05-18
yes I can

---

### Post by spiderbatdad on 2008-05-18
> **hemajith said:**
> yes I can
lol.ok, as an example:```
/dev/sda1 /mnt/winxp -t ntfs -r -o auto, umask=0222 
```

where you have previously run:```
sudo mkdir -p mnt/winxp
```
and where sda1 is actually determined by:```
sudo fdisk -l
```

---

### Post by haxt on 2008-05-18
I agree with 'akiratheoni'. Get rid of 6.06. It's a horrible distro imo. Upgrade to Hardy Heron 8.04 now!

---

