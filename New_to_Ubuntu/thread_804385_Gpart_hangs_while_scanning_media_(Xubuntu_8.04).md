---
title: "Gpart hangs while scanning media (Xubuntu 8.04)"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by DesignerTrevor on 2008-05-23
Howdy,

I'm trying to install Xubuntu on an...elderly laptop of mine to give another year or two of useful life before it dies completely. It's an Averatec 3150 that has been roughly used as a computer for a traveling portrait studio that I owned for a few years. It keeps getting slower and slower under XP, so I thought an optimized OS like Xubuntu would be ideal.

However, whenever I try and run Gpart, either in the Install process from the live CD or from Xubuntu booted off the CD, it hangs. The mouse stops being capable of movement while Gpart is "Scanning media", and no keypresses do anything either.

Quick stats: Athlon XP 1600+ Processor, 512MB of PC2100 DDR RAM, a 30GB Hard Drive, which has about 5 gigs of free space. I want to remove XP in the install process, though, so that limitation shouldn't matter.

I'm completely unfamiliar with Linux, and a number of searches on Google and this forum seemed to turn up similar problems, but none that seemed to offer any solutions that I can take advantage of.

Can anyone offer me some advice for installing this? 

Your patience is much appreciated.

---

### Post by NightwishFan on 2008-05-23
Make sure you check the cd for errors. If you find none try running gparted from a terminal and see if you can notice any errors that pop up in terminal.
```
gparted
```

---

### Post by DesignerTrevor on 2008-05-23
My apologies; I forgot to mention that I'd already checked the CD for errors and it doesn't have any.

I tried to install regular Ubuntu (also checked the CD and it's fine), and it hung even earlier. I did just notice a very brief message that flashes at boot. I can't quite make it out, but it says something about missing firmware and then gives a reference to "B43/ucode5.fw" and says that I need to download it.

I'll try running Gpart from the terminal as soon as I can figure out how to get into the terminal. :P

[[EDIT: That would be under Accessories, I see. I feel a little dumb.]]

---

### Post by DesignerTrevor on 2008-05-23
So it ran successfully from the terminal, although running it from the Applications taskbar didn't work.  There's a three error messages in the terminal window, however; 

```
ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system. /dev/scd0 has been opened read only.
Unable to open /dev/scd0 read-write (Read-only file system. /dev/scd0 has been opened read only.
Unable to open /dev/scd0 - unrecognised disk label.


```

Either way, since I've got Gparted running now, I should be able to manually create a partition and be on my merry installing way, right?

---

### Post by NightwishFan on 2008-05-23
Correct. There also is a manual partitioning available in the installer itself if you so choose. If that fails, try the alternate install cd, its manual partitioner seems more effective.

---

### Post by DesignerTrevor on 2008-05-23
Well, I set my laptop to partition the drive and then went to bed for the night. It crashed while I was away. A little experimenting with it showed me that Gparted was crashing when it tried to *write* the changes to the drive, now. No further information comes from the Terminal aside from the three errors that it already gets when I start gparted.

Anyone have any idea how I can fix this so that the install will be able to proceed?

---

### Post by |Eric| on 2008-05-26
go in your Motherboard bios desable virus scannin 
(that basicaly blocks writes to MBR witch makes most install crash (including  windows)

---

