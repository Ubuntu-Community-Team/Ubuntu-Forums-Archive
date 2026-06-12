---
title: "Should I set up partitions?"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by GpD79 on 2011-10-15
I'm brand new to Ubuntu. I was going to install 11.04 a week or two ago, because I got a brand new computer but decided to wait because I saw that 11.10 was soon on its way! Now that it's here, I have a few questions for how to install Ubuntu along side Windows.[LIST=1]
[*]Does anyone feel that Ubuntu 11.10 is stable enough to install or should I still go with 11.04 since I'm a newbie?
[*]Should I set up partitions in windows prior to starting? Also, how much space should I allocate for Windows 7 and for Ubuntu?
[*]Finally, will files created while using Windows 7, such as videos and music, available to use in Ubuntu?
[/LIST]In case you need to know what kind of machine I am running, here is a rundown:
 
1 2nd generation Intel Core i7-2630QM processor 2.00 GHz with Turbo Boost 2.0 up to 2.90 GHz
1 6GB,DDR3,2 DIMM
1 Backlit Internal Keyboard - English
1 15.6HD TLF WLED LCD L50xX
1 NVIDIA GeForce GT 525M 1GB graphics with Optimus
1 750GB 7200 RPM SATA Hard Drive
1 Genuine Windows 7 Home Premium 64 bit Service Pack 1, English, No Media
1 Tray Load Blu-ray Triple Writer (reads and writes CDs, DVDs, BDs)
1 JBL 2.1 Speakers with Waves Maxx Audio 3
1 Intel Centrino Wireless-N 1030 and Bluetooth 3.0
1 90 WHr 9-cell Lithium Ion Primary Battery
1 Microsoft Office 2010 Home and Student, English
1 2.0MP HD webcam with single digital mic (H.264)
1 Mini DisplayPort (1),
2 USB 3.0
1 USB 2.0 (eSATA/powershare combo)
1 Integrated network connector 10/100/1000 LAN (RJ45)
1 HDMI 1.4
1 Audio jacks: headphone (2 total) with SPID/F support (1), 1 Mic-in
1 9-in-1 media card reader Supporting SD, SDIO, SDXC, SDHC, MS, MS Pro, MMC, MSXC, xD
 
 
Any help anyone can provide would be greatly appreciated!

---

### Post by mcduck on 2011-10-15
1. Some will say no, other will say yes, the truth is that the only way to find out how stable it is on *your* computer and with the programs you use is to try it yourself. :)

2. You should resize your Windows 7 partition in Windows, leaving the space you intend to use for Ubuntu as unallocated unpartitioned space. That way you can simply tell Ubuntu's installer to use the unallocated space, and it will set up Linux partitions automatically for you. Windows wouldn't be able to set them up anyway. 

How much space you want really depends on your personal needs, how much programs you want to install in each OS and how much personal files you want to store.

3. Yes, you can access your Windows files from Ubuntu. Trying to work the other way doesn't work, though, as Windows only has support for it's own file systems. So in case you want to move files from Ubuntu to Windows you'll either have to do it from Ubuntu, or set up a shared partition which both are able to read.

---

### Post by jmate24 on 2011-10-15
just install 11.04 don't install 11.10 yet there still are bugs and it is less feature rich in my opinion plus if you upgrade it uninstalls a lot of your favourite apps.

and yes you can install Ubuntu alongside Windows 7 but if Windows crashes (BSOD for example) and you have to use your recovery disk then the recovery disk will either wipe out Ubuntu in favour of getting Windows back to it's original state when you bought the computer or it will wipe out the grub boot files. The best way to go is to do a clean install of Ubuntu on that type of pc. if you have more than one hard drive and you want to RAID (Redundant array of Independent Disks) then you will have to get the alternate install .ISO from [http://releases.ubuntu.com]("http://releases.ubuntu.com") 

By the way: I like to build my own computers instead of buying them from the 'BIG-BOX' stores I can get what I want at a price I can afford and they last 2-3 times as long. And cheaper than the box stores. mine was $500 US and it has an AMD Athlon XII 640 3.0 GHz Processor a 750GB HDD 8GB RAM 3 SATA DVD-RAM drives 1 500W Power supply an Apple wired keyboard (Apple blue-tooth is not guaranteed to work with other blue-tooth receivers other than apple) and i have a free 21" flatscreen and a $2 mouse..

if you have any more questions you can pm me as well.

good luck

---

### Post by GpD79 on 2011-10-15
Thanks guys for your help.  I don't think I am going to do a clean install because when I spoke to the salesman on the phone, who was an avid linux user, he stated that I should install Ubuntu alongside Windows 7. He said that if I clean install Ubuntu, I will no longer be able to get support from Dell since they're not trained on it. He said it would be a good failsafe because in case hardware went bad, they would be able to check it via Windows 7. That seems to make sense to me.  
 
So, if I were to intsall alongside, how do I resize the partitions in windows 7?  As for how much space I should allocate, I don't think I will use Windows 7 much.  I just want it to be functional.   The rest can go to Ubuntu.  Does anyone have any what would be an appropriate allocation of space just to ensure that Windows 7 still works?  Do people usually just guess?
 
jmate24 - I wish I could of built my own computer, but I've never done anything like that before, so I'm afraid of messing it up.  Also, I don't like desktops.  My apartment is small and they take up too much space.  I've never heard of anyone building their own laptops.

---

### Post by patC42 on 2011-10-15
Presumably you have 11.4 on a Disk.
If you start your computer from the CD then you will be able to start Gparted to access the windows partition and resize it.

When you install 11.4 it will give you the option of Install alongside the windows partition. Use free space. Or something else

---

