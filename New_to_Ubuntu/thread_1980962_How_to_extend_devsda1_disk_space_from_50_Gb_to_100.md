---
title: "How to extend /dev/sda1 disk space from 50 Gb to 100GB"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by GuruPrasad123 on 2012-05-16
Hi, I am new to Ubuntu 11.04.

I created a vm with Ubuntu 11.04 OS.

allocated disk space of 50 GB. But now, i want to increase the disk space of sda1 from 50 GB to 100GB.

So what are the steps to do that.

Please help me to extend disk space..

Thanks In advance:popcorn:

---

### Post by codemaniac on 2012-05-16
IF you are using virtualBox ,
Open a terminal and navigate to the folder with the VirtualBox disk image, then use the following command .
```
VBoxManage modifyhd YOUR_HARD_DISK.vdi --resize SIZE_IN_MB 
```

---

### Post by GuruPrasad123 on 2012-05-16
I dont have virtualBox installed.

How can i do?

---

### Post by codemaniac on 2012-05-16
> **GuruPrasad123 said:**
> I created a vm with Ubuntu 11.04 OS.


Then what  virtualization software you are running ?

---

### Post by GuruPrasad123 on 2012-05-16
vmware tools(vcenter,ESX).

I can increase the disk space through vm settings. but it is not reflecting (if i enter df -h , showing old disk space values).

After adding more GBs through vm settings, what commands i need  to run ?

---

### Post by codemaniac on 2012-05-16
> **GuruPrasad123 said:**
> vmware tools(vcenter,ESX).

I can increase the disk space through vm settings. but it is not reflecting (if i enter df -h , showing old disk space values).

After adding more GBs through vm settings, what commands i need  to run ?

Sorry i have not used VMWARE before , but folks out here can surely come up with some solutions .

Cheers and best of luck !!

---

### Post by GuruPrasad123 on 2012-05-16
Thanks Robert.

Yes I hope someone from ur group will help me..

---

### Post by drmrgd on 2012-05-16
> **GuruPrasad123 said:**
> vmware tools(vcenter,ESX).

I can increase the disk space through vm settings. but it is not reflecting (if i enter df -h , showing old disk space values).

After adding more GBs through vm settings, what commands i need  to run ?

I think the issue is that you've increased the maximum allowed size of the system, but the partitions are still the same size and need to be increased. I believe that this can be done using gparted.  I would recommend first making a copy of your current Ubuntu virtual machine folder just in case something goes wrong (assuming you have space on your harddrive).

First shutdown your virtual machine.  Then find the .ISO that you used to install Ubuntu in the virtual machine, and choose to boot from that image (just as you did when you first installed it).  Choose the Try Ubuntu option, and once the OS is up and running, launch gparted.  You should now see the partitions that you set up when you first installed Ubuntu, and you should see a whole bunch of unallocated space (50Gb if I'm not mistaken).  Just increase the size of your partition to include that unallocated space (this might take a while), and once it's completed, reboot to your Ubuntu installation and you should be good to go.

Hope that helps.

---

