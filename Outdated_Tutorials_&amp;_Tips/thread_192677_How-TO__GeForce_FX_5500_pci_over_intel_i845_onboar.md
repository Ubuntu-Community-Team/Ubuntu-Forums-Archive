---
title: "How-TO : GeForce FX 5500 pci over intel i845 onboard graphics"
date: 2006-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by lf82 on 2006-06-09
This how-to saved my life. 
Could be usefull for anybody having intel integrated graphics on their motherboard and thinking of upgrading their video card using the PCI slot.

Orginaly posted by mstralka:

Wow, I finally got my NVIDIA GeForce FX 5500 PCI to work properly. My PC has onboard Intel 845GV graphics so whenever I tried to switch to the NVIDIA, my computer would freeze on bootup at the hotplug section. Even though I disabled the onboard graphics in the BIOS, agpgart would still try to load the onboard graphics instead of my NVIDIA. After beating my head against the wall for 2 days, here's what I did to finally make it work. Please note this may not work for everyone.

Here's my system:
Ubuntu 5.04
Kernel: 2.6.10-5-686
Compaq SR1210NX
512 mb Ram
Intel Celeron D 330 - 2.66 GHZ, 256kb L2 Cache, 533 Mhz FSB
80 GB Hard drive
[http://h10025.www1.hp.com/ewfrf/wc/d...name=c00063244](http://h10025.www1.hp.com/ewfrf/wc/d...name=c00063244)


PREWORK: Configure Linux to boot into text mode by default - not X. I'm not sure of an easy way to do this with Ubuntu (because I used Webmin), but you basically don't want X to but up in runlevel 2, in case something goes wrong, you'll at least get to a login prompt easily.
You can try using update-rc.d to reconfigure gdm to boot only in 3, 4, and 5 [http://ubuntuforums.org/showthread.php?t=20583](http://ubuntuforums.org/showthread.php?t=20583)

1. Figure out what PCI port your NVIDIA card is on (Mine is PCI:1:9:0)
Code:

**lspci -X**

Here's mine (yours will look different)
Code:

mstralka@ubuntu:~ $ lspci -X 
PCI:0:0:0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface 
PCI:0:2:0 Display controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device 
PCI:0:29:0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 
PCI:0:29:1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 
PCI:0:29:2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 
PCI:0:29:7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller 
PCI:0:30:0 PCI bridge: Intel Corp. 82801 PCI Bridge 
PCI:0:31:0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge PCI:0:31:1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller 
PCI:0:31:3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller 
PCI:0:31:5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller 
PCI:1:9:0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] 
PCI:1:12:0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+

Your card may show up as an "unknown device" if it is not in /var/lib/misc/pci.ids. You can look yours up at the official source: [http://pciids.sourceforge.net/iii/?i=10de](http://pciids.sourceforge.net/iii/?i=10de), then add it to /var/lib/misc/pci.ids in the appropriate place, or download pci.ids from that website and replace /var/lib/misc/pci.ids


2. Follow the Ubuntu 5.04 Starter Guide instructions to install the NVIDIA drivers [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver) - here's the important part

Code:

[B]sudo apt-get install nvidia-glx 
sudo apt-get install nvidia-settings 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
sudo nvidia-glx-config enable
[/B]

3. Add nvidia to /etc/modules so it will load at startup

Code:

**sudo gedit /etc/modules**

Add to the end
Code:

**nvidia**


4. Add agpgart and intel_agp to the hotplug blacklist so they won't load at startup
Code:
[B]
sudo gedit /etc/hotplug/blacklist[/B]

Add the following to the end:
Code:

[B]agpgart 
intel_agp[/B]


5. Edit /etc/X11/xorg.conf (after backing it up)
-In Section "Modules", be sure to comment out GLCore and DRI, but make sure glx is enabled.
-Modify the Section "Device" appropriately for your system. Mine looks like this:
Code:

Section "Device" 
  Identifier "NVIDIA Corporation NV34 [GeForce FX 5500]" 
  Driver "nvidia" 
  BusID "PCI:1:9:0" 
    Option "NvAGP" "1" 
    Option "RenderAccel" "true" 
    Option "NoLogo" #This is optional - it will hide the NVIDIA splash screen 
   #0 : Disable AGP 
   #1 : use NVIDIA's internal AGP support, if possible 
   #2 : use AGPGART if possible #3 : use any agp support (try AGPGART, then NVIDIA's AGP) 
EndSection


6. Reboot and enter the BIOS Settings. Disable the onboard video
7. Unplug your monitor from your onboard video card and plug it into the NVIDIA card
8. If it hangs at hotplug, do a hard-reboot, and when it gets to hotplug again, press CTRL-C and adjust settings.
9. Try to start X
Code:
[B]
sudo gdm[/B]

10. If that doesn't work you may have to reconfigure X
Code:

**sudo dpkg-reconfigure xserver-xorg**

---

### Post by greenwom on 2006-07-08
my system will not allow me to 
sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings 

I can only have one or the other, I useed the GLX package, how do I get the settings??

---

### Post by spool on 2006-07-08
If I'm not mistaken, nvidia-settings is included in nvidia-glx. You should only need to install the nvidia-glx package.

---

### Post by tseliot on 2006-07-09
This guide is for **Ubuntu Hoary 5.04**.

Anyhow I can adapt it and include it in the Problems Section of my guides for Breezy and for Dapper (giving you due credits in my guide)

---

### Post by tseliot on 2006-07-22
I have written this guide for Dapper, Breezy and Hoary:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

---

### Post by surak on 2006-08-08
I created a package for fixing this issue. It works on dapper and edgy (I didn't tested it on breezy or hoary or warty).

The file is at launchpad: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55104](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/55104)

Remember that you still need to change the video device for nvidia by typing, as root, "dpkg-reconfigure xserver-xorg" and then setting it to nvidia.

---

### Post by captainpotato on 2007-02-24
> **tseliot said:**
> I have written this guide for Dapper, Breezy and Hoary:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

tseliot - thanks very much for your efforts. Your HOW-TO solved my problem and I can now boot my machine using the FX 5200 in the PCI slot. Now to solve the nvidia driver issues...

---

### Post by such on 2007-07-17
> **tseliot said:**
> I have written this guide for Dapper, Breezy and Hoary:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)

Work fine 7.04 feisty fawn thx.

Note:im sorry bad english :(

---

### Post by banhbaochay on 2008-09-11
Hi everybody,
I can't install driver VGA card with my computer because I use VGA card NVIDIA. It's very luck when I read this thread. But I don't know how to boot into text mode. So I still can't install. 
I found this text which help me to boot into text mode:
> 

When you see the GRUB Loading message, press ESC to get to the grub menu. Here, you will see several lines with kernel descriptions in them: select the one that does not say recovery using the arrow keys.
# Press e to edit the commands associated with that kernel. This will bring up another screen with various options, the one you are looking for has kernel in it. Using the arrow keys, select the line with kernel in it and press e to edit the line.
# This will take you to a screen with the contents of the line in it, just add your new command at the end, then press enter.
# You will be returned to the previous menu and you should be able to see your altered boot options added to the line you edited (unless the boor command line is too long). Press b to boot using the edited boot command.


I don't know what command I must add at the end?????

---

