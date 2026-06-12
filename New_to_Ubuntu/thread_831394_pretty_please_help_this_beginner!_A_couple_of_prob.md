---
title: "pretty please help this beginner! A couple of problems!"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Diana_Woods on 2008-06-16
Oh hi,

I posted recently about upgrading the Breezy Beaver version of ubuntu that I had installed with haste and folly from a library CD, and w/o knowing anything about linux. If only I had realized then that it was horribly out of date.

I just installed the most recent version (8) but it did not install over top of the old Ubuntu as I had expected. Instead Grub gives me the option to boot V5, V8 or Windows.

Now a lot of disk space is being used by the Ubuntu I don't want.

Ok, the other issue is with wireless. I've noticed that wireless is a tricky thing just by browsing the forums a little. I am curious is there is a way that a ubuntu program can scan for wireless connections sorta like Bonjour does in windows. That is, I often use wireless at my public library, the cafe down the street, and sometimes gank it from my neighbour. In all three cases I don't have any information about these wireless connections, aside from that fact that they are detected, unprotected and ready for me to click.

So. In a nut shell: how do I wipe my system clean of Ubuntu 5, how do I connect to unprotected wireless networks that I have no information on?

thank you thank you.

:guitar:

---

### Post by mrussell on 2008-06-16
You could remove the first install and update your boot file (menu.1st) but considering that these are fresh installs and you don't have anything invested in the data or setup I would just reinstall the latest version and this time select 'use the entire disk'.  The problem with just deleting the first install is that the partition has already been created and you'll have to work around it, which will be a pain.  I don't know of a way to eliminate that partition and merge the space into your /home partition so it will be easily usable.  

The wireless program that Ubuntu installs will scan for open wireless networks and you can just select the one you want to connect to, just like windows.  Just click on the wifi icon in the top right and it will show your networks.  If you don't see these networks, then maybe something is wrong with your wifi setup.  Wifi installation is often not as simple as with windows and can take some playing around with if you don't have a well-supported wifi chipset.  If it isn't working, search these forums by the name of your chipset and see what people have done to get it working.  You can find the chipset name by typing lshw at the system prompt and looking for the wireless info.  

Have fun!  Matt

---

### Post by sam_delta on 2008-06-16
for your wireless network, can you post the output of each of the following commands ```
lspci
iwconfig
sudo iwlist scan
``` (open applications>accessories>terminal, type the command, and post the output here)
with the output of those commands, we will be able to know which wireless adapter you have, and see if your wireless adapter is working fine/ with the current drivers. knowing which adapter you have, and if it has the correct drivers installed, we will be able to help you further

thx
sam

---

### Post by avtolle on 2008-06-16
If you want to keep Windows (and dual boot) don't select the "use entire disk" option. You will need, instead, to delete the partitions that the two versions of Ubuntu occupy, then in the installer, use the "install to largest...." option.

---

### Post by Diana_Woods on 2008-06-16
Matt, If I reinstall and use the entire disk does that mean windows will be wiped? 

I do intend to eventually get rid of Windows, but need it while I am learning to connect to the internet w/ ubuntu.

While I wait for feedback I am going to go back into ubuntu with those commands posted by Sam and see what I can make of the wireless.

---

### Post by Diana_Woods on 2008-06-16
oh ok, my question already answered, I figured windows would be cleared. I'm going to try the other method.

(sorry I don't know how to delete posts that aren't relevant)

---

### Post by Diana_Woods on 2008-06-16
When I installed Version 8 I tried to manually deal with the partitions. But I don't know how to distinguish between them. There were a great deal many of small and large partitions serving various functions unbeknownst to me... it was also asked of me to assign partitions for numerous functions like "root" etc. I was afraid to mess with it, and so opted for a "guided install" that resulted in my problem.

---

### Post by avtolle on 2008-06-16
Yes, the default in the guided partitioner would have merely installed 8.04 using the largest unallocated space, which resulted in your problem. Since you are not comfortable with manual partitioning, I need to see if I can quickly find a link to something that will help you. I'll get back with either something, or someone else will try to help, I'm sure.

---

### Post by avtolle on 2008-06-16
Before doing anything further, would you kindly post the results of ```
sudo fdisk -l
``` so we can see what is being dealt with? You will need to do this from the terminal while in Ubuntu, BTW.

---

### Post by Diana_Woods on 2008-06-16
ok, so here is what I got when I typed in sudo fdisk -l

diana@garden:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa315a315

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416   12  Compaq diagnostics
/dev/sda2   *         384        3690    26563477+   c  W95 FAT32 (LBA)
/dev/sda3            3691        7487    30499402+   f  W95 Ext'd (LBA)
/dev/sda4            7488        9729    18008865   fd  Linux raid autodetect
/dev/sda5            5046        5662     4956021    7  HPFS/NTFS
/dev/sda6            7388        7487      803218+  8e  Linux LVM
/dev/sda7   *        3691        4985    10402024+  83  Linux
/dev/sda8            4986        5045      481918+  82  Linux swap / Solaris
/dev/sda9            5663        7308    13221463+  83  Linux
/dev/sda10           7309        7387      634536   82  Linux swap / Solaris

Partition table entries are not in disk order


As for the information that sam_delta suggested I post for wireless connection help this is what I got:

diana@garden:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter


diana@garden:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

diana@garden:~$ sudo iwlist scan
[sudo] password for diana: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

---

### Post by avtolle on 2008-06-16
Moving you to the top for someone else to see, as I must go. Observation: at a minimum, the partitions labeled /dev/sda6 through /dev/sda10 need to be deleted. 

Obviously at this point, you are seeing that just wiping the whole disk and starting over is the easiest option, but since you want to keep Windows (are you really still using Windows 95?), that's not an option. Hopefully, someone else may pick up this thread and give you further assistance.

---

### Post by Diana_Woods on 2008-06-16
Thanks so much for your help. Not sure why it says 95. I am using XP

---

### Post by pawnrocket on 2008-06-16
/dev/sda5 5046 5662 4956021 7 HPFS/NTFS 

Thats your windows partition.. 

You could load the livecd and goto System/Administration/partition editor and delete everything but /dev/sda5 and the W98 partitions (I don't know what those are) 
After that reinstall and work on your wireless problems.. 

I am 100% sure that someone else will have a more elegant answer to your question, but this is what I have... 

If I were you I would wait a little while and see if anyone else comes up with something better before doing it this way. 

I would recommend however that you do a manual Partition 

Put aside 10GB for the mount point "/" root (Where your OS and system info are)

and then put the rest on your mount point "/home"  (Where your personal information is)

Just in case you have problems in the future you will always have your saved information.

---

### Post by sam_delta on 2008-06-17
for your wireless, 

do you have a wired connection????
most likeley you will need a wired connection to get the correct drivers downloaded from the internet

if you have a wired connection, plug it into your computer, and go into system>administration>hardware drivers,,, check if "broadcom wireless drivers" are listed, if they are listed, right click them and enable them, if they are not listed, post back here

sam

---

### Post by Diana_Woods on 2008-06-17
pawn rocket, I tried what you suggested. Here is what happened:

In the partition editor some partitions are "mounted" and so I am told to "unmount" before I make any changes. I can't figure out how to do that.

I tried using the manual partitioner in the installer to delete everything but the /dev/sda5 ntsf.. then using the free space to insall Ubuntu. There is a drop down list of "file allocation" mechanisms (including "FAT32, FAT16, ext3 ...") are well as the boot and the swap. After fiddling around I was not permitted to continue with the installation because of not defining a "root file system" in spite of giving everything "file allocation" option a try before pressing "forward."

That aside, I tried to assign boot a partition and every single attempt resulted in a freeze and subsequent shut-down of my machine.

My final question is: what is the SWAP aspect? What are the essentials for me to assign partitions to? I assume that all 8 or so options on the drop down menu do not require their own respective partitions and that I am supposed to choose based on a preference that I am not knowledgable enough yet to have.

so, I need to know why my computer shuts down when I try to give "boot" its place (as I assume that It is the essential part, and this is hypotheticaly how I can proceed given that no file allocation option will advance me).


Ok, on another note.

Sam:

I don't have a wired connection. Curious whether or not I can download drivers w/ my windows, put them on my flash, then get them into ubuntu?

---

### Post by MasterSander on 2008-06-17
The SWAP is a partition ubuntu uses when it has not enough RAM, it takes extra HDD space to compute (this goes slower than RAM ofc).

You need the GParted live cd to edit your partitions, it's hard to edit partitions when you are using them at that moment, isn't it?

Make a partition with mount point /  -> Here is what everything is going to be installed on (unless you want a seperate home partition, but since you're dualbooting I don't think that's extremely handy) and a partition for swap of around 1 gig HDD space. You don't need a boot partition unless you're installing different distros of linux and that partition should be very small (files don't take a lot of space), but you won't need that 'cause you're only using ubuntu. Unless you think you'll be installing an other distro in the near future. The fact that it freezes when you try to make a boot partition is somewhat weird to me as well. 

I hope this somewhat helps you out.

---

### Post by eriqjaffe on 2008-06-17
> **Diana_Woods said:**
> I don't have a wired connection. Curious whether or not I can download drivers w/ my windows, put them on my flash, then get them into ubuntu?If you can access your Windows partition from inside Ubuntu, then there's no need to go to a flash drive, but there's no reason why you **can't** go to a flash drive.

---

### Post by sam_delta on 2008-06-17
for your wireless

try post number #9 from
[http://ubuntuforums.org/showthread.php?t=766800](http://ubuntuforums.org/showthread.php?t=766800)

any error/question feel free to ask

sam

---

