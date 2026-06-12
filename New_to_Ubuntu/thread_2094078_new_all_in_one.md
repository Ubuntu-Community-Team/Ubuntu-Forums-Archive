---
title: "new all in one"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by misswham on 2012-12-12
HI.  I bought an all in one last wk.  Put the usb flash with ubuntu on it and it worked fine live BUT as soon as I installed, halfway thru the installation the screen got slightly dim then all the way dark before the installation was finished.  I restarted and it installed fine BUT after 5 mins the screen went slightly dim then black and restarting didnt work, but shutting the pc totally DOWN did.  It kept on happening so i booted in windows 8 and it booted fine but went dark the same so i took it back.  I ask a guy who was a geek and he told me that the graphic cards that were in most of these new windows 8 pcs werent compatible with linux yet and i would do better getting one with an NVIDIA graphics card because that was the error message I got while trying to install.  So i just bought another pc and I am asking if you all think that the one i bought, will be compatible with most linux distros ie ubuntu or mint since i use both.   look below and give me ur opinion please.

Hi there. Had trouble with mint and graphic cards on other all in ones i purchased but a geek at bestbuy told me that the graphic cards in most windows 8 pcs are intel and they dont work yet with LINUX. They told me to get one with NVIDIA. They are hard to find but i bought one today. I have listed the specs below and can someone tell me if they think that linux will work fine with dual booting with windows 7 on this system WITHOUT messing it up with the installation?

Key Specifications

Vizio All-in-One CA24-A2

24-inch Full HD LED-backlit display (1920 x 1080 pixels)

2.3 GHz Intel Core i7-3610QM quad-core processor (3.3 GHz with Turbo Boost Technology; 6 MB L3 cache)

1 TB SATA hard drive (5400 RPM)

8 GB of installed DDR3 RAM (maximum capacity)

NVIDIA GeForce GT 640M LE graphics with 1 GB of video RAM superior graphics performance on multimedia applications

---

### Post by Calinou on 2012-12-12
It should work fine (we all know NVIDIA always does!). However, there's a good chance your computer has 4 primary MS-DOS partitions, this means you'll have to remove the recovery partitions before setting up dualboot.

---

### Post by chadk5utc on 2012-12-12
Ok IMHO if you can use the PC with the live cd then there is a compatible driver that will work with Linux. While running the live cd try to figure out which modules are loaded for it and get what info you can. You might try checking the hardware specs against the linux HCL.

---

### Post by oldfred on 2012-12-12
Actually the geek was wrong. 

The Intel drivers do work for most systems. Some seem to have issues, but many have issues with whatever you have. 
Very new systems are less supported as the vendors rarely write drivers for Linux and they all have to be reversed engineered after release.

If a new Windows 8 system you have UEFI. Or was this an older model with Windows 7? With UEFI you need to use 12.10 64 bit and boot the installed in UEFI mode not BIOS/legacy mode. IF Windows 7 we need to know which mode it is installed in as it could be BIOS or UEFI.

       Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

    
Post this from liveCD:
       sudo parted /dev/sda unit s print

---

### Post by misswham on 2012-12-27
Im trying to install and i got this screen that asks.

The installer has detected that the following disks have mounted partitions

/dev/sdc

Do you wnat the installer to try to unmount the partitions on these disks before continuing?

I hit yes but when i tried to install besides windows 7, it wont let me move the line over to get more space. What should I do?


I went back and hit no and it would let me move the bar 2 partition but i didnt go further because i wanted 2 wait 2 see if thats what im supposed to click. It said by pressing no that I wouldnt be able to resize the partition but that function let me move the bar TO resize, I just dont know whats going to happen afterwards if I click continue,

---

### Post by oldfred on 2012-12-27
Without knowning more about your system, we cannot suggest much.

Post for every drive, since you seem to have several. sda, sdb, sdc or how many you have.

sudo parted /dev/sda unit s print

---

