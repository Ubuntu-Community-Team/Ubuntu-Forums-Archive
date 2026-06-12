---
title: "partition table created using SATA-USB interface vs laptop hard drive bay"
date: 2021-01-24
forum: New to Ubuntu
---

### Post by youngwarlock on 2021-01-24
I created a dos/mbr partition table and some partitions using gparted, on a hard drive I connected to my laptop via a SATA-USB interface. I then placed the hard drive in my system hard drive bay and booted the system using a live USB. When I opened gparted, it did not recognize the partition table. I then created another partition table with the hard drive in the laptop's hard drive bay. When I removed the hard drive from the bay and connected it to my laptop via a SATA-USB interface, gparted was also not able to recognize the partition table. In both cases however, gparted was able to recognize the partition table on the hard drive, if I connect it to my laptop via the same interface with which I had created the partition table.

My question is how does the system differentiates between a partition table created in the hard drive bay and via a SATA-USB interface?

---

### Post by oldfred on 2021-01-24
I have a SATA to USB adapter.
It works great for my old SSD, but will not even spin up my old HDD.
Does your have separate power supply or just USB power. USB power probably not enough.

I do not recommend MBR for any drive unless you have to have Windows installed in BIOS boot mode on that drive.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by youngwarlock on 2021-01-24
> **oldfred said:**
> I have a SATA to USB adapter.
It works great for my old SSD, but will not even spin up my old HDD.
Does your have separate power supply or just USB power. USB power probably not enough.

I do not recommend MBR for any drive unless you have to have Windows installed in BIOS boot mode on that drive.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Thank you for your response. I use just USB power, and it has being working fine. With regards to the type of partition table, I also tried GPT but it was still not recognized.

---

### Post by youngwarlock on 2021-01-28
Problem solved! It turns out that the system cannot differentiate, but the SATA-USB interface I was using reverses the bytes block and so my system cannot read the content when the HDD is in the system HDD bay. So in order for the system to recognize data I placed on the HDD via SATA-USB, I need to use conv=swab in dd command
```

dd if=mbr_file of=/dev/drive_on_SATA-USB conv=swab bs=512 count=1

```
Now partition table will be unrecognized while HDD is still connected via the SATA-USB interface, but will be recognized if I place the HDD in the system HDD bay.

---

