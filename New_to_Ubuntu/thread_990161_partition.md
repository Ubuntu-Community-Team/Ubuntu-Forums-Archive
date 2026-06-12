---
title: "partition"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by dean5000v on 2008-11-22
hey well i previously had windows xp installed and i wanted to dual boot with ubuntu. So i've installed ubuntu and i made sure that i created another partition for the new installation to be on the problem is when i use this command. 

sudo /sbin/fdisk -l

it only lists the linux partition, when i installed ubuntu could it of deleted the windows partition automatically ? 

i've tried google but isn't really giving me answers

---

### Post by handydan918 on 2008-11-22
If you will post the output of fdisk, we will know for sure. 

And no , Ubuntu doesn't "automatically" delete Windows. You have to tell it to.

---

### Post by beno1990 on 2008-11-22
The Ubuntu installer will automatically delete all other partitions unless you specify a manual partition setup.

Check the size of this partition against the total size of the drive. If they match or they're pretty close, it's a safe bet that the XP partition was deleted in the install.

---

### Post by davideotape on 2008-11-22
Open the terminal up, and type in this code:
```
sudo fdisk -l
```

Then press enter, and post the results. This should help to tell what has happened to the windows partition.

---

### Post by dean5000v on 2008-11-23
Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22aae730

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36483   293049666   83  Linux
dean@dean-desktop:~$ 
dean@dean-desktop:~$ 
dean@dean-desktop:~$ 



looks to me as if the partition has been deleted

---

### Post by kansasnoob on 2008-11-23
> **dean5000v said:**
> Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x22aae730

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36483   293049666   83  Linux
dean@dean-desktop:~$ 
dean@dean-desktop:~$ 
dean@dean-desktop:~$ 



looks to me as if the partition has been deleted

Sure does! You also have no swap!

Start by doing some studying here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

and here:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

---

### Post by dean5000v on 2008-11-23
hey well i want to avoid putting windows on if i can the problem is that i need windows 2007 to do my university work on. Would wine work for the office 2007 ?

---

