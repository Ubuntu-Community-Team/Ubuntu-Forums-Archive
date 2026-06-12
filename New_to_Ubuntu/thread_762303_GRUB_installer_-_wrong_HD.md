---
title: "GRUB installer - wrong HD"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by soc_kev on 2008-04-22
Okay, so I have a duel boot setup with Windows/Recovery partition on one disk and I have Ubuntu on an external USB disk. The idea was to be able to boot to either system - Windows when I'm on the go with my laptop and Ubuntu when my external HD is plugged in.

Here's my problem: I installed the GRUB files to my external HD along with Ubuntu. So now the external HD **Must** be plugged in to boot my computer.
1) How do I install my GRUB files to the windows MBR? Is that possible? I want to be able to boot windows on the go when my external HD+Ubuntu is not present.

2) In an attempt to fix the above issue through the command line, I messed up GRUB further so now when I try and boot to Windows, I get a flashed screen that reads "Starting GRUB stage 2" and the cuts right back to the normal GRUB screen with the different boot options.

What's up? How do I fix this mess?

Thanks a million!
-soc_kev

---

### Post by nicedude on 2008-04-22
It is possible to fix probably but it will make a difference whether you are using Windows XP or Vista? as Vista is a little worse about playing nice with its other OS friends. So I think if you have to fix vista Master boot Record that you need to do it with vista so follow the first link if thats the case if XP go to #2 Also which version of ubuntu 32 or 64 bit? I am guessing 7.10?

Vista discussion here
Heres a post thats similar prob
[http://ubuntuforums.org/showthread.php?t=598739](http://ubuntuforums.org/showthread.php?t=598739)

heres one that should work if XP
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

another grub vista link
[http://www.neowin.net/forum/index.php?showtopic=605747](http://www.neowin.net/forum/index.php?showtopic=605747)

You might post back all your specs and look at those links

---

### Post by soc_kev on 2008-04-22
Thanks!
I'll go take a look at those links but in the mean time...

I'm running Ubuntu 7.04, 32 bit, Kernel# ...15 (as opposed to ...16, I don't remember the exact number) 
It's on an HP Pavilion dv6000 Laptop. (I've heard 7.1 has issues with the HP's hence the lower version)
I'm duel booting with Windows Vista 32 bit.

I tried installing GRUB from the command line to (hd0) which has worked in the past but for whatever reason this time, it does not. Also I should mention that GRUB will boot my recovery partition (factory installed form HP) but not the normal Vista partition. 

Thanks again,
soc_kev

---

### Post by nicedude on 2008-04-22
Hey man I have been looking around for your exact problem and nobody has it exactly like you but everybody with a similar prob seems to be either trying to reinstall grub or half claim you should use your Vista disk to redo the mbr (master boot record) Which you don't have a Vista cd because how cheap companies are they just cut 10GB off your disk instead. In the future even if you get this patched up you should install both OS on your laptop drive as you have 160gb drive so I would go something like 30GBVista (when you recover from your hdd partition for vista what size does it end up or is it interactive, )  3gb linux swap 20gb ubuntu and then make the rest a storage partition as you could still have a ton of stuff on there
and use either OS anywhere and your portable could be storage too.

Sorry but Im really good with XP & PC hardware but have only played around with vista very little as when I got my laptop with Vista & Recovery Partition like yours I put a Dban boot-n-nuke wiper disk and said bye bye to vista 5 min after powered up and got my disk space back. So I just don't like it because in my eyes its just trouble like usual but more so. I have to ask why do you need windows in the first place? ( not being mean just asking what role it fills) Ubuntu is the much safer OS against hackers and basically is immune to viruses & spyware so it just seems the more logical choice for hooking up to multiple networks or pub wifi.



OK LETS TRY THIS TO SEE WHAT HAPPENS
Open the a terminal and enter the following commands

sudo grub
root (hd0,0)
setup (hd0)
quit

You may have to modify the hard disk parameters to suit your setup. My root partition is the second on my first hard disk.



If the above doesn't work then run the commands below see what you can do but also just PM them to me and as soon as I get a chance I will try to figure this out

Command to show partitions
sudo fdisk -l

If you can boot into Ubuntu then you could see if this opens your grub config as normally it would

sudo gedit /boot/grub/menu.lst

---

### Post by soc_kev on 2008-04-22
Some points of clarification: 

I've tried working with the GRUB terminal. 
sudo grub
root (hd1,1) <- 1=external HD, 1=linux partition
setup (hd0)

This "works" as in it installs in the terminal, but when I reboot to the GRUB menu, Vista will not load. It flashes a "starting stage 2" screen and returns immediately to the GRUB screen. 
It would appear as though GRUB is not reading the Vista partition. I checked the menu.lst file and it has a section for Vista... it just doesn't read the partition.

I should mention that this was working ~1 day ago. All I did was try and reinstall GRUB (with the terminal). I did something wrong (probably installed to the wrong partition) but now when I try to reinstall GRUB normally, it doesn't access the internal HD.

Here is the output of sudo fdisk:
Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6480    52050568+   7  HPFS/NTFS
/dev/sda2            6481        7297     6562552+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       32677   262477971    c  W95 FAT32 (LBA)
/dev/sdc2   *       32678       60044   219825427+  83  Linux
/dev/sdc3           60045       60801     6080602+   5  Extended
/dev/sdc5           60045       60801     6080571   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 62 sectors/track, 926 cylinders
Units = cylinders of 15810 * 2048 = 32378880 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           4       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 2)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(3, 12, 21)
Partition 1 does not end on cylinder boundary.
/dev/sdb2               4         927    29206168    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(3, 12, 22)
Partition 2 has different physical/logical endings:
     phys=(911, 254, 62) logical=(926, 180, 59

---

### Post by Liz1948 on 2008-04-23
HELP! I have read through several threads about problems with GRUB but nothing matches my problem. I installed Ubuntu on a 2nd hd about 1 month ago. Everything was going great. I could boot into Ubuntu or XP without a problem. Suddenly today I am getting GRUB error 25. The only way I can get on is with the live cd. 
I am a *real* neophyte. I don't know where GRUB is installed; I don't know which partition is which; after all of this, I barely know my own name.
Can someone tell me a real simple way to get on my computer?
:confused:

---

### Post by annda on 2008-04-23
@Liz1948: error 25 means disk read error. it might mean your disk is damaged. can you access your disks when using the liveCD? 

usually. hard disks do not break, controllers do. are both hd's internal?

---

### Post by Liz1948 on 2008-04-23
@Liz1948: error 25 means disk read error. it might mean your disk is damaged. can you access your disks when using the liveCD?

usually. hard disks do not break, controllers do. are both hd's internal?

Both are internal. I can get into the 2nd hd where Ubuntu is installed. When I try to access the main hd, I am told "unable to mount the volume". Reason - "unclean shutdown". I shut it down this morning the same way I always do. 
It might be time to bite the bullet and take it to a computer guru. Problem is, I don't know anyone around here who is familiar with Ubuntu.
By the way, this controller is just about to break.

---

### Post by soc_kev on 2008-04-26
PROBLEM SOLVED.

Turns out, my MBR was shot and GRUB had no way of loading the windows files. I used a Vista recovery disc to fix the MBR and windows loaded right up, no problem.

From here, I will be able to set up a proper duel boot system on my internal HD thus avoiding any boot issues, e.g. not having my external HD plugged in!

Many thanks to nicedude for putting a lot of time and effort into helping me figure this one out. 
:)

---

