---
title: "HOWTO: Asus z96s"
date: 2008-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by hoborgowski on 2008-03-24
Hello there. I just bought a new shiny Asus z96s laptop. After many long battles I managed to install full-working **Ubuntu 8.04 Hardy beta**.
I didn't make notes during my struggles with the configuration, but I tried to rewrite everything that I remembered. I hope that my instructions will help you make your hardware working. The onboard devices are:

Intel Core 2 Duo CPU
TOSHIBA MK1646GSX SATA2 Hard Drive (with Intel ICH6 Controller)
nVidia GeForce 8600 GS
MATSHITA DVD-RAM UJ-850S
RTL8169sc/8110sc ethernet card
Intel Wireless WiFi 4965AGN
Intel HDA Audio
Syntek AVStream USB2.0 1.3M WebCam

Fine. Let's get started then :)

[FONT="Arial Black"]1. Partitioning[/FONT]

**1.1 Problems with windows partitions**
The first thing I'd like to mention is a problem with windows installer detecting free disk space. If you install windows xp / vista first, you probably won't encounter any particular difficulties. If, however you choose to install Ubuntu first and leave some free space in the partition manager during installation, you may run into trouble. When I tried to install windows after Ubuntu, I was suddenly stopped by a message saying that &#8222;windows installer cannot detect any hard drives&#8221;. After switching from AHCI to IDE in Bios I was able to detect the space that I prepared for windows but the installer refused to use it, even after creating a suitable partition. The reason was simple : windows installer was able only to create a logical partition in that space...
Anyway, unless you feel super familiar with partitioning, primary and logical partitions and all that stuff, you better install windows first. If you of course want to.

**1.2 Distribution of disk space**
This is, of course, your individual decision. There are many different opinions on how to choose partitions and filesystems wisely. My final choice was pretty simple (160 GB):

windows 	30 GB
/		15 GB
/tmp		1 GB
swap	1.5 GB
/home	all the rest

For linux partitions I chose ext3.
If you want to use hibernation then you better set more swap size, at least the amount of your RAM.

[FONT="Arial Black"]2.Devices[/FONT]
Not all the devices were properly installed with the default 2.6.24-12-generic kernel. After downloading and compiling a newer one (2.6.24.3) even more of them stopped to respond ;)
Here is a list of kernel modules that I had to build in or attach as compiled modules to make all the internal devices working.

**2.1 Bluetooth**
To make my bluetooth running fine I had to do these two things:

Compile the kernel with :
[*] Networking--->Bluetooth Subsystem Support
(a corresponding entry in kernel .config file wold be BT=y)

Add *bluetooth* to /etc/modules.conf

Finally, install gnome-bluetooth tool to enable the file transfer function:
```
sudo aptitude install gnome-bluetooth
```

**2.2 WiFi**
Do following changes to your linux kernel configuration:

[*] Device Drivers--->Network Device Support--->Wireless LAN ---> Intel Wireless WiFi Link Drivers
(iwlwifi=y)

[M] Device Drivers--->Network Device Support--->Wireless LAN ---> Intel Wireless WiFi 4965AGN
(iwl4965=m)

and append * iwl4965* to /etc/modules.conf

Finally, use apt-get to download and install *iwlwifi-firmwar*e. You may need to add proper repositories to /etc/apt/sources.list

*Note: if you want to configure WPA encryption, don't use spaces in the passphrase.*

**2.3 Camera**

Follow all the instructions from 
[http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html](http://www.zer0.net/2007/12/asus-syntek-webcam-installation-on.html).

Don't forget to append
```
option stk11xx vflip=1
```
to /etc/modules.d/options because without that your camera output will be flipped upside-down.

**2.4 Graphic Card**
First make sure, that these two kernel modules are disabled:

Device Drivers--->Graphics support--->Support for frame buffer devices--->nVidia Framebuffer Support
[fb_nvidia=n]

Device Drivers--->Graphics support--->Support for frame buffer devices--->nVidia Riva Support
[fb_riva=n]

Download nVidia Geforce 8600 GS driver installer for linux from [www.nvidia.com](www.nvidia.com). Before running it you may need to download some additional packages like *gcc* or *make*. You also have to close Xorg. If you have trouble with shutting down gdm, enter recovery mode from grub.
If the installer cannot find kernel source tree, make sure that you have downloaded and unpacked linux-sources and linux-headers matching your currently running kernel.
After installing the nVidia driver you should agree to let it modify the /etc/X11/xorg.conf file. Now start Gnome. If you want to check if everything is ok, try typing 
```
glxinfo | grep direct 
```
from the console. If you see 'direct rendering : yes' and your screen resolution seems to be 1200x800, then your GeForce was installed properly.
Note: If you want to watch all the divx / xvid / rmvb stuff without any problems, use apt to install *smplayer* and then install the following package:
[http://rapidshare.com/files/70388050/w32codecs_20061022-0medibuntu1_build1_i386.deb.html](http://rapidshare.com/files/70388050/w32codecs_20061022-0medibuntu1_build1_i386.deb.html)
by typing
```
dpkg -i w32codecs_20061022-0medibuntu1_build1_i386.deb
```

**2.5 Sound Card**
When configuring the kernel, go to 
Device Drivers--->Sound--->Advanced Linux Sound Architecture--->PCI Devices--->Intel HD Audio
and check [*] that option along with other related ones.

**2.6 Other devices**
You may also want to add these two modules:

Device drivers > Misc Devices --> Asus laptop extras
[asus_laptop=m]
Device Drivers ---> Serial ATA (prod) and Paralell ---> Intel ESB, ICH, PIIX2, PIIX4 PATA / SATA support
[ata_piix=m]

and add
```
asus_laptop
ata_piix
```
to /etc/modules

If you have 4GB of RAM or more, you need also to select:

Processor type and features--->High Memory Support--->64 GB
[HIGHMEM64=y]

Yes. 4GB needs 64GB support to be selected.

As for the internal dial-up modem, I don't need it at all so excuse me but I can't explain how to install it. The SD card readers and other subsystems (Core 2 Duo processor, Realtek ethernet card) seemed to work automatically without any problems.

---

