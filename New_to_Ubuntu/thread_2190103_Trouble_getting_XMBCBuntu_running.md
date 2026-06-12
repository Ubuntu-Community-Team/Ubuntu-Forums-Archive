---
title: "Trouble getting XMBCBuntu running"
date: 2013-11-25
forum: New to Ubuntu
---

### Post by Photobug on 2013-11-25
I have an HTPC I purchased from some guy pre-built and am trying to get it up and running using XBMC on Ubuntu.  Initially the previous owner had a USB drive running a version of XBMC.  I added Aeon nox to it to update the Interface look.  Now I am unable to access the settings and therefore unable to add more add-ons to the system.  This boot does work but I can not access settings and therefore can not load 3rd party add-ons like BlueCop.

So I am trying to add a fresh installed XBMC thumb drive so I can start from scratch.  I have tried Linux Live to create an install disk and then using it to create a USB drive on my HTPC.  There is no GPU on this setup but a built in GPU in the MOBO, so I am not sure if it is an Nvidia or AMD GPU so I have tried both variations of the Ubuntu install without success.  It loads the second thumb drive then crashes soon after restart.   I am trying to boot XBMCBuntu-Intel-Nivida and -AMD.

I would appreciate any suggestions on how to get the original install so I can access settings or how to get my new install to work?

---

### Post by DuckHook on 2013-11-26
Your posting is very confusing. Not meant as a rebuke, but it helps us to help you if you take the time to explain the problem clearly and in detail. Examples: I do not run XBMC, so do not know what Aeon nox is, nor BlueCop. You mention a USB drive but give no other system specs. Does your box have a HDD at all? SDD? How do you boot? Though custom-built, you must know its CPU and RAM? At least whether Intel or AMD? What version are you running? Which version did you download from Linux Live? Please provide full system architecture. But if you really don't know, don't worry, as there are commands that can be run to find out.

Since your current install does boot, do <Ctrl>+<Alt>+<t> to launch a terminal. If this doesn't work in XBMC, do <Ctrl>+<Alt>+<F1> to get to a new console. Login if necessary and then do:```
lspci -vk | grep -iA15 vga
```This will tell you what video chipset you are using and the current driver. Post this info back to this thread.

Hopefully a forum member with XBMC experience will jump in to help. If not, perhaps we can muddle through anyway.

---

### Post by Photobug on 2013-11-26
> **DuckHook said:**
> Your posting is very confusing. Not meant as a rebuke, but it helps us to help you if you take the time to explain the problem clearly and in detail. Examples: I do not run XBMC, so do not know what Aeon nox is, nor BlueCop. 

Thanks DH for chiming in and letting me know how confusing my post was.  I will try to better explain my setup and issues.

After many tries at different configurations I have managed to get a version of XBMC up and running in a limited capacity though.  I honestly did not know the total configuration of this computer as I bought it used and I only had a rough idea of whats inside.  Now that I have this up and running here are the stats for my computer from the System Summary info in XBMC, let me know if any more details are needed.

Free memory: 3807 MB
OS: Linux 3.5.0-22-generic #34-Ubuntu smp

Storage looks like the OS uses a little more than 2GB leaving me 26 GB for add-ons

Video GPU: Mesa DIR Sandybridge Desktop x86/mmx/sse2

Open GL: Intel version 3.0 mesa 9.0

CPU Intel Core I5-2400 @3.1 GHz
speed 1600MHz

There is no HDD onboard.  The previous owner ran it off a 32GB thumb drive and I'd like to do the same for now.  One reason is it will allow me to play with and configure different flash drives and experiment with different systems while I try to use XBMC and other Linux OSs.  I may put an HD in later but once up and running I will be using it only to run music and videos to my Stereo and TV.  All storage will be on a separate server.

Aeon Nox is a skin or GUI, it corrupted my last install so I reformatted that thumb drive.  I tried using my other computer running Windows 7 and using Linux Live USB creator to create flash drive running XBMCBuntu 12.2.  With this I tried to run the computer on the "Try XBMC" and "Install XBMC" modes.  The first just runs the OS off the flash drive the second mode installs XBMC on a HD or in this case another flash drive I have installed.  I tried many times to run these two modes and both caused a crash on bootup.

I then tried the same thing with XBMCBuntu 12.0 and am able to only run it under "Try XBMC" mode.  At least it is up and running but any configurations changes or add-ons I add are not useable after adding and are not still there after a reboot.  So I would really like to be able to get a flash drive so the system is permanently installed so I can make configuration changes and install add-ons.  I am willing to try other methods besides Live Linux but it needs to be done from a Windows 7 PC.  

Thanks

---

### Post by DuckHook on 2013-11-27
Since yesterday, I've downloaded XBMCbuntu and tried to install it in a VM only to discover that it is extremely picky about its video subsystem and expects either an Intel, NVidia or AMD GPU. Since VMs emulate graphics that are none of the above, I can't get XBMCbuntu to run in my VM. However, I did discover that you can choose Ubuntu DE at login, so that we can eliminate at least one unknown.

I was hoping that an XBMC guru might have stepped in by now, but I guess they are all off watching their content!

Okay, back to your difficulties. It should not be hard to use Linux on one stick and install it on another. What you need to know is the Linux conventions for:

1. Finding block devices (which include HDDs and USB sticks) in the system,
2. Mounting them to mount points,
3. Installing to those mount points.

Also, it would be nice to know the exact graphical system that you have. Your new info is much more helpful, but running System Summary does not give the actual chipset details--only the general architecture (Sandybridge) and driver (Mesa). If we want to look for a video driver that may be more suitable, we need to know your actual video chipset details.

I'm afraid that you won't be able to avoid the command line. First make sure that all USB sticks including the empty one that you want to install to are plugged in. Reboot. After booting, do not choose XBMC or XBMCbuntu. Instead choose a standard Ubuntu DE, open a terminal, do the following, and post output of these commands back to this thread.```
lspci -vk | grep -iA15 vga
``````
sudo blkid
``````
sudo parted -l
``````
df -h
``````
lsusb
```Commands such as these tend to get mistyped all the time and even a single difference won't work. I would recommend that you actually cut and paste the commands into the terminal, then cut and paste the output back to this thread. Wrap the output in "code" markers (the # in the edit box) to help us read them properly.

---

### Post by Photobug on 2013-11-28
> **DuckHook said:**
> 

Also, it would be nice to know the exact graphical system that you have. Your new info is much more helpful, but running System Summary does not give the actual chipset details--only the general architecture (Sandybridge) and driver (Mesa). If we want to look for a video driver that may be more suitable, we need to know your actual video chipset details.

I am pretty sure I am running an Nvidia Graphics Card built into the Motherboard.  The reason why I assume this is the only OS I have been able to run in the XBMCBuntu 12.0 Nvidia.  Is there a way to do a hardware check of my system without running any OS?



I'm afraid that you won't be able to avoid the command line. First make sure that all USB sticks including the empty one that you want to install to are plugged in. Reboot. After booting, do not choose XBMC or XBMCbuntu. Instead choose a standard Ubuntu DE, open a terminal, do the following, and post output of these commands back to this thread..

I am unable to get only an Ubuntu OS running.  My only options showing with the startup is try or install.  Also when I look into the LinuxLive website it shows a list of compatible OSs it works with and the only XBMCBuntu it shows is the XBMCBuntu 12.0 AMD. Since I need the Nvidia, I am SOL?

I am willing to try a unique upload of Ubuntu to just get an OS running so i can run the commands you suggest.  Is there an Ubuntu build you suggest I run?  Or is there another way to create a USB OS disk other than LinuxLive?

---

### Post by squakie on 2013-11-28
My suggestion:  use another PC - a friends' or family memebers', install unetbootin.  Run unetbootin and select the OS (scroll down to Ubuntu) and the version (like maybe 12.04) using your USB flash stick.  This will build a "normal" Ubuntu live media you can boot from on the PC and select try, then open the terminal and type the commands Duckhook has suggested.  Please don't assume it's nVidia unless there is something you aren't telling us - the summary you posted doesn't indicate that.

Please do that and using that live session just cut and paste  back all of the results as requested.

PS:  xmbc is available and runs in "normal" Ubuntu.  You would need to create persistence (the ability to "remember" things across boots) when using unetbootin - with a 32gb flash drive I'd suggest everything you can get -> perhaps 28 gig (I don't know how much room Ubuntu takes on the flash drive).  Then you can install XBMC itself to Ubuntu and give it a try.  You don't need just XBMCuntu - just normal Ubuntu.

EDIT:  you can search the forum via the "search" box and/or search the web - there are plenty of instructions out there for actually running Ubuntu from a flash drive.

---

### Post by DuckHook on 2013-11-28
> **Photobug said:**
> I am unable to get only an Ubuntu OS running. My only options showing with the startup is try or install.Hmmm... okay. My experience was only with the installed system on a virtual machine--did not note the restrictions on LiveDVD. I can't believe that it is impossible to bring up a terminal in XBMC, but perhaps it's better not to waste time poking around trying. With my limited knowledge, I'm afraid that you are being led by a blind man.>  Also when I look into the LinuxLive website it shows a list of compatible OSs it works with and the only XBMCBuntu it shows is the XBMCBuntu 12.0 AMD. Since I need the Nvidia, I am SOL?The Mesa driver leads me to believe that your box actually has an Intel GPU. NVidia would have loaded "Nouveau" and AMD/ATI would have loaded "Radeon". At least, that's how it works on Ubuntu. Don't know enough about XBMCbuntu. The difficulty is that Mesa sometimes is used for very old ATI and NVidias as well as oddballs that are somewhat also-rans in the GPU sweepstakes these days. It doesn't sound like your system is one of those, though one never knows.> I am willing to try a unique upload of Ubuntu to just get an OS running so i can run the commands you suggest. Is there an Ubuntu build you suggest I run? Or is there another way to create a USB OS disk other than LinuxLive?Now, there's a thought. It's a shame to have to delve into the guts of Ubuntu just to get a content machine running, but if you have the time and the inclination... it can also be educational. XBMC is nothing more than an alternate desktop environment anyway. As I understand it, it's designed to hide the complexity of the real OS and just present a pretty front end with a simplified set of options that can be selected through a remote. Many users just load Ubuntu first and install XBMC from the repositories. You might want to consider this option too.

There's nothing wrong with using Linux Live. It's a great little project that makes it that much easier for Windows users to discover the ups and downs of Linux. Once the OS is burned onto a USB/DVD then, for all intents and purposes, Windows is no longer in the picture, you are dealing with a pure Linux environment and we should be on firmer ground. I would recommend that you use Linux Live again and burn a copy of Ubuntu 12.04. Don't be fooled by the older release date. 12.04 is a long term release which means that it is solid, stable and will be supported until 2017. XBMC should run very well on top of such a solid foundation.

Once you get a Live environment running, it should not be difficult to proceed from there.

EDIT

Didn't see squakie's post till just now. Yes, that is another option.

---

### Post by squakie on 2013-11-28
*IF* XBMCuntu is acting like the other stand-alone XBMC installs, the only way to get a terminal is to ssh to it.

---

### Post by howefield on 2013-11-28
If you can ssh into your xbmc install, try editing the .xbmc/userdata/guisettings.xml file. You'll need to scroll down to the look and feel section... the default confluence skin will look like the screenshot. Edit, save ect.

---

### Post by Photobug on 2013-11-28
I really would like to get something like Ubuntu up and running.  I had bought the Ubuntu book 3 years ago and had an Ubuntu run ruining in side windows.
I wish I had it now because my W7 laptop just started crashing today to the point I can only run it in safe mode.  Priority one get an Ubuntu running on all my computers.
For now I have made progress with the XBMC: I started it up made some changes in settings. I then accessed a video I had burned to a thumb drive, and am watching it now.  
I will try to get at another computer to get an Ubuntu thumb drive running.
What is SSH?

---

### Post by Photobug on 2013-11-29
[FONT=Garamond][SIZE=3][FONT=Garamond][SIZE=3]I opened up the computer to get all the info I could.  It was buried in a TV cabinet and a pain to get to.  During this process I plugged in the BlueRay player and added a 250 and 500GB hard drives.  The Mobo is a 
[/SIZE][/FONT][/SIZE][/FONT]                                      GA-H67MA-UD2H-B3                     (rev. 1.1)                   

                                               
                                                   Intel[SUP]®[/SUP] H67 Chipset  

  

                                                                                     
                              
[LIST]
[*]Supports Intel new B3 stepping 6 series chipset 
[*]Supports the newest LGA1155 Intel[SUP]®[/SUP] Core&#8482; processors 
[*]Innovative 8 phase power VRM design for optimum power efficiency 
[*]Ultra Durable 3 Technology with copper cooled quality for lower working temperature 
[*]Hi-def 108dB Signal-to-noise ratio Blu-ray&#8482; DVD audio playback 
[*]GIGABYTE 3x USB Power with On/Off Charge USB ports 
[*]Supports USB 3.0 with superfast transfer rates of up to 5 Gbps 
[*]High speed SATA3 storage interface with superfast 6Gbps link speed 
[*]CrossFireX support for ultimate graphics performance 
[*]HDMI/ DVI/ DisplayPort interface for smoother HD video playback 
[*]Enhanced Intel HD Graphics 2000/3000 integrated with the processor 
[*]XHD technology accelerating hard drive performance with ease 
[*]Innovative Smart 6 technology for smarter PC management 
[*]Hybrid EFI technology with DualBIOS for 3TB HDD support 
[/LIST]
             
[FONT=Garamond][SIZE=3][FONT=Garamond][SIZE=3]
I then took my other computer and Unetbootin-ed a USB drive with Ubuntu 12.04.  I first tried to get it onto one of the HDDs.  This install does not work.  So I just booted from the thumb drive.  I was able to get this info from it, using the terminal mode.

If I can get Ubuntu running like I want I may not need to even get XBMC working.  One issue I am having now is screen resolution.  My output from the computer is going through an Onkyo receiver so the computer thinks that is its output.  Right now the screen resolution is such that the Icons from the Ubuntu OS is off the screen on the left the only way I can get to them is run the mouse pointer down the left side and see what pops up.  Also I would like to get a flash compatible browser so I can run Hulu and amazon prime. 
Here are the results of the Ubuntu testubuntu@ubuntu:~$[COLOR=#40e0d0] lspci -vk | grep -iA15 vga[/COLOR]
00:02.0  VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09) (prog-if 00  [VGA controller])
    Subsystem: Giga-byte Technology Device d000
    Flags: bus master, fast devsel, latency 0, IRQ 47
    Memory at fb800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at ff00 [SIZE=64]
    [SIZE=2]Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Giga-byte Technology Device 1c3a
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at fbfff000 (64-bit, non-prefetchable) 
    Capabilities: <access denied>[/SIZE][/SIZE][/FONT][SIZE=64][SIZE=2]ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="4a3fd7fa-843b-ee4c-9fe6-98799cbc6978" TYPE="ext2" 
/dev/sda1: LABEL="New Volume" UUID="E6A8C25CA8C22ABF" TYPE="ntfs" 
/dev/sdb1: UUID="5941c5a0-c14b-4329-abb0-0beb76b44026" TYPE="ext4" 
/dev/sdb5: UUID="a863dd9f-f8b6-4052-9158-6a176952f3e3" TYPE="swap" 
/dev/sdg1: UUID="4450-F9B5" TYPE="vfat" 
/dev/sdg5: UUID="90c7f89b-271a-4d92-8cac-d7c39c622b6c" TYPE="swap"[/SIZE] 

[FONT=Garamond][SIZE=3]ubuntu@ubuntu:~$ [COLOR=#40e0d0]sudo blkid[/COLOR]
/dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="4a3fd7fa-843b-ee4c-9fe6-98799cbc6978" TYPE="ext2" 
/dev/sda1: LABEL="New Volume" UUID="E6A8C25CA8C22ABF" TYPE="ntfs" 
/dev/sdb1: UUID="5941c5a0-c14b-4329-abb0-0beb76b44026" TYPE="ext4" 
/dev/sdb5: UUID="a863dd9f-f8b6-4052-9158-6a176952f3e3" TYPE="swap" 
/dev/sdg1: UUID="4450-F9B5" TYPE="vfat" 
/dev/sdg5: UUID="90c7f89b-271a-4d92-8cac-d7c39c622b6c" TYPE="swap" 
ubuntu@ubuntu:~$ ^C
[/SIZE][/FONT][SIZE=2]
ubuntu@ubuntu:~$ [COLOR=#40e0d0]sudo parted -l[/COLOR]
Model: ATA WDC WD5000AAKS-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ntfs         boot


Model: ATA WDC WD2500KS-00M (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  246GB  246GB   primary   ext4
 2      246GB   250GB  4207MB  extended
 5      246GB   250GB  4207MB  logical   linux-swap(v1)


Model:  Patriot Memory (scsi)
Disk /dev/sdg: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  26.8GB  26.8GB  primary   fat32           boot, lba
 2      26.8GB  31.0GB  4206MB  extended
 5      26.8GB  31.0GB  4206MB  logical   linux-swap(v1)


ubuntu@ubuntu:~$[COLOR=#40e0d0] df -h[/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
/cow            1.6G  515M  957M  35% /
udev            2.0G   12K  2.0G   1% /dev
tmpfs           792M  976K  791M   1% /run
/dev/sdg1        25G  2.3G   23G  10% /cdrom
/dev/loop0      676M  676M     0 100% /rofs
tmpfs           2.0G   16K  2.0G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   80K  2.0G   1% /run/shm

ubuntu@ubuntu:~$[COLOR=#40e0d0] lsusb[/COLOR]
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 13fe:4100 Kingston Technology Company Inc. 
Bus 002 Device 004: ID 15c2:0038 SoundGraph Inc. GD01 MX LCD Display/IR Receiver
Bus 001 Device 005: ID 046d:c525 Logitech, Inc. MX Revolution Cordless Mouse
Bus 001 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
ubuntu@ubuntu:~$ [/SIZE][/SIZE][/FONT]

---

### Post by DuckHook on 2013-11-29
> **Photobug said:**
> I opened up the computer to get all the info I could. It was buried in a TV cabinet and a pain to get to. During this process I plugged in the BlueRay player and added a 250 and 500GB hard drives. The Mobo is a
GA-H67MA-UD2H-B3 (rev. 1.1)


    Intel® H67 Chipset



    Supports Intel new B3 stepping 6 series chipset
    Supports the newest LGA1155 Intel® Core&#8482; processors
    Innovative 8 phase power VRM design for optimum power efficiency
    Ultra Durable 3 Technology with copper cooled quality for lower working temperature
    Hi-def 108dB Signal-to-noise ratio Blu-ray&#8482; DVD audio playback
    GIGABYTE 3x USB Power with On/Off Charge USB ports
    Supports USB 3.0 with superfast transfer rates of up to 5 Gbps
    High speed SATA3 storage interface with superfast 6Gbps link speed
    CrossFireX support for ultimate graphics performance
    HDMI/ DVI/ DisplayPort interface for smoother HD video playback
    Enhanced Intel HD Graphics 2000/3000 integrated with the processor
    XHD technology accelerating hard drive performance with ease
    Innovative Smart 6 technology for smarter PC management
    Hybrid EFI technology with DualBIOS for 3TB HDD support

I then took my other computer and Unetbootin-ed a USB drive with Ubuntu 12.04. I first tried to get it onto one of the HDDs. This install does not work. So I just booted from the thumb drive. I was able to get this info from it, using the terminal mode.

If I can get Ubuntu running like I want I may not need to even get XBMC working. One issue I am having now is screen resolution. My output from the computer is going through an Onkyo receiver so the computer thinks that is its output. Right now the screen resolution is such that the Icons from the Ubuntu OS is off the screen on the left the only way I can get to them is run the mouse pointer down the left side and see what pops up. Also I would like to get a flash compatible browser so I can run Hulu and amazon prime.
Here are the results of the Ubuntu test
```
ubuntu@ubuntu:~$ lspci -vk | grep -iA15 vga
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
Subsystem: Giga-byte Technology Device d000
Flags: bus master, fast devsel, latency 0, IRQ 47
Memory at fb800000 (64-bit, non-prefetchable) [size=4M]
Memory at e0000000 (64-bit, prefetchable) [size=256M]
I/O ports at ff00
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: i915
Kernel modules: i915
``````
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="4a3fd7fa-843b-ee4c-9fe6-98799cbc6978" TYPE="ext2"
/dev/sda1: LABEL="New Volume" UUID="E6A8C25CA8C22ABF" TYPE="ntfs"
/dev/sdb1: UUID="5941c5a0-c14b-4329-abb0-0beb76b44026" TYPE="ext4"
/dev/sdb5: UUID="a863dd9f-f8b6-4052-9158-6a176952f3e3" TYPE="swap"
/dev/sdg1: UUID="4450-F9B5" TYPE="vfat"
/dev/sdg5: UUID="90c7f89b-271a-4d92-8cac-d7c39c622b6c" TYPE="swap"
```

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKS-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 500GB 500GB primary ntfs boot


Model: ATA WDC WD2500KS-00M (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 246GB 246GB primary ext4
2 246GB 250GB 4207MB extended
5 246GB 250GB 4207MB logical linux-swap(v1)


Model: Patriot Memory (scsi)
Disk /dev/sdg: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 1049kB 26.8GB 26.8GB primary fat32 boot, lba
2 26.8GB 31.0GB 4206MB extended
5 26.8GB 31.0GB 4206MB logical linux-swap(v1)
```

```
ubuntu@ubuntu:~$ df -h
Filesystem Size Used Avail Use% Mounted on
/cow 1.6G 515M 957M 35% /
udev 2.0G 12K 2.0G 1% /dev
tmpfs 792M 976K 791M 1% /run
/dev/sdg1 25G 2.3G 23G 10% /cdrom
/dev/loop0 676M 676M 0 100% /rofs
tmpfs 2.0G 16K 2.0G 1% /tmp
none 5.0M 0 5.0M 0% /run/lock
none 2.0G 80K 2.0G 1% /run/shm
```

```
ubuntu@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05e3:0716 Genesys Logic, Inc. USB 2.0 Multislot Card Reader/Writer
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 003: ID 13fe:4100 Kingston Technology Company Inc.
Bus 002 Device 004: ID 15c2:0038 SoundGraph Inc. GD01 MX LCD Display/IR Receiver
Bus 001 Device 005: ID 046d:c525 Logitech, Inc. MX Revolution Cordless Mouse
Bus 001 Device 006: ID 046d:c52b Logitech, Inc. Unifying Receiver
```

You must have inadvertently turned your font sizing into super large characters. Only you or the mods can correct your original posting, but I've reposted your output into code tags for my own easier reading. Will parse through later tonight and respond.

---

### Post by DuckHook on 2013-11-29
First things first. The edges of your desktop are extending beyond your display likely because you are outputting to a HDTV. HDTVs are often defaulted to a legacy setting called "overscan". Overscan is designed to blow the picture up by a few extra pixels on each side to hide irritating edge artifacts that were sometimes inadvertently broadcast in the old days. This is not consequential in a TV broadcast where you don't miss what you can't see, but when the TV is used as a monitor, it pushes the edges of your desktop out of sight. Most TVs have a menu setting that turns off overscan. Not everyone calls it overscan and different vendors call it different things, so you will have to look for technically synonymous terms. On my Sharp, it's called dot-for-dot.

From now on let's call the machine you purchased as an XBMC box the "XBMC".
Let's call your Windows computer "Windows".
Now you have an additional BlueRay player. Unless it's plugged into the XBMC, let's not mention it again, as it is irrelevant to getting XBMC working and is just confusing. If it is instead a BD drive and *is* now plugged into XBMC, then please correct my understanding.

You've added two HDDs to XBMC. One is 250GB and the other is 500GB.

You then successfully installed an image of Ubuntu 12.04 onto a USB stick and tried to install Ubuntu onto XBMC. You say that the install did not work, but please also describe how it failed.

You are now running XBMC using the LiveUSB stick, ran the requested commands and posted the resulting output.

First, some system info for you:

You have an integrated Intel video chip in XBMC. This is a video chip that is integrated into your CPU. You have neither a NVidia nor AMD/ATI video card, but an Intel. The driver that the LiveUSB session is running is i915. Once the permanent system is installed, do not be surprised if the driver changes to Mesa.

Both of your new HDDs are showing up and Ubuntu can see them. However, your first HDD, the 500GB disk, is formatted as NTFS. Ubuntu's native filesystem is ext4, and it cannot install onto an NTFS formatted disk. However, it does look like Ubuntu may have successfully installed onto your second HDD, the 250 GB disk. I suspect that you unknowingly chose the second disk during the installation process and Ubuntu installed both its operating system and its bootloader there. But because your BIOS is set up to boot from the first HDD (which has neither operating system nor bootloader), the XBMC BIOS cannot find an OS and it looks to you like the install failed. This is just a conjecture at this point. Your description of how the install failed will either confirm or deny my guesses.

The rest of your system looks fine.

***Recommended courses of action***

1. Go into your BIOS and change the boot order of your HDDs. Choose the smaller HDD to boot first. If my above guess is correct, then you may already have an operating system on XBMC and simply telling it to boot from the proper drive may be all you need to solve the problem. If this doesn't work, then

2. Try the install again. But this time, when the installation program gets to the part where it asks you how you would like to partition the disk, pause and pay attention to the following:

A. You will be able to choose from two disks. One will be called "sda" and the other "sdb"
B. Make sure you choose "sda"
C. Then choose "Use Whole Disk".
D. The partition program will warn you that this will erase all data on the drive and are you sure. Choose "yes".

Let the installation proceed to completion, reboot when it tells you to, and let us know how it goes.

---

### Post by Photobug on 2013-11-30
I am not sure why the big font, I just copied and pasted, I went back and fixed it so that others aren't shocked by the huge font up in their face.


> **DuckHook said:**
> First things first. The edges of your desktop are extending beyond your display likely because you are outputting to a HDTV. HDTVs are often defaulted to a legacy setting called "overscan". Overscan is designed to blow the picture up by a few extra pixels on each side to hide irritating edge artifacts that were sometimes inadvertently broadcast in the old days. This is not consequential in a TV broadcast where you don't miss what you can't see, but when the TV is used as a monitor, it pushes the edges of your desktop out of sight. Most TVs have a menu setting that turns off overscan. Not everyone calls it overscan and different vendors call it different things, so you will have to look for technically synonymous terms. On my Sharp, it's called dot-for-.
Now you have an additional BlueRay player. Unless it's plugged into the XBMC, let's not mention it again, as it is irrelevant to getting XBMC working and is just confusing. If it is instead a BD drive and *is* now plugged into XBMC, then please correct my understanding.

You've added two HDDs to XBMC. One is 250GB and the other is 500GB.

You then successfully installed an image of Ubuntu 12.04 onto a USB stick and tried to install Ubuntu onto XBMC. You say that the install did not work, but please also describe how it failed.



I found the formating to get my screen right, between the Onkyo receiver the output passes through the computer itself and the TV there are many different formating options, and I finally tracked it down.  I had some weird formatting on both my HDDs and reformatted them on the WIndows computer, probably both were NTFS and the 250GB was formatted properly when the Ubuntu was attempted to be installed.  The BD device is actually a BD drive that was in the computer but was not powered or attached to the MOBO.  It now is along side the two HDDs. 


[QUOTE=DuckHook;
A. You will be able to choose from two disks. One will be called "sda" and the other "sdb"
B. Make sure you choose "sda"
C. Then choose "Use Whole Disk".
D. The partition program will warn you that this will erase all data on the drive and are you sure. Choose "yes".

Let the installation proceed to completion, reboot when it tells you to, and let us know how it goes.[/QUOTE]

I have changed the boot order and when booting without a USB drive it freezes at "booting OS"
I initially tried to re-install from the thumb drive to the HDD and this failed near the begining of the install then proceeded to boot up from the thumb drive.  From the Livedisk booted Ubuntu I was able to run a full install of Ubuntu to the HDD without failure.  However when i restart itdoes fail to boot from the HDD.  It only boots from the LiveUSB disk.  There was no option for SDA or SDB.  I will continue to dabble to see what i can come up with.

---

### Post by Photobug on 2013-11-30
Latest test results.

I tried to reconfigure the USB placements on the Mobo to make the 250 GB HDD #1 then double checked it was first in the BIOS, no success. Then I unplugged the 500 GB HDD, double checked the BIOS, and still could not get the Boot to go past "LOADING OPERATING SYSTEM".  I restarted with the USB stick in and tried "Boot from first hard drive"
It started out a string of large fonted code white letters on a black screen followed by a second screen of smaller fonted code then stopped with the option to type "help" for comand options

---

### Post by DuckHook on 2013-11-30
> **Photobug said:**
> ...It started out a string of large fonted code white letters on a black screen followed by a second screen of smaller fonted code then stopped with the option to type "help" for comand optionsAll of these results point to GRUB loading but then not being able to find a proper operating system. Now that the NTFS HDD is unplugged it should no longer be visible to the system. Please try installing again using all of the defaults during the install and selecting "Use Whole Disk" during partitioning.

---

### Post by Photobug on 2013-11-30
I tried to install from the thumb drive but ran into a fatal error.  So it is started up a boot from the Thumb drive and am now trying to use that to install.  I will let you know how it goes.

---

### Post by Photobug on 2013-11-30
Success.  I have it installed onto the Hard drive now.

Now I have to go back and remember how to do all the updates and settings changes I made to the USB drive version of the OS to get the new OS to work as well as the USB one.

One problem I am having is the downloading of Codecs.  I am running the "restricted" update that downloads all the needed things for MP3 and Flash, or so I hope.  I had just gotten the built in Blueray player to play videos on the thumb drive OS when I got the HDD to load the OS.  Is there a tutorial to setup 12.04 for the first time?  When I go to download things like Codecs it says I need to choose an application to do so, what should I choose and how do I go about dragging codecs into my Ubuntu HDD setup?

---

### Post by DuckHook on 2013-11-30
This is very good news!

I was starting to think that yours was one of those 'cursed' installs where everything that can go wrong goes wrong. But now that you have it installed, you have the luxury of time to get things right.

My first and most important piece of advice for a new install always is to not do crazy things to destabilize it. You should update it, but then it is better to live with certain constraints for a short time (like slow open-source video drivers) than to try changing everything all at once and end up with a broken system again. This forum is an excellent resource for tweaking your system methodically, one tweak at a time.

It is hard to do any better than the following sites for learning how to use Ubuntu and I highly recommend them:

Firstly, and especially for Windows users new to Linux, "Linux is not Windows" intro:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

General Ubuntu Intro:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

"Owlcroft" is old and hasn't been updated in a long time, but is still good for the basics:

[http://owlcroft.com/ubuntu/](http://owlcroft.com/ubuntu/)

An easy and safe resource for doing your first tweaks is:

[https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

Last, but not least, the general Ubuntu help site is amazing. I recommend it last only because it tends to be a little overwhelming for new users:

[https://help.ubuntu.com/community/ExternalGuides](https://help.ubuntu.com/community/ExternalGuides)

The ultimate objective is to get your box working well in its original goal as a content deliverer using XBMC. The members of this forum would be happy to help you get there. Only now, you have the added option of a usable Ubuntu system for exploration, utility and troubleshooting. Well done and Happy Ubuntuing!

---

### Post by DuckHook on 2013-11-30
> **Photobug said:**
>  When I go to download things like Codecs it says I need to choose an application to do so, what should I choose and how do I go about dragging codecs into my Ubuntu HDD setup?In Linux, these are not downloaded from outside. Most are contained in the repositories. If you go through the *Psychocats* website, it will provide very good instructions about how to install these codecs. *easylinuxtipsproject* also has instructions. If you use very oddball codecs, then it is sometimes necessary to install them from vendor sites. This is usually discouraged because it is awfully risky to go outside of the repositories for software—avoidance of which is one of the simple but very effective reasons that Linux does not need antivirus plugging up its guts.

---

### Post by Photobug on 2013-11-30
> **DuckHook said:**
> In Linux, these are not downloaded from outside. Most are contained in the repositories. If you go through the *Psychocats* website, it will provide very good instructions about how to install these codecs. *easylinuxtipsproject* also has instructions. If you use very oddball codecs, then it is sometimes necessary to install them from vendor sites. This is usually discouraged because it is awfully risky to go outside of the repositories for software—avoidance of which is one of the simple but very effective reasons that Linux does not need antivirus plugging up its guts.

It was actually a Firefox issue. I found threads online of people having issue with Firefox not giving Linux a clew as to what to do with any files.

When I tied the link using Chrome the links I clicked on opened Ubuntu Software Center to install the Codecs.

So far I have installed the restricted package to add codecs and Flash capacity.  I am able to watch Hulu and Amazon Prime videos which I had yet figured out on my previous OS configuration, but on the previous OS setup I was able to watch the BlueRay player using VLC player and now it won't run a DVD at all.

---

### Post by Photobug on 2013-11-30
A quick search brought me back to an Ubuntu Forum and this code

[COLOR=#000000]sudo /usr/share/doc/libdvdread4/install-css.sh

Problem solved or at least I got a Blueray player Hulu and Amazon Prime player out of my Ubuntu computer.  I am out of town for 4 days, so I can read up and get ready to install XBMC when I get back.[/COLOR]

---

