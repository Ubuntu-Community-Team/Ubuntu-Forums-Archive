---
title: "Installing on an ext. HDD (USB)"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Gonioscope on 2012-04-26
Hi, Members, 

I want install 10.04 or 12.04 (perhaps on an USB Stick, too). How is this done and how can I create enough space for downloads, updates and software? I tried this with a stick, but could not update nor download software due to lack of storage. There was still capacity on the stick also I deleted all unnecessary software coming with 10.04, e. g. games. So I do not know whether I made a mistake or this ideas are simply not feasible. 

How to keep enough space?? When completed all this, I want use Ubuntu from HDD/Stick, connected to the USB port of a netbook. 

Thanks a lot for your hints, kind regards, 

Goni

---

### Post by c2tarun on 2012-04-26
What is the size of your USB stick?

---

### Post by Gonioscope on 2012-04-26
Size is 8GB, around 6GB left,  HDD 450 GB, 60 GB left. Installation completed with Universal USB Installer (Linux) 1.8.9.2. But using the HDD is not possible ....not bootable...perhaps there is another way.

---

### Post by oldfred on 2012-04-26
The USB installer is intended to just make a flash drive instead of a CD to use as an installer. It also is a liveCD/USB to allow you to test that your system works ok. But you can add persistence and save some data. 

But if flash drive is larger you can do a full install, which is the same whether a flash drive, external drive, or internal drive. I have a full install of 12.04 (alpha) on a 8GB partition on a 16GB flash drive to test on my laptop as I did not have enough space to test with a separate partition. Install was functional but not speedy, even with settings to reduce writes.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

On a flash drive you want to reduce writes as that is slow and may want to consider a lighter weight version as both writes & USB connection speeds are slower than a hard drive.

HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

The screen shots are older versions but the install process is the same, most install screens only have minor changes.
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?

---

### Post by Gonioscope on 2012-05-09
Dear Oldfred, 

Thanks a lot for your reply, on my netbook is Win7 and 11.10 installed, perhaps I will delete 11.10. When booting I can select between the two OSs. So what will happen, when I plugging in a HDD or USB-Stick, with 10.04 installed? With or without 11.10? Plugging it in when the book is already running or connecting the device shortly after starting the book or even before? Up to now I did not install 10.04 on a device, because I did not fully understand the procedure, but I will try it, this or next week. 

Kind regards, 
Goni

---

### Post by oldfred on 2012-05-09
My 12.04, I just updated to the release on the flash drive. It is 16GB with 8GB for data and 8GB for the install. 

I have a bunch of ISO for installing or repairing systems, so if I boot I can either boot a full system or boot an ISO (grub will loopmount and directly boot many ISO). I also store some data in the data partition as another backup. 

If you just plug it in, it is just another mount of a couple of partitions. Of course if you modify files that are required for booting from the / partition it may not boot, but you can browse (or repair if needed) the system partition or copy data to the data partition.

---

### Post by Gonioscope on 2012-05-22
Hm, enigmatic reply....as mentioned above I am a beginner, could you write something which answers my questions, please.

---

### Post by oldfred on 2012-05-22
You should be able to plug your USB flash drive in anytime. But you can only boot it from BIOS or your one time boot key.

Did you try installing yet? Examples were in links posted before.

---

### Post by Gonioscope on 2012-05-22
Hi, 
Up to now I did not dare to do this....as soon as possible I will try it. I am even in posting and all these forum stuff a beginner, really. Thanks a lot. 
 Greetings,
Goni

---

