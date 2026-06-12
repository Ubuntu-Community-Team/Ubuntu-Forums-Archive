---
title: "Dual-boot problem"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by The Matt on 2012-07-06
Ok, so I'm brand new at Ubuntu, I've been knowing about it for years, but never caught the whim to try it out. After purchasing a new laptop, I decided to go for it. What I was going for was a dual booting system, Windows 7 and Ubuntu. I downloaded my ISO, burned the cd, and after a few hours of searching through help threads, and tutorials, I'm ready to go. With my old pc open so I can access a tutorial while I'm doing it. I start the process. 
Here's what I did
1. Using Windows, I repartitioned the hard drive. I created a 50 gb partition on my Windows hard drive to install on. I named it E. 
2. I start the Ubuntu install process with the Live dvd.
3. I go through the normal process, next, next, blahdeblah
4. Select the dual boot install to run Windows side by side with Ubuntu.
5. Here's where I got a bit turned around. Ubuntu asks me about partitioning, formatting, all that. I already have my partition made, but I have to set it to an XFS file system, right? XFS 2 from what I read on a tutorial. So I ?reformat? the partition and set it to be made to XFS2 
5. After that, it seems to go swimmingly, all automated, no mistakes to be made.
6. Ubuntu prompts me to restart the computer to finish the install.
7. Restart and BAM...straight...to...Windows. Hmm.
So did I format or partition wrong? I didn't want to use a third party partitioning tool, as I read I may need a Windows boot disk to repair my copy of Windows. So where do I go from here? A few hours of researching FOR the install, and an hour of researching to figure out where I went wrong is enough for me. Forgive me if there's already a thread about this, I just don't have the energy to search anymore. And I'm patting my back a little bit that I managed not to kill my Windows install in the process of this.

---

### Post by sffvba[e0rt on 2012-07-06
Could you please link to the tutorial you used? (Never heard of XFS filesystem).


404

---

### Post by The Matt on 2012-07-06
Sorry bouthat, I was going by memory, and apparently my memory was wrong. It was EXT2.

---

### Post by The Matt on 2012-07-06
Well. Good news and bad news...the good first. I managed to figure out how to get Ubuntu on my system! Now the bad news....I managed to install it right over my nice little copy of Windows. Not what I was trying to do. Anyone got a spare copy of a Windows 7 boot disk lying around? If not...I sure hope I like Ubuntu...

---

### Post by kansasnoob on 2012-07-06
> **The Matt said:**
> Well. Good news and bad news...the good first. I managed to figure out how to get Ubuntu on my system! Now the bad news....I managed to install it right over my nice little copy of Windows. Not what I was trying to do. Anyone got a spare copy of a Windows 7 boot disk lying around? If not...I sure hope I like Ubuntu...

You can't just use someone else's Win disc(s) to reinstall your Win. It doesn't work :(

Before doing anything else boot the Ubuntu live CD/USB again and post the output of:

```
sudo parted -l
```

Do not use the installed Ubuntu again until you find out what you have done!

---

### Post by kansasnoob on 2012-07-06
Since it was fairly new you should be able to contact the manufacturer for re-installation discs. You may have to pay something though.

---

### Post by sffvba[e0rt on 2012-07-06
This is one of the reasons I hate pre-installed OS's and applications without installation media :(


404

---

### Post by The Matt on 2012-07-06
Meh...it's a rent to own computer. I'm gonna check with em later.

---

### Post by kansasnoob on 2012-07-06
> **The Matt said:**
> Meh...it's a rent to own computer. I'm gonna check with em later.

Arrgh, here in Kansas those rent-to-own contracts are truly horrible. Good luck.

---

### Post by The Matt on 2012-07-06
Ok so here's my current situation. I have a Windows 7 upgrade disk. My problem is I don't have an old Windows install disk. Any suggestions?

---

### Post by zwygart on 2012-07-07
Question : Are you sure Windows 7 is erased or just not bootable? It happens often that windows is present but the bootloader didn't got it right. To be sure run any linux (live or not) and post the output of one of the tree commands after or all of them : 
sudo parted -l
sudo fdisk -l
sudo blkid

---

### Post by The Matt on 2012-07-07
Thanks, but I got it. I downloaded an ISO of Windows 7.

---

### Post by The Matt on 2012-07-07
So I'm back to my former situation...I have Windows 7 and I want a dual-booting system with Ubuntu lol. 2 days for nothing.

---

### Post by Laiquendi on 2012-07-08
You should install Win7, then install Ubuntu on another partition (prepared before or during installation), but focus not to delete windows. It happens at the beginning but you'll manage to do it eventually and not make this mistake ever again ;) AND let Ubuntu install "GRUB", it will detect both systems and let you dual-boot.

---

### Post by oldfred on 2012-07-08
Backup, make a Windows repairCD just in case, and use Windows to shrink the NTFS partition but not to create new partitions. A default side-by side install will install to the unallocated space or if you want added partitions for /home or shared NTFS data you should partition in advance with gparted.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

Installer has not changed much so these also are good:
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Paddy Landau on 2012-07-08
In addition to the previous helpful posts:

For future note, please follow the [instructions on Ubuntu's official website]("http://www.ubuntu.com/download/help/install-ubuntu-desktop"). You must have followed a very old tutorial, because we haven't used ext2 (or even ext3) for a long time. We use ext4 now. And the installer will create and format the partition for you — you don't need to do it yourself.

---

