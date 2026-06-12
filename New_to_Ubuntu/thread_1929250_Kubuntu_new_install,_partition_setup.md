---
title: "Kubuntu new install, partition setup"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by meduser on 2012-02-21
hi, I am installing a fresh copy of kubuntu 11.10. I am installing on a 250 gb hdd. I want to commit the whole drive to Kubuntu.

I have been told I need a root partition, a swap, and then make the rest a swap drive.  

I am not sure how to do what with it. I have the drive empty, but it is not formatted. I am installing kubuntu 11.10 from usb stick.my drive is sitting in the prepare partitions as /dev/sdb free space 250059 mb. 

Please, if anyone can help, it would be appreciated.

Thanks

---

### Post by forrestcupp on 2012-02-21
I would just let the installation do it automatically. During the installation, it will automatically create a small swap partition, and another one for root and everything you need.

---

### Post by meduser on 2012-02-21
Hello, and thank you for the reply.

I had a thread going:

[http://ubuntuforums.org/showthread.php?t=1928629](http://ubuntuforums.org/showthread.php?t=1928629)

That is why I am looking for help on the partitioning and setup of Kubuntu. I want the home partition to have the majority of the free space, with the root partition only being 30gb's. I also need to know how big to make the swap partition, as last time I made it 70gbs...oops.

I have 4gbs of ram, an empty 250 gb hdd, that had all the other partitions deleted. I want this to run clean, stable, and I don't want to be running out of room on the home directory.

---

### Post by forrestcupp on 2012-02-22
> **meduser said:**
> 
That is why I am looking for help on the partitioning and setup of Kubuntu. I want the home partition to have the majority of the free space, with the root partition only being 30gb's. I also need to know how big to make the swap partition, as last time I made it 70gbs...oops.

I have 4gbs of ram, an empty 250 gb hdd, that had all the other partitions deleted. I want this to run clean, stable, and I don't want to be running out of room on the home directory.

Well, if you want to manually set it up, they recommend that the swap partition be a minimum of how much RAM you have, but preferably double. So, if you feel that you can spare it, you would make a swap partition of 8GB, your '/' root partition of 30GB, then create a partition out of the rest of the unallocated space and mount it as /home.

If Kubuntu's setup is like Ubuntu's, then on the screen where you can choose to let the setup automatically do the partitioning, you would choose the option that says something like "Do something else". From there you can delete all the partitions, create new ones, including swap, out of the unallocated space, and mount them as '/' and '/home'.

---

### Post by mastablasta on 2012-02-22
Again if you don't knwo how to partition - the easiest way is still to do it automatic install and then create a separate home partition:
 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
 
another option is to simply create a separate parittion let's call it data and then when you download you just tell the progs to download there instead of to /home/download

---

