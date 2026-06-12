---
title: "Messed up Partition after Ubuntu 11.10 Install"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by hdnewbie on 2012-05-17
Hello, I am an absolute beginner, and will be evident by the way I installed Ubuntu for the first time. It seems I can no longer access my Windows 7 installation, and I cannot locate it off my harddrive partition as I must have done it wrong. 

Here is some information:
I have a HP Pavilion Dv4 Laptop with Windows 7 64bit. 
My harddrive information from a bootinfoscript run is attached.
Ubuntu 11.10 is installed
I have a 500 GB harddrive, and I used 20GB for the partition for Ubuntu. I installed Ubuntu off of a live USB.


I do not have access to my recovery disks, and I tried going through the HP recovery setup by pressing f11 during startup right when it shows me the hp logo, but the screen flickers and Ubuntu soon loads. I can still access the BIOS. I loading something on GParted to see if I could access my computers recovery partition, but I didn't really know what I was doing, and there didn't seem to be anything evident of a recovery partition anyhow.

Any help would be much appreciated, thank you.

Please also let me know if there is any other script or program I should run to elucidate anything else.

---

### Post by Vereinfachen on 2012-05-17
I looked at your file. It seems like instead of making the Windows partition smaller and creating a small partition for Ubuntu you removed every partition in the hard drive (including your HP recovery partition) and from that empty space made a small Ubuntu partition. So everything got deleted. I am no expert on data recovery, so don't do anything yet and wait for someone here to tell you how to recover some of your files. There are special tools for that.

---

### Post by hdnewbie on 2012-05-17
Well this just got interesting. 

Thanks for your reply, I look forward to anyone with expertise in this.

---

### Post by Vereinfachen on 2012-05-17
You shouldn't be so relaxed about it, all your data is gone. :X
Did you have important data on your windows installation?

---

### Post by wilee-nilee on 2012-05-17
> **hdnewbie said:**
> Well this just got interesting. 

Thanks for your reply, I look forward to anyone with expertise in this.

At this point if you want to recover anything do not use that HD, use a live cd or usb thumb. Testdisk is commonly suggested on the forum for recovery, let someone who is experienced help here.

Not sure if you had any images of the installs, in other words clones, but if you do or had any all you would have to do is slip them back in. Personally I use clonezilla for this but it is a text cloner that is fairly simple once you know it, but there many free imagers that have a nice gui.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by westie457 on 2012-05-17
First the bad news. Everything that was on the hard drive has gone. There is virtually no chance of recovering anything at all. Any files that can be recovered might well come out mangled.

Now this is where it could get interesting if you are up for the challenge.

Stop using that hard drive, for the moment do your computing using a Live Desktop. You can check here what we are about to try.
 [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Whilst using the Live Desktop open a terminal, (easy way is press Ctrl+Alt+T at the same time). In the terminal type in ```
sudo apt-get install testdisk
```

When that has finished type in ```
sudo testdisk
```
Follow the prompts on the screen. We are going to attempt to recover the partitions that were on your hard drive before it was formatted.

If the hunt for the partitions is unsuccessful there is also a small chance of recovering individual files which is a time-consuming,laborious, frustrating and boring job. For that you will need another hard drive with a lot of empty space on it to write all recovered files to.

As stated at the start 'there is every chance that the files have gone'

---

