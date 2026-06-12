---
title: "[SOLVED] dual boot with fat32 mount error"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Chlorate on 2008-05-28
I've been trying to use the illustrated guide to dual booting windows [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I have all my partitions ready.

#1 primary 16.00 GB B K ntfs   /media/sdal
#2 primary 16.00 GB   F ext3   /
#5 logical 210.1 GB   f fat32  /windows
#6 logical 8.00 GB    F swap    swap

That is what I see, then when I finish partitioning I get the error

"The attempt to mount a file system with type vfat in SCST1 (0, 0, 0), partition #5 (sda) at /windows failed."

I don't know what to do! I followed the instructions and made sure I matched up with the guide. I only have windows technically installed. I can't figure out what I'm doing wrong. 

Please help! Thanks. 

If I can't get this working I'll just do the first option when you install Ubuntu (with the little slider) but I like the idea of the shared space between them a lot. So please, help! :(

---

### Post by housam on 2008-05-28
Boot from the live CD and type in the terminal 

```
sudo fdisk -l
```

where -l is a small L and post the results please

---

### Post by Chlorate on 2008-05-28
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1946    15631213+   7  HPFS/NTFS
/dev/sda2            1947        3891    15623212+  83  Linux
/dev/sda3            3892       30401   212941575    5  Extended
/dev/sda5            3892       29434   205174116    b  W95 FAT32
/dev/sda6           29435       30401     7767396   82  Linux swap / Solaris

---

### Post by housam on 2008-05-28
If you want to use the fat32 sda5 partition as a shared between ubuntu and windows reformet it to ntfs using Gparted . it is accessable from both OS.

You still able to install ubuntu on sda2 , it is ready for installation. just assign it manually as a root ( / ) during the installation

---

### Post by Chlorate on 2008-05-28
> **housam said:**
> If you want to use the fat32 sda5 partition as a shared between ubuntu and windows reformet it to ntfs using Gparted . it is accessable from both OS.

You still able to install ubuntu on sda2 , it is ready for installation. just assign it manually as a root ( / ) during the installation

Should I do this through the way I have been doing or use the live CD to install it? 

And what is Gparted? Should I install ubuntu and just leave that fat32 as free space and use gparted? I need details. I don't want to screw this up! lol. Thank you though in advance.

---

### Post by housam on 2008-05-28
Boot from the live CD  and go for system >> admin. >> partition editor ( Gparted ) . it is the partitioning tool. do the format before installing ubuntu . You can take a screen shot ( applecations >> accessories >> screen shot ) and post an image of Gparted .

---

### Post by oedha on 2008-05-28
what if you change the mount point of sda5 to /media/sda5 or /media/foldername ?

---

### Post by Chlorate on 2008-05-28
Alright I put the screenshot as an attatchment. Does everything look right? 

I will apply the changes if it's all okay. 

So once that is done I should just do an installation from the live disc, then do the manual partition install, and everything should be ready to go?

---

### Post by Chlorate on 2008-05-28
> **oedha said:**
> what if you change the mount point of sda5 to /media/sda5 or /media/foldername ?

What would that do? I could try that option, or the one from housam? 

Choices! Hmm, the housam one seems simpler, but if that one doesn't work I can always try yours oedha.

---

### Post by housam on 2008-05-28
It looks fine . go ahead for the installation . when it comes to the partitioning step , choose the manual way and assign the sda2 for installation as a root with the sign ( / ) .
Good luck

---

### Post by Chlorate on 2008-05-28
Argh. I feel so helpless. I swear once this is done I know it has to be smoother sailing.

So it is asking me to mount them. I mounted the sda1 (windows xp) to /windows and sda2 to / and sda5 to /windows and sda6 is a swap. But now they can't share the same mount point. Should I just leave them blank? And should I format anything?

---

### Post by housam on 2008-05-28
only mount sda2 as a root and do not format any thing ( if you want let sda2 only to be reformatted ).

---

### Post by Chlorate on 2008-05-28
Alright I got it working, thank you so much. I can now enjoy linux with peace of mind, now onto the fun!

---

### Post by housam on 2008-05-28
Glad to hear that. congratulations. 
cheers
Housam

---

