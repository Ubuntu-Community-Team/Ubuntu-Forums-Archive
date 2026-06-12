---
title: "execute commands to autorun with usb stick"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by DanADaMan on 2013-04-29
I bought a unique linux PC/setup, used to run a commercial application. The PC doesn't even have a typical keyboard and instead uses a custom control panel. Upon turning it on, it runs numerous scripts and eventually loads its custom application.   

I want to make some changes, but don't know a thing about linux. So I removed the drive, plugged it into my Windows laptop (via usb to sata) and then used EXT2FSD to read the drive. Found that it had 8 partitions, with the first being a Swap partition and the other 7 have either Ext2 or Ext3 file systems.

I confirmed that the bios is setup to execute a usb drive before the harddrive. I want to create a usb drive which has a Bin (executable) file that basically does the following steps:

#1 - uncompress Linux - I think this is needed cause when you boot the PC now that is the first step is does? Anyone know where or how I can find the linux OS on one of the 8 partitions. Or do I need to point to the kernel and if so how do I find it and what command is needed to "uncompress" linux

#2 - execute a bin file found on the root of partition4. Assume file is called Start.bin on root of partition4 - what command is needed to execute that? 

Being that I do not have a linux pc, I want to create this small Bin file through my Windows laptop. Any idea on how I do that?

Also I believe there are numerous different Linux OS, Ubuntu just being one.  By looking at the drive, is there any way for me to find out which I have (is there a certain file name that would let me know)?


Thanks

---

