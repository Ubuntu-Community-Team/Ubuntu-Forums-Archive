---
title: "Problem asscessing Hard-drive with xubuntu on a flash drive"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by slam81 on 2012-11-10
Hi, so new at this so please be patient with my description,

I have an Acer U46E-Rals5 laptop in which I had kept in standby for a while. However i saw an windows error which forced me to reboot, however Windows 7 would not load properly and just end up stalling. I tried to get into safe mode or use the last secure version of the OS, but the laptop would just stall on booting up. 

Not wanting to wipe the harddrive as yet, I removed my internal drive(WD 750GB ATA)  and hooked it up via usb to another laptop running xp. The other laptop would not recognize my laptop drive and it would peroidically crash/freeze windows explorer and just tell me that the drive needed to be formatted. 

Anyway still not wanting to do as yet, I managed to connect the internal drive via usb to a mac, and i was able to salvage most of my critical files, however accessing the drive was slow and not all of the content was showing in a particular folder (ie. it only showed 3 items when i knew there were over 100 in that folder). 

Anyway I was able to go make a bootable flash drive of linux running xubuntu,(from ubootnet.sourceforge.net) and was able to boot up the laptop, however I cannot access the harddrive after it is mounted the error that is displayed is as follows 

Failed to open directory 'OS'
error when getting information for file/media/OS/.fseventsd: input/output error

keep in mind the system does see how big the drive is, and how much free space there is on it. 

I would very much like to recovery all of my files and then wipe the harddrive or is this indicative of a complete hard drive failure? Would greatly appreciate any assistance
Thx

---

### Post by newb85 on 2012-11-10
Welcome!

You seem to have two objectives:
[list]
[*]Accessing your data
[*]Determining the health of your HDD.
[/list]

For the first objective, let's get some information about how much Xubuntu knows about your drive and partitions.  In a terminal (open with Ctrl+Alt+T), issue the following commands one-at-a-time and post the results of each here.
```
sudo lshw -C disk
sudo lshw -C volume
```

---

