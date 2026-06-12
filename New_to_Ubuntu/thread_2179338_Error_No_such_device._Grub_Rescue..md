---
title: "Error: No such device. Grub Rescue."
date: 2013-10-07
forum: New to Ubuntu
---

### Post by Fysikeren on 2013-10-07
I recently bought a used computer from work but without any hard disks - fortunately I had a couple of old ones lying around that I could use. Unfortunately I seem to be unable to start any of them up - one greets me with the message

error: no such device: dc1baca5-4220-4d44-a31e-08a8c3d3c4d6
grub rescue>

whereas the other one gets stuck at the same point but only shows a small blinking line in the upper left corner instead of the error message. I have tried booting from a 12.04 LiveCD but for some reason it does not work - it just returns to the same screen(s). I have checked the cables and everything seems to be connected correctly (and I hear the disk spinning when trying to boot from the CD).

Running a 'ls' on the harddisk which gets to the grub rescue reveals (hd0) and (hd0,1) but it seems unresponsive to all other commands I could think of (saw some threads suggesting commands such as 'sudo fdisk -l' but both 'sudo' and 'fdisk' seem to be unknown commands.

Unfortunately I do not recall how the hard disks were set up earlier but they might have been in raid and dual booting Ubuntu and Windows XP.

Any suggestions as to how I should proceed from here? My own are basically just limited to trying (yet) another hard disk and burning a new LiveCD (although I recently used the disk for my laptop). Unfortunately I do not have another computer to test the hard disks in.

My knowledge of Ubuntu is very limited so there might as well be something obvious I am overlooking.

---

### Post by whitesmith on 2013-10-07
> **Fysikeren said:**
> I have tried booting from a 12.04 LiveCD but for some reason it does not work - it just returns to the same screen(s). I have checked the cables and everything seems to be connected correctly (and I hear the disk spinning when trying to boot from the CD)Live CD should work on a computer with sufficient RAM even if it has no HDDs at all. My suggestion is to run the memory checking utility on GRUB to see if bad memory is the problem. Resolve that issue, and then we'll go on to the HDDs. You need to post info about this box: make and model, RAM, etc. We can't work with things we don't fully understand.

---

### Post by DuckHook on 2013-10-07
You are going about finding a solution in generally the right way. Obviously you have Googled, gone through old threads, etc. You mention "old computer": is especially important to provide system specs. Everything you can think of and more.  Type/make/model, CPU, amount of DRAM, Video Card, amount of VRAM, type/make/model of HDD (IDE, SATA, SCSI?), how you partitioned, etc. You mention that the old disks may have been dual-booting. Are you trying to do same? If so, does XP work? If you want to try LiveDVD again, I recommend a torrent download of a lighter flavour--either Xubuntu or Lubuntu--torrent for better reliability, and lighter flavour for better chance of working with old HW. But without more physical specs, don't really know where to go.

---

### Post by ant2 on 2013-10-07
When you tried booting from the live CD did you check the boot order in the BIOS was set to boot from the CD first?

---

### Post by Fysikeren on 2013-10-08
Okay, so a few technical details and some A&Qs:
[FONT=arial]
[/FONT]> **DuckHook said:**
>  You mention "old computer": is especially important to provide system specs. Everything you can think of and more. 
[FONT=arial]
The computer is a 8x PC HP Workstation xw4400, Intel Core2 6700 CPU, dual core, 2.66 GHz, 4 GB RAM with [/FONT][FONT=arial]NVIDIA Graphics Card with 8600GT or 8600GTS GPU. The HDDs are Seagate SATA 500 GB, I do not remember how they were partitioned (they have been lying in a box for several years) and this time around I am simply trying to get one of them running (i.e. no raid, right now only one system and I have not been able to change anything about the partitioning). I have tried with a Windows 8.1 boot from a USB stick but it does not work (the motherboard might possibly be too old to boot from USB from startup?). If additional details are needed I can try to peek inside the box when I get home.

I will try to get my hands on some new DVDs to boot from (a LiveDVD and Windows 8.1) within the next couple of days.

[/FONT]> **ant2 said:**
> When you tried booting from the live CD did you check the boot order in the BIOS was set to boot from the CD first?[FONT=arial]

The boot order should be correct as I specifically set it to boot from the CD first.

[/FONT]> **whitesmith said:**
>  My suggestion is to run the memory checking utility on GRUB to see if bad memory is the problem.
[FONT=arial]
How do I run the memory checking utility on GRUB? Googling this did not make me much smarter (references to something called memtest86+ but it seems this has to be installed somehow?).

Thanks for the help so far[/FONT]

---

### Post by DuckHook on 2013-10-08
Your box is powerful enough to run whatever flavour of 'buntu you choose. The graphics card may be a tad light, but it should still run fine and without problems. The rest of your system also seems mainstream, so this means that we can eliminate choice of OS as a factor. Feel free to run whatever you like.

When physical stuff looks okay, but both LiveDVD and installation to two different drives don't work, my first suspicion is: corrupted install disk.

I suggest that you throw your old install disk away, download another ISO image, but this time using torrent (which is more accurate due to dynamic error correction), and do a DVD integrity check. Instructions for integrity check are [here]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck"). Torrent download is [here]("http://www.ubuntu.com/download/alternative-downloads"). Make sure you choose 64-bit Desktop (not "alternate" which won't boot into LiveDVD).

Then run a LiveDVD session to see if it works. It is also remotely possible that your DVD drive may be wonky in which case, burn a LiveUSB and try that instead. The key is to download an image that you can be sure of.

If none of this works, we will have to try diagnosing other causes.

---

### Post by ant2 on 2013-10-08
Did you burn the disk image onto the DVD [correctly]("http://askubuntu.com/questions/172570/how-to-create-a-livecd-livedvd-liveusb")? and not simply copy the the ISO file onto a DVD as data?

I apologize if I'm telling you how to suck eggs.

---

### Post by Fysikeren on 2013-10-09
> **DuckHook said:**
>  I suggest that you throw your old install disk away, download another ISO image, but this time using torrent (which is more accurate due to dynamic error correction), and do a DVD integrity check. Instructions for integrity check are [here]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck"). Torrent download is [here]("http://www.ubuntu.com/download/alternative-downloads"). Make sure you choose 64-bit Desktop (not "alternate" which won't boot into LiveDVD). 

I have burned a new LiveDVD (and a Windows DVD) and it did indeed work - well, at least it fixed the problem mentioned above. Unfortunately I still cannot install Ubuntu due to some other error (Windows said that I lack a partition driver, Ubuntu said something like 'fatal error' regarding the choice of partitions) but I will make a new thread for that if I have not figured it out in a few days time.

I suspect that the error was either with the CD, the CD/DVD drive or the number of bits (but I think a 32-bit - the prior disk was a 32-bit CD, the new ones 64-bit DVDs.

Thanks for all the help guys!

P.S.@ant2: Eliminating the most obvious sources of errors is always a sounds strategy. In burning the new disks I did indeed make the error of just burning the ISO in one case (but caught it as soon as I inspected the disc). Also, I do not know how to suck eggs - we usually blow them but I expect it is just running in reverse ;).

---

