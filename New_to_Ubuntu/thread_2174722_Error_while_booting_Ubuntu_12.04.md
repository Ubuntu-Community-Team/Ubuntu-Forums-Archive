---
title: "Error while booting Ubuntu 12.04"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-09-15
Here's what I have for hardware...
Gigabyte 970A-D3 Rev 3.0 motherboard
NVidia GeForce GTX 650 Ti Boost video/graphics card
AMD FX 6300 Six Core Processor
32gb of RAM(4x8gb sticks) Corsair Vengence
Asus DVD/Blu-Ray
1tb Hard Drive "00RKKA0"(With Windows 7 Professional)
1tb Hard Drive "07ZF5A0"(With Ubuntu 12.04 Precise Pangolin)
75gb Hard Drive "00FLA1"(No OS)

I have had this error happen a couple of times when booting Ubuntu.  I have to turn my PC off when it happens.

What is causing this error and how can I fix it?

---

### Post by fireflower on 2013-09-16
The word "kernel" worries me. Did you check the integrity of the Ubuntu iso with md5check before you installed it? Have you been able to successfully boot Ubuntu at all? Does this same error happen every time you try to boot it? What kind of RAID configuration are the hard drives in? What can you tell us about your BIOS settings?

---

### Post by ImTroyMiller on 2013-09-16
Yes, I checked the md5sum and they matched the sum that is in the file on Ubuntu.com.  The ISO was downloaded from Ubuntu.com

Yes, Ubuntu boots fine the majority of the time, it was just these two times that I got this error.

No RAID configs.

I had to choose the IOMMU option in BIOS to boot Ubuntu with working USB ports.  Without it, only two USB ports work.

One thing I haven't tried yet, is unplugging my 3D emitter for my Nvidia 3D glasses.  That's the only hardware haven't configured in Ubuntu.

---

### Post by mtron2 on 2013-09-16
Hello! 

I have also seen this error once a quite long time ago. In my case the krenel couldn't find the files in /boot because my BIOS of that time could only see the first  130GB of my harddrive and my /boot files ended  up past that point. But since you have a very new mainboard (and your Bios is up to date?) i guess that there might be a grub configuration problem.

A workaround you could try is to check if your Ubuntu partition on the second 1TB HDD is  within the first 130GB of the disk. (via the gnome disk-utility or the gparted program) and that grub uses UUID's to map the partitions instead of the device nodes like /dev/sda. 

So i suggest to run the boot-info [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) script and post your RESULTS.txt so we can exclude grub as "known suspect" ;)

---

### Post by ImTroyMiller on 2013-09-16
This video shows an error I get when I run my Ubuntu Disk Repair disk...

[http://www.youtube.com/watch?v=ZqL2-OuUPxA](http://www.youtube.com/watch?v=ZqL2-OuUPxA)

---

### Post by ImTroyMiller on 2013-09-17
This error always happens when I run my Ubuntu Repair disk.

---

### Post by Mephisto Pheles on 2013-09-17
NVidea Gforce on my box requires nvidia drivers, the nouveau drivers will give me the result you posted: kernel panic. Even the Ubuntu install disk crashes on me with this kernel panic warning.

---

### Post by ImTroyMiller on 2013-09-18
Is there any possible way for me to run my Ubuntu Repair disk?

---

### Post by fireflower on 2013-09-18
> **ImTroyMiller said:**
> Ubuntu boots fine the majority of the time, it was just these two times that I got this error. To be quite honest, after wrestling with computers of one OS or another for 20 years, this doesn't strike me as a real problem. It's just one of those mysteries of the machine spirits. If an error arises, and you restart, and it vanishes in a puff of ones and zeroes, thank the Omnissiah and go about your day.

---

### Post by Easy Limits on 2013-09-18
You might try running a Memtest on your RAM and see if you are getting any errors there.  I have had nothing but problems with my Corsair RAM.

---

### Post by fireflower on 2013-09-18
> **Easy Limits said:**
> Memtest This is a good idea. It's really any RAM that is suspect, not just Corsair. The business  model for RAM manufacturers simply does not allow for enough time to check every sector of  every stick. It's cheaper for them if you do their quality control for  them. You buy the ram, it doesn't work, you send it back, they send you a  replacement, and you're out some postage.

---

### Post by ImTroyMiller on 2013-09-21
My RAM is good.  Tested fine.

---

