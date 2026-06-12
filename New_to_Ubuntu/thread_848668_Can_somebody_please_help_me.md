---
title: "Can somebody please help me?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by pensaer on 2008-07-03
I'm trying to dual boot hardy heron and windows xp on my machine.  I previously had windows installed across two HDD with a raid 0 array.  I want to reinstall windows on one harddrive and unbuntu on the other.  When I began reinstalling windows I was prompted to download some updates, and after I downloaded and installed them and rebooted I now get the blue screen o' death and can't proceed with installing windows.  it says something like "please remove any recently installed hardware and check for viruses".  Anyway, I am wondering how I can go ahead and repartition my drives and at least get ubuntu installed on one of them and worry about the windows later.  I'm worried that since windows did not get a clean install the onboard raid controllers will mess with my installation of ubuntu.

Specs:
Abit IP35 pro mobo w/ ICH9 
Intel Core 2 Duo
(2) 250GB Seagate Barracuda HDD SATA

As of right now I'm just floating on the liveCD, somebody please throw me a life preserver here.  Thanks much for your advice in advance.

---

### Post by sayakb on 2008-07-03
Ubuntu installation should not be a problem. Use the partitioner available with the LiveCD (gparted). If necessary, force mount a drive by:
```
sudo mount /dev/sda1 /media/drivename -o force
```

But if you install Windows **after** ubuntu, you'll lose GRUB. Use [Supergrub Disk]("http://www.supergrubdisk.org/") to revive grub.

---

### Post by pensaer on 2008-07-03
gparted recognized both drives as unallocated.  neither has a disklabel on them currently.  it warns me that if i were to add one it will delete the info currently on the disk.  i don't mind  if that happends (i have everything backed up), but will that sufficiently wipe all the windows info off and give me a clean install of ubuntu?  

thanks for your quick response.

---

### Post by sayakb on 2008-07-03
Yes.. rather than formatting, **delete** the drive and make a new partition again (you could format the new partition for Windows in NTFS if you like)

---

### Post by pensaer on 2008-07-03
awesome, thanks for the advice.  wish me luck, here goes...

---

### Post by sayakb on 2008-07-03
Best of Luck! It should go just fine :D

---

### Post by pensaer on 2008-07-03
alright, installation went fine, but upon rebooting it says:

loading GRUB (or something to that effect)
Error 2

what should I do about the number two?

btw, i partitioned as follows:

10GB /
4GB swap
120 GB /home

---

