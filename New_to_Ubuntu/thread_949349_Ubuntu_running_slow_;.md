---
title: "Ubuntu running slow ;\"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by LeftNut on 2008-10-16
As of recent ubuntu has been running kinda laggy. i have compiz installed i use the cube no animations. i use emerald themes. and cario-dock dock bar. If anyone could direct me to a thread were i can improve my performance of ubuntu or give me some suggestions i would really appreciate it.

Thank you for any help,
Gary

---

### Post by alphacrucis2 on 2008-10-16
> **LeftNut said:**
> As of recent ubuntu has been running kinda laggy. i have compiz installed i use the cube no animations. i use emerald themes. and cario-dock dock bar. If anyone could direct me to a thread were i can improve my performance of ubuntu or give me some suggestions i would really appreciate it.

Thank you for any help,
Gary


What shows up with top?

---

### Post by LeftNut on 2008-10-16
> **alphacrucis2 said:**
> What shows up with top?

top of the system monitor? what do you mean by top? when i open windows or programs there taking awhile to load up now and it shouldn't be because of my system specs.

Thank you,
Gary

---

### Post by alphacrucis2 on 2008-10-16
> **LeftNut said:**
> top of the system monitor? what do you mean by top? when i open windows or programs there taking awhile to load up now and it shouldn't be because of my system specs.

Thank you,
Gary

top is a command line program that you run under terminal. It shows the processes running on your pc and what resources they are using. There is also a variant called htop. I can't recall if htop is installed by default or you have to install it through the package manager. I'm not on my linux machine at present. (using my windows lappy). The htop display looks like this example - lots of useful info for diagnosing performance problems:

[http://htop.sourceforge.net/]("http://htop.sourceforge.net/")

---

### Post by LeftNut on 2008-10-16
> **alphacrucis2 said:**
> top is a command line program that you run under terminal. It shows the processes running on your pc and what resources they are using. There is also a variant called htop. I can't recall if htop is installed by default or you have to install it through the package manager. I'm not on my linux machine at present. (using my windows lappy). The htop display looks like this example - lots of useful info for diagnosing performance problems:

[http://htop.sourceforge.net/]("http://htop.sourceforge.net/")

ah me either atm i'll report back when i get home.

thank for the help so far though,
Gary

---

### Post by LeftNut on 2008-10-16
heres the tops:
top - 04:29:31 up 2 min,  2 users,  load average: 1.03, 0.75, 0.30
Tasks: 120 total,   1 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.0%us,  3.3%sy,  0.0%ni, 85.1%id,  0.0%wa,  0.5%hi,  0.2%si,  0.0%st
Mem:   3114896k total,   604544k used,  2510352k free,    50768k buffers
Swap:  4369640k total,        0k used,  4369640k free,   282896k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 5741 root      20   0  325m  33m 8272 S   21  1.1   0:13.90 Xorg                                                                                                                
 6243 g         20   0 49556  38m  11m S    1  1.3   0:05.08 compiz.real                                                                                                         
 6038 g         20   0 42092  25m  13m S    1  0.8   0:01.58 gnome-panel                                                                                                         
 6352 g         20   0 19924  10m 6060 S    1  0.4   0:00.32 emerald                                                                                                             
 6385 g         20   0 74472  20m  11m S    1  0.7   0:00.72 gnome-terminal                                                                                                      
 6406 g         20   0  2308 1132  856 R    1  0.0   0:00.16 top                                                                                                                 
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.38 init         

top lower:
top - 04:32:24 up 5 min,  2 users,  load average: 0.55, 0.70, 0.36
Tasks: 120 total,   1 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.0%us,  0.0%sy,  0.0%ni, 50.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3114896k total,   650148k used,  2464748k free,    50856k buffers
Swap:  4369640k total,        0k used,  4369640k free,   304940k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.38 init

---

### Post by LeftNut on 2008-10-16
bump

---

### Post by LeftNut on 2008-10-16
> **LeftNut said:**
> bump

any ideas =\

Thank you,
Gary

---

### Post by celticbhoy on 2008-10-16
What are the specs on your machine?

Was it running ok previously?

Have you installed anything or added/removed hardware?

---

### Post by randy78 on 2008-10-16
What is the speed of your CPU?
How much RAM (memory) do you have?
Are you using an integrated graphics controller or do you have a different video card (ATI, Nvidia)?

There are many things that we can disable from starting up during boot, but we need to know the hardware specs first. :)

Take Care

EDIT: celticbhoy beat me to it ;)

---

### Post by LeftNut on 2008-10-16
> **celticbhoy said:**
> What are the specs on your machine?

Was it running ok previously?

Have you installed anything or added/removed hardware?

my machine specs are 1.9ghz duo processor/3gb's of ram/gaming graphics card/nvidia drivers i think

It was running fine previously but i encountered a  problem trying to uninstall compiz so i re-installed ubuntu and formated that partion. upon re-install of hardy i installed cario-dock/compiz-fusion icon/compiz desktop effects/atlantis theme but dont have it enabled/emerald theme.

feel free to tell me if i missed any important information.

i'm still new to linux i've been more of a windows power user and i'm still adjusting to the different commands in terminal compared to dos.

Thank you very much,
Gary

---

### Post by forger on 2008-10-16
heh.. fellas, just ask for the output of this command:
```
sudo lshw -short
```

---

### Post by forger on 2008-10-16
also, the output of xorg:
```
cat /etc/X11/xorg.conf
```

---

### Post by LeftNut on 2008-10-16
> **forger said:**
> heh.. fellas, just ask for the output of this command:
```
sudo lshw -short
```

this commnad gave me this.

H/W path           Device      Class       Description
======================================================
                               system      P-6831FX
/0                             bus         P-6831FX
/0/0                           memory      99KiB BIOS
/0/4                           processor   Intel(R) Core(TM)2 Duo CPU     T5450 
/0/4/5                         memory      64KiB L1 cache
/0/4/6                         memory      2MiB L2 cache
/0/4/1.1                       processor   Logical CPU
/0/4/1.2                       processor   Logical CPU
/0/16                          memory      3GiB System Memory
/0/16/0                        memory      1GiB SODIMM Synchronous 667 MHz (1.5 
/0/16/1                        memory      2GiB SODIMM Synchronous 667 MHz (1.5 
/0/1                           processor   
/0/1/1.1                       processor   Logical CPU
/0/1/1.2                       processor   Logical CPU
/0/100                         bridge      Mobile PM965/GM965/GL960 Memory Contr
/0/100/1                       bridge      Mobile PM965/GM965/GL960 PCI Express 
/0/100/1/0                     display     GeForce 8800M GTS
/0/100/1a                      bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1a.1                    bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1a.7                    bus         82801H (ICH8 Family) USB2 EHCI Contro
/0/100/1b                      multimedia  82801H (ICH8 Family) HD Audio Control
/0/100/1c                      bridge      82801H (ICH8 Family) PCI Express Port
/0/100/1c/0        wmaster0    network     PRO/Wireless 4965 AG or AGN Network C
/0/100/1c.1                    bridge      82801H (ICH8 Family) PCI Express Port
/0/100/1c.1/0                  storage     Sil 3531 [SATALink/SATARaid] Serial A
/0/100/1c.2                    bridge      82801H (ICH8 Family) PCI Express Port
/0/100/1c.2/0      eth0        network     RTL8111/8168B PCI Express Gigabit Eth
/0/100/1c.3                    bridge      82801H (ICH8 Family) PCI Express Port
/0/100/1c.4                    bridge      82801H (ICH8 Family) PCI Express Port
/0/100/1d                      bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1d.1                    bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1d.2                    bus         82801H (ICH8 Family) USB UHCI Control
/0/100/1d.7                    bus         82801H (ICH8 Family) USB2 EHCI Contro
/0/100/1e                      bridge      82801 Mobile PCI Bridge
/0/100/1e/6                    bus         FW323
/0/100/1f                      bridge      82801HBM (ICH8M-E) LPC Interface Cont
/0/100/1f.1        scsi4       storage     82801HBM/HEM (ICH8M/ICH8M-E) IDE Cont
/0/100/1f.1/0.0.0  /dev/cdrom  disk        DVD RW AD-7563A
/0/100/1f.2        scsi0       storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA AHC
/0/100/1f.2/0      /dev/sda    disk        250GB WDC WD2500BEVS-2
/0/100/1f.2/0/1    /dev/sda1   volume      11GiB Windows NTFS volume
/0/100/1f.2/0/2    /dev/sda2   volume      221GiB Windows NTFS volume
/0/100/1f.2/1      /dev/sdb    disk        250GB TOSHIBA MK2552GS
/0/100/1f.2/1/1    /dev/sdb1   volume      131GiB Windows NTFS volume
/0/100/1f.2/1/2    /dev/sdb2   volume      101GiB Extended partition
/0/100/1f.2/1/2/5  /dev/sdb5   volume      97GiB Linux filesystem partition
/0/100/1f.2/1/2/6  /dev/sdb6   volume      4267MiB Linux swap / Solaris partitio
/0/100/1f.3                    bus         82801H (ICH8 Family) SMBus Controller
/0/2               scsi6       storage     
/0/2/0.0.0         /dev/sdc    disk        Multi-Card
/0/2/0.0.0/0       /dev/sdc    disk

---

### Post by celticbhoy on 2008-10-16
My guess would be that your graphics card driver needs sorting after the re-install

---

### Post by celticbhoy on 2008-10-16
[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

look here

---

### Post by LeftNut on 2008-10-16
> **forger said:**
> also, the output of xorg:
```
cat /etc/X11/xorg.conf
```

the file is there when i goto that directory in file explorer but in terminal using that command it says no such file.

> **celticbhoy said:**
> My guess would be that your graphics card driver needs sorting after the re-install

i installed the nvidia drivers through synaptic i assume these are the most upto date since on the last install of hardy i used these and they were fine.


Thank you,
Gary

---

### Post by randy78 on 2008-10-16
kind of a shot in the dark, but try this in a terminal: 
whereis xorg.conf 

and then

ls -l <location of xorg from above>

---

### Post by LeftNut on 2008-10-16
> **randy78 said:**
> kind of a shot in the dark, but try this in a terminal: 
whereis xorg.conf 

and then

ls -l <location of xorg from above>

this is what the terminal gave me for that:
g@G-Mobile:~$ whereis xorg.conf
xorg: /usr/lib/xorg
g@G-Mobile:~$ ls -l /usr/lib/xorg
total 4
drwxr-xr-x 8 root root 4096 2008-10-16 00:58 modules

---

### Post by alphacrucis2 on 2008-10-16
When you did cat /etc/X11/xorg.conf note that the X11 has to be capital X. If you typed cat /etc/x11/xorg.conf it wouldn't work as directory and file names are case sensitive. Just a thought.

---

### Post by LeftNut on 2008-10-16
> **alphacrucis2 said:**
> When you did cat /etc/X11/xorg.conf note that the X11 has to be capital X. If you typed cat /etc/x11/xorg.conf it wouldn't work as directory and file names are case sensitive. Just a thought.

roger roger you are correct sir here is what i got from it:
g@G-Mobile:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by forger on 2008-10-17
I need this one too:
```
glxinfo | grep direct
```

It will say whether the driver is actually loaded and used

---

### Post by Bicko on 2008-10-17
Hi all,

I have a very similar problem and am looking forward to seeing how this pans out.

Not to hijack the thread, but my story is....

...Fresh install of Hardy, nVidia 6800GS graphics card, glxgears reports 290fps immediately after install. Activate the nVidia restricted drivers and I then get 2.956 fps from glxgears!

I now notice that Google Earth will start but work sllllowly (previously would dump me and then restart X), screen savers move painfully slowly (hardly a worry, really!) but they did seem smoother before. While Google Earth is running (crawling?!), 'top' shows it's taking 98-99% CPU constantly.

This all worked fine before the switch to Hardy - previously used all the recent versions of kubuntu (note the K) and have gone for this LTS version in order to see if I can get other family members to use it.

I'll post the output of sudo lshw -short, cat /etc/X11/xorg.conf, & glxinfo | grep direct below.

Thanks for any pointers you can give, but I'm happy to follow the help you're all giving to LeftNut.

Cheers,
Bicko.
> jayne@rascalpants:~$ sudo lshw -short
[sudo] password for jayne: 
H/W path           Device      Class       Description
======================================================
                               system      System Name
/0                             bus         P4B533-V
/0/0                           memory      64KiB BIOS
/0/4                           processor   Intel(R) Pentium(R) 4 CPU 2.80GHz
/0/4/9                         memory      8KiB L1 cache
/0/4/a                         memory      512KiB L2 cache
/0/2a                          memory      1GiB System Memory
/0/2a/0                        memory      512MiB DIMM DRAM Synchronous
/0/2a/1                        memory      512MiB DIMM DRAM Synchronous
/0/2a/2                        memory      DIMM DRAM Synchronous [empty]
/0/100                         bridge      82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
/0/100/1                       bridge      82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge
/0/100/1/0                     display     NV40 [GeForce 6800 GS]
/0/100/1d                      bus         82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
/0/100/1d.1                    bus         82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
/0/100/1d.2                    bus         82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
/0/100/1d.7                    bus         82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
/0/100/1e                      bridge      82801 PCI Bridge
/0/100/1e/b                    bus         FW323
/0/100/1e/c                    multimedia  SB0400 Audigy2 Value
/0/100/1e/e        eth0        network     LNE100TX
/0/100/1f                      bridge      82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
/0/100/1f.1        scsi0       storage     82801DB (ICH4) IDE Controller
/0/100/1f.1/0      /dev/sda    disk        80GB WDC WD800JB-00ET
/0/100/1f.1/0/1    /dev/sda1   volume      19GiB Windows NTFS volume
/0/100/1f.1/0/2    /dev/sda2   volume      54GiB Extended partition
/0/100/1f.1/0/2/5  /dev/sda5   volume      19GiB W95 FAT32 partition
/0/100/1f.1/0/2/6  /dev/sda6   volume      6000MiB Linux filesystem partition
/0/100/1f.1/0/2/7  /dev/sda7   volume      352MiB Linux swap / Solaris partition
/0/100/1f.1/0/2/8  /dev/sda8   volume      29GiB Linux filesystem partition
/0/100/1f.1/0/3    /dev/sda3   volume      8032KiB Linux filesystem partition
/0/100/1f.1/1      /dev/cdrom  disk        DVD-RW  DVR-106D
/0/100/1f.3                    bus         82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
/0/1               scsi2       storage     
/0/1/0.0.0         /dev/sdb    disk        CompactFlash
/0/1/0.0.0/0       /dev/sdb    disk        
/0/1/0.0.1         /dev/sdc    disk        SM/MS/SD
/0/1/0.0.1/0       /dev/sdc    disk        


> jayne@rascalpants:~$ cat /etc/X11/xorg.conf
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection


> jayne@rascalpants:~$ glxinfo | grep direct
direct rendering: Yes

---

### Post by LeftNut on 2008-10-17
> **Bicko said:**
> Hi all,

I have a very similar problem and am looking forward to seeing how this pans out.

Not to hijack the thread, but my story is....

...Fresh install of Hardy, nVidia 6800GS graphics card, glxgears reports 290fps immediately after install. Activate the nVidia restricted drivers and I then get 2.956 fps from glxgears!

I now notice that Google Earth will start but work sllllowly (previously would dump me and then restart X), screen savers move painfully slowly (hardly a worry, really!) but they did seem smoother before. While Google Earth is running (crawling?!), 'top' shows it's taking 98-99% CPU constantly.

This all worked fine before the switch to Hardy - previously used all the recent versions of kubuntu (note the K) and have gone for this LTS version in order to see if I can get other family members to use it.

I'll post the output of sudo lshw -short, cat /etc/X11/xorg.conf, & glxinfo | grep direct below.

Thanks for any pointers you can give, but I'm happy to follow the help you're all giving to LeftNut.

Cheers,
Bicko.

Feel free to hijack my friend i solved my issue by re-installing hardy and installing everything again. now everything runs great again i dont know what the issue was with the last install of hardy. but i've done this a few times now and it only takes me 30 minutes to completely redo everything since i back up all the wallpapers/themes/and etc. i wish you the best at fixing this issue though.

Good Luck,
Gary

---

### Post by LeftNut on 2008-10-17
Also if you want i can redo any commands i previously entered if you guys want them to compare.

thanks,
Gary

---

