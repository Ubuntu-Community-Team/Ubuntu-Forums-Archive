---
title: "Cannot install Ubuntu 15.04 due to failure to mount a file system with the type vfat"
date: 2015-08-25
forum: New to Ubuntu
---

### Post by Jason_Lexow on 2015-08-25
I recently (yesterday) decided that I wanted to dual-boot Ubuntu alongside Windows 7 on my main 1TB drive. Everything was going fine until I hit the partitioning menu. I'm trying to use 3 partitions, all of which are primary partitions since I haven't figured out how to change 2 of them to logical drives. Does that matter or not? I selected my main 20GB partition as an Ext4 journaling file system with mount point / and my second 8GB partition as another Ext4 system with mount point /home. The last 2GB partition I set as swap area, and I then selected my 1TB HDD (which also has Windows 7 on it) as the device for the boot loader installation. I then pressed install now and continue when it when it asked me whether or not to format the partitions.

It proceeded to give me an error message that says "The attempt to mount a file system with the type vfat in SCSI2 (0,0,0), partition #1 (sdb) at /boot/efi failed. You may resume partitioning from the partitioning menu." Could someone help me with this? Preferably in simple terms since I'm pretty new to this. I'm no stranger to Windows or building computers but for me this is a whole new territory.

---

### Post by grahammechanical on 2015-08-25
How many hard drives do you have? Perhaps you can use a Windows utility to examine the hard drives partition and take a screenshot and add it to your post. I ask for this because I am a little confused.

You speak of wanting to use 3 primary partitions for Ubuntu. And also having Windows 7 on the same disk. If you have a msdos partition table on the hard disk then you are limited to 4 primary partitions. And I would be surprised if Windows 7 was only using one Primary partition. If on the other hand you have GPT (GUID Partition Table) then you can have as many a 128 partitions but we do not speak of Primary or Logical partitions.

And then there is the error message. VFAT is a Microsoft partition format that allows the use of long file names. But at partition #1 (sdb) = a second hard disk. and at /boot/efi. Why have /boot/efi unless you have a UEFI boot system instead of a BIOS boot system. Please show us a screenshot.

Regards.

---

### Post by TheFu on 2015-08-25
Or just post the output from **sudo parted -l**. THAT would be most helpful.

---

### Post by Jason_Lexow on 2015-08-26
I apparently fixed the issue myself without any problems. I had a hunch that it was connected to the amount of hard drives and partitions I had connected so I disconnected every one but my SSD. It installed without a hitch. Thanks for the help anyways guys! This is a great forum =)

My guess is that the installer got confused by the amount of hard drives and partitions I had and couldn't locate my Windows 7 on my hard drive, which might have cause some conflict with the installation. The reason I think this is because I used the same USB stick to install Ubuntu on my mother's computer and it had no problems with that.

---

### Post by sandyd on 2015-08-26
Hi, if you have found a solution to your problem, please mark this thread as solved by going to Thread Tools -> Mark Thread as Solved.

Thanks!

---

