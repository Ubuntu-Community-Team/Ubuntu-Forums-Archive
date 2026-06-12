---
title: "HowTo auto-install VMware-Server on Ubuntu 6.06 Dapper"
date: 2006-08-09
forum: Outdated Tutorials &amp; Tips
---

### Post by jbaloul on 2006-08-09
**HowTo Install Vmware Server + Ubuntu**
[i]
Posted At:
[http://howtoforums.net/viewtopic.php?t=55](http://howtoforums.net/viewtopic.php?t=55)
[/i]

**Overview:**
For those of you who are not familiar, in brief VMware is a technology used to run multiple, simultaneous, OS's with virtual hardware on top of one physical server. You can run any Windows on top of any Linux, and visa versa. -- [http://www.vmware.com](http://www.vmware.com)

I put this together to automate the installation / pre-installation requirements for Ubuntu VMware Servers...
I use these installation procedures on a daily basis to rapidly deploy lite weight Ubuntu vmhost servers, and I have certified this installation on the following Hardware / Architectures:
    **Servers:**
    *AMD64* - Sun Microsystems: X4200 - AMD Opteron Model 280 64bit CPU's
    *i686* - IBM: eServer xSeries 345 - Intel Xeon 64bit CPU's
    **Workstations:**
    *i386* - Compaq: Evo D510 CMT - Intel Pentium 4 CPU's
    *i386* - Acer: Veriton 7500G - Intel Pentium 4 CPU's
    *i386* - Acer: Veriton 7200D - Intel Pentium 4 CPU's
    *amd* - Tiger: Dual CPU - AMD Athlon MP CPU's

**Final Results:**
The final configuration, if everything went smooth should be:
*Ubuntu 6.06 Dapper, OpenSSH-Server, VMware-Server, VMware-Console, FluxBox window manager*

**Ubuntu VMware-Server Management**
This installation will give you the ability to manage your server using the following methods:
**1. SSH - Secure Shell:**
From Linux - OpenSSH-client, built into most *nix systems by default.
From Windows using a tool like PuTTy: [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)
**2. VMware-Server-Console - Remotely**
You can connect and manage the Virtual Machines via the console from any OS
**3. VMware-Server-Console - Locally**
You can login to the Window Manager (FluxBox) locally and run VMware-Console from the menu (right click)

**FAQ**
Q. "Why do you install a GUI (window manager) on a VMware server?"
A. The reason is when connectivity goes down, and you cannot connect from neither ssh nor remote VMware-Console, then you should have the ability to connect to the localhost with VMware-Console.

Q. "Why did you choose FluxBox as the Window Manager?"
A. In my opinion, Gnome & KDE are a bit too much for what we need...I try to keep the system thin and to the point while ensuring stability and scalability. I have benchmarked all the WM's, including XFCE (Xubuntu), and I chose not to choose a pre-packaged Ubuntu, rather to install a clean X with FluxBox, what I consider to be the most robust, highly configurable, lite weight WM out there today.


**Screenshots:**
*some screenshots to give you an idea of what we are aiming for*
[http://howtoforums.net/downloads/screenshots/dapper-vmware/dapper-vmware1.png](http://howtoforums.net/downloads/screenshots/dapper-vmware/dapper-vmware1.png)
[http://howtoforums.net/downloads/screenshots/dapper-vmware/dapper-vmware2.png](http://howtoforums.net/downloads/screenshots/dapper-vmware/dapper-vmware2.png)
[http://howtoforums.net/downloads/screenshots/dapper-vmware/dapper-vmware3.png](http://howtoforums.net/downloads/screenshots/dapper-vmware/dapper-vmware3.png)


**This script consists of 4 parts.**
1. A clean server install of Ubuntu 6.06 LTS aka Dapper
2. Downloading & running the 2 Ubuntu VMware automatic install scripts
3. Downloading & running the VMware-Server & VMware-Server-Console Installations

**IMPORTANT: Pre-Installation considerations:**
1. You downloaded Ubuntu 6.06 LTS Server from [http://www.ubuntu.com/download](http://www.ubuntu.com/download)
2. Installed a fresh Ubuntu Server system
3. Connected to a network with dhcp / internet connection

**WARNING!: do not do this over an SSH connection or on an existing production system!**

**OK nuff talk, Let's Begin !!!**

**1. Get the Scripts...**
```

wget http://howtoforums.net/downloads/dapper-vmware.tar.bz2
tar -xjvf dapper-vmware.tar.bz2
sudo sh dapper-vmware.sh

```

Follow the USAGE for the script and use your network specific settings, to run the script again.
```

USAGE: sudo sh ./dapper-vmware.sh <new hostname> <new domain name> <new ip address> <new subnet> <new broadcast address> <new default gateway> <new dns nameserver ip address> <cpu architecture>
----------------------------------------------
   USAGE Example:
sudo sh ./dapper-vmware.sh vmhost01 howtoforums.net 192.168.1.5 255.255.255.0 192.168.1.255 192.168.1.1 192.168.112.2 amd64

        Supported cpu architectures:
        Please type one of the following
        1. i386        2. amd64        3. other

```


**2. Reboot into the new Kernel...**
```

sudo reboot

```

**3. Login to the graphical interface (gdm)**

**4. Login to a console - CTRL+F1**

**5. Run the Post installation script...**
```

sudo sh post-dapper-vmware.sh

```

**You are all set!!!**
You can now register (you must register to get your Free license) and download VMware-Server & VMware-Server-Console at:
[http://www.vmware.com](http://www.vmware.com)

You need to get the following:

> 
VMware Server for Linux.

Binary (.tar.gz)


*and...*

> 
VMware Server Linux client package.
- Linux VMware Server Console (.tar)


Once the tar files are downloaded you can then run the installation...
I gave an example below...
```

tar -xzf VMware-server-1.0.0-28343.tar.gz
cd vmware-server-distrib/
sudo ./vmware-install.pl

```



**Related Links:**
Ubuntu 5.10 Breezy Installation: [http://howtoforums.net/viewtopic.php?t=5](http://howtoforums.net/viewtopic.php?t=5)

FluxBox Information:
[http://www.fluxbox.org/](http://www.fluxbox.org/)
[http://fluxbox-wiki.org/index.php/Fluxbox-wiki](http://fluxbox-wiki.org/index.php/Fluxbox-wiki)

Other FluxBox Based Disro's:
Damn Small Linux: [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

HowTo install Remote Desktop (rdesktop1.5) with SeamLess Windows To run your favorite Windows Applications On your Linux box:
VMware is a classic Solution for running this...
[http://howtoforums.net/viewtopic.php?t=52](http://howtoforums.net/viewtopic.php?t=52)
 


Enjoy! :cool: 
-- 
Jacob
Linux -- Breaking All Boundries
"you may say I am a dreamer, but i'm not the only one"
[http://howtoforums.net](http://howtoforums.net)

---

