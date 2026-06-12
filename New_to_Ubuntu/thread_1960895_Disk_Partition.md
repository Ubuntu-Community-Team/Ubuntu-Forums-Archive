---
title: "Disk Partition"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by e1078 on 2012-04-18
Dear Concerned,
 
Please help me in knowing can we have HDD partioned like windows while installing Ubantu, So that data will be safe in event of machine crash & the same can be retrived.
 
It will be more helpful if any one guide on having the partition size to my machine I have got 500 GB HDD,  6 GB RAM core i5 processor.

---

### Post by ksprasad on 2012-04-18
Hi,
 
If you meant a partition which can be accessed from both windows and linux, u need to create it in NTFS format. Before installing ubuntu itself u can create it using gparted. But ubuntu install partition should be ext4. 
 
Regards,
ksprasad

---

### Post by e1078 on 2012-04-18
> **ksprasad said:**
> Hi,
 
If you meant a partition which can be accessed from both windows and linux, u need to create it in NTFS format. Before installing ubuntu itself u can create it using gparted. But ubuntu install partition should be ext4. 
 
Regards,
ksprasad
Dear Prasad,
 
Thanks for the input but i only want to have Ubantu installed on the machine with partition so to protech data in event of crash.
 
Thanks in advance
 
Regards,
Abhijin

---

### Post by kc1di on 2012-04-18
> **e1078 said:**
> Dear Concerned,
 
Please help me in knowing can we have HDD partioned like windows while installing Ubantu, So that data will be safe in event of machine crash & the same can be retrived.
 
It will be more helpful if any one guide on having the partition size to my machine I have got 500 GB HDD,  6 GB RAM core i5 processor.

I'm not exactly sure what your asking?

But if your asking can you have a Windows partition on ubuntu the answer is yes. If you want to make a seperate /home partition the please see the following guides.

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

or this one:

[http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by e1078 on 2012-04-18
> **kc1di said:**
> I'm not exactly sure what your asking?

But if your asking can you have a Windows partition on ubuntu the answer is yes. If you want to make a seperate /home partition the please see the following guides.

[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

or this one:

[http://www.psychocats.net/ubuntu/installseparatehome]("http://www.psychocats.net/ubuntu/installseparatehome")
Dear Prasad,
 
Appreciate your concern , i only want to know can i have HDD partioned like Windows while installing Ubantu.
 
I dont need to access any drive from windows as i will only be using Ubantu as OS.

---

### Post by kc1di on 2012-04-18
> **e1078 said:**
> Dear Prasad,
 
Thanks for the input but i only want to have Ubantu installed on the machine with partition so to protech data in event of crash.
 
Thanks in advance
 
Regards,
Abhijin
Ok now that I understand your question here is how I would partiton your HDD for Ubuntu install:

Use the guide mentioned in my last post to create a seperate /home partiton. 

/ (partition for system files) 12 GB
swap Partition 4GB (not sure if this is a laptop but you'll need it if it is , if not you don't strictly need a swap partion.) 

/Home Partition Rest of disk.

Good luck :)

---

### Post by e1078 on 2012-04-18
Thank you Dave, I will try.

---

### Post by ksprasad on 2012-04-18
Hi Abhijin,
 
In ubuntu even in case of system crash, u can very well access the disk partitions using live cd/usb. I usually use different partiton to store my data and give around 40gb for my root partition :) 
 
Regards,
ksprasad

---

### Post by e1078 on 2012-04-18
Thank u Prasad for the input.

---

### Post by The Cog on 2012-04-18
Just to be clear, you cannot install Linux on a Windows partition. Neither can you place user's home directories on a Windows partition. This is because Windows NTFS filesystem cannot store the required Unix permissions and file properties.

You can however split the disk into different partitions with the Linux system and home directories on the Linux filesystem and place other data on an NTFS/FAT partition. It is possible for Linux and its users to access the NTFS/FAT contents.

Of course, regular backups is the proper way to address your concerns.

---

### Post by Mark Phelps on 2012-04-18
> **e1078 said:**
> ... Please help me in knowing can we have HDD partioned like windows while installing Ubantu, So that data will be safe in event of machine crash & the same can be retrived.


I think the problem you're having getting answers is that basically, your question is nonsensical -- in that, there is no partitioning scheme that Windows uses that makes your data safe in the event of a machine crash.

As already mentioned, if your machine crashes, you can boot from an Ubuntu desktop PC and use it to retrieve your data.  That has nothing to do with any partitioning scheme.

The only way to protect your data from system crashes is to regularly back it up to external drives.  And, once again, that has nothing at all to do specifically with either MS Windows or Ubuntu.

---

