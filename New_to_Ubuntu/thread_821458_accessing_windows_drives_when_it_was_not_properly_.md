---
title: "accessing windows drives when it was not properly shutdown"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by sharks on 2008-06-07
my windows was corrupt so i had to shutdown manually and i cannot log on to it and because of that i could not access my windows partitions.is there a way to access my windows partitions.i dont have windows installation cd.

---

### Post by rraj.be on 2008-06-07
I think running a fsck may solve this problem.

i have Not yet tried this ,but i hope this will reset the set flag thus enabling  it to be mounted.

Before that you could try a force mount drive to gain access.

I am sure you can clear this by the following.

Just try it and reply to me soon.

```
sudo mkdir /media/windows
sudo mount /dev/(yourdevice) /media/windows -o force
```

---

### Post by sharks on 2008-06-07
when i tried the code it says
> mount: can't find /dev/sda1/media/windows in /etc/fstab or /etc/mtab


---

### Post by rraj.be on 2008-06-07
Is your drive visible in fdisk.

if it's visible in that then it should work surely.

Else try ```
Touch
``` function to change access parameters of the Drive.

---

### Post by sharks on 2008-06-07
the drives are listed.when i try fsck it says it could cause serious error

---

### Post by rraj.be on 2008-06-07
Could you post the output of 

```
sudo fdisk -l | grep NTFS
```

---

### Post by sharks on 2008-06-07
It is:

> /dev/sda5            1365        2716    10859908+   7  HPFS/NTFS
/dev/sda8            3953        5864    15358108+   7  HPFS/NTFS
/dev/sda9            5866        7777    15358108+   7  HPFS/NTFS
/dev/sda10           7778        9730    15687441    7  HPFS/NTFS


---

### Post by bumanie on 2008-06-07
I would firstly try to navigate to the partitions via Places --> Computer --> File system. To do this with super user rights type > gksudo nautlius in terminal. See if you are able to copy important data off the partitions. After saving what you can, (hopefully everything) in terminal > sudo ntfsprogs. Then with each partition > sudo ntfsfix dev/sda5 > sudo ntfsfix /dev/sda6 and so on until you gone through all the partitions. This may fix the file systems. If it is the bot sector that is bad, try supergrub disc or test disk to fix that area.

---

