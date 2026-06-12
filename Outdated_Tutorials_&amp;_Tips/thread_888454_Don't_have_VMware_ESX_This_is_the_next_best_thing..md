---
title: "Don't have VMware ESX? This is the next best thing. (Howto)"
date: 2008-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by paradexes on 2008-08-13
This tutorial assumes you have a basic understanding of Virtualization and the Linux (Debian/Ubuntu) CLI commands. The goal here is to build Ubuntu with a very minimal install to maximize performance.

This tutorial is ideal for small businesses or individuals that heavily use Linux and are not looking to buy Virtual Infrastructure 3 or any of the equivalent competitor products. 

As you may or may not know, VMware ESX server is supposed to be an OS or a thin layer of software that has one function. To create VMs for near native performance. 

There recently was a free release for ESX3i which is a stripped down version of ESX. However it lacks a the virtualized Linux console that its bigger brother has and both are limited to very specific hardware configurations. This tutorial is meant to be an alternative solution using existing VMware products and give similar results. Granted performance will be a little slower, but for most cases it will be enough to work reliably and with flexibility. 

First download and burn to CD

For anyone with a x64 bit capable CPU I strongly recommend:
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-amd64/current/images/netboot/mini.iso)

If you are limited to x86 hardware then download:
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso)

Boot the CD and type CLI at the boot screen.

Install Ubuntu (if you are not familiar with an Ubuntu installation please search these forums for further assistance as it is out of the scope of this doc)

Once installed please set your IP address to static by editing /etc/network/interfaces to look like:
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1

```

If you have more interfaces just add eth1, eth2, etc.

Before installing VMware server you MUST have the following installed:
build-essential linux-kernel-headers debian-helper-scripts (optional)
Install by typing
```
sudo apt-get install build-essential linux-kernel-$(uname -r) debian-helper-scripts
```

If the install goes well...

Then download VMware Server 2.0 RC1 (as of this writing) (RC2 has been released which is also VMware-server-2.0.0-110949.*.tar.gz)
by typing in the console 
```
wget http://download3.vmware.com/software/vmserver/VMware-server-2.0.0-101586.x86_64.tar.gz
``` 
Then type the following each on a separate line
```
cd ~/
tar -xvf VMserver*
cd vmware-server-distrib
sudo ./vmware-install.pl
```

Answer the questions and get the free registration key at vmware.com and you are all set if you don't have one. You can also google for the key seeing as it is a free product. I will not post it here in the interest of possible liability. 

Assuming you followed the default web ports then you should be able to just type [http://servernameorip.com/ui](http://servernameorip.com/ui) and you will be presented with a login and then a fully functional web based client to create manage and provision VMs. With an open source underlying system to keep the system running and massive driver support, this in many ways already beats out ESX for SMBs. 

VMware is rock solid IMO, and the management tools rock. (again my opinion).

Here is a free and very flexible alternative using Ubuntu and woudl want from ESX. And there is immense flexibility in both hardware and software to manage the host system based on the open source aspects of Linux. This tutorial can be adapted for various other distros as well that can strip the OS down to barebones, but Ubuntu is the one I have focused on since it is the distro I use and it was the easiest to implement this.

If you find any other tweaks that help boost the performance post them up. I kept this real basic for anyone new to Linux and Virtualization to follow on.

---

### Post by Mike'sHardLinux on 2008-08-15
Thanks for the tutorial! I was just trying to install ESXi and it doesn't like my hardware.

I noticed one typo when I was installing my server: I think **linux-kernel** should be **linux-headers**, at least, that's what I had to do.

Thanks again!
:guitar:

---

### Post by MrFSL on 2008-08-16
Disable ipv6

---

### Post by paradexes on 2008-08-29
You can, but you should not need to. At least that was not the case on Hardy 8.04.1

Can you state why IPV6 needs to be disabled? I can post it in the notes if I can get a detailed reason why. My goal with this howto is to make it solid as a rock for anyone to setup stably.

---

### Post by Sam Lars on 2008-08-29
Thanks for this guide.  I've tried putting in
```
localhost/ui
127.0.0.1/ui
```
and it tells me that there's a server there, but it can't connect to it.
I tried
```
http://127.0.0.1:902/
```
and got
```
220 VMware Authentication Daemon Version 1.10: SSL Required, ServerDaemonProtocol:SOAP, MKSDisplayProtocol:VNC , VMXARGS supported
```

Edit:
I finally got to it after doing a port scan and trying the 8000 series ports (one of which I suspected VMware was set up on), and
```
localhost:8222/ui
```
did the trick.

---

### Post by MrFSL on 2008-08-30
> **paradexes said:**
> You can, but you should not need to. At least that was not the case on Hardy 8.04.1

... because the people over at vmware told me to.

Sorry wish I could supply a link... let me search a second...

Here is a google search:
[http://www.google.com/search?hl=en&q=vmware+ipv6&btnG=Google+Search&aq=f&oq=](http://www.google.com/search?hl=en&q=vmware+ipv6&btnG=Google+Search&aq=f&oq=)

Greets.

---

### Post by MrFSL on 2008-08-30
[http://www.vmware.com/products/beta/vmware_server/releasenotes_vmserver2.html](http://www.vmware.com/products/beta/vmware_server/releasenotes_vmserver2.html)

> The vmnet-netifup daemons do not terminate when VMware Server is stopped.
Workaround: Disable IPv6 on your host.

---

### Post by airjrdn on 2008-09-14
A normal VM runs within a host OS so you can run Windows inside Linux or vice versa.  ESX differs in that the "host OS" is actually a minimal VMWare OS correct?  And you can "switch" between running OS's similar to switching between applications?

I have some apps that are Windows only, and won't run in a VM due to graphics constraints.  Would this negate my need for dual booting (shutdown Linux, and reboot into Windows)?  So I could just alt-tab or whatever to get to Windows or back to Linux?

---

### Post by MrFSL on 2008-09-14
Not quite. ESX is an enterprise virtualization system - specifically desired because its High Availability options.

For the most part it would be used to run enterprise server solutions that have high availability requirements. 

There is no graphical desktop for ESX. The concept is that you install ESX on your servers and then use a management computer to setup your Virtual Machines. - This would not be for daily user use and operations. 


This thread points out that because this is considered a "server" solution it is made to only run on specific hardware. If you wanted a similar solution without the H.A. and Enterprise Service features you can run Ubuntu server with vmware server 2 beta. This is because the web interface is similar to ESX as well as the system resources needed to run the host.

In short ESX is not meant to be a Desktop product. It is probably not what you want to run at home.

---

### Post by airjrdn on 2008-09-14
"Ubuntu server with vmware server 2 beta"

Wouldn't that just be running Windows inside of Ubuntu in VMWare, similar to how I do w/Ubuntu 8.04 LTS?

I'm really after what it was I thought ESX did.  Something with an *extremely* minimal footprint that gives each OS near direct access to the hardware.  So there'd be almost no speed difference playing a game in XP for example vs playing it in XP where XP was the only OS on the machine.

---

### Post by MrFSL on 2008-09-15
ESX is not what you are looking for. All hardware is still vitualized as it is in VMware server

---

### Post by airjrdn on 2008-09-15
Thanks for the info.

---

### Post by MrFSL on 2008-09-15
the best solution for what you are describing in a dual boot system.

AKA you choose which operating system to run at boot time.

There is loads of info on this here on the forums as well as in the ubuntu official documentation

---

### Post by airjrdn on 2008-09-15
Yeah, that's what I'm doing now, both dual booting, and running XP in VMWare/VirtualBox.  It would be really nice to not have to get out of Ubuntu just to do something that won't work via XP in a VM.

---

### Post by paradexes on 2008-09-25
MrFSL has been spot on on most of the comments. The howto is meant for people who cannot run VMware ESX or ESXi (which are similar) because they do not have the hardware for it (some desktop systems will run it if you have the right combo if chipsets and such). 

The idea is to install a minimal Ubuntu install and not have all the extra cruft so you can have basically a headless system if you wanted to. Installing a UI kinda defeats the purpose. 

When I setup a system like this I install the mini.iso I refered to in my OP and the boot option CLI to install the system. I try to keep it minimal where possible. 

For more performance, you could recompile the kernel and remove extra packages you would not need. With the extensions in Intels VT and AMDs version of VT, you could get close to the same performance as ESX (but still with some performance hits) 

As far as disabling IPV6 it is something you can do if you are affected by the vmnet-ifup daemons issue refered to in the release notes: 

The vmnet-netifup daemons do not terminate when VMware Server is stopped.
Workaround: Disable IPv6 on your host.

But in my case I did not need to do that so YMMV.

---

### Post by bcde617 on 2008-09-25
Cool topic, come on to update it. will keep an eye on it. Coolingame was established in December 25, 2004. Our head office located in Malaysia beachPenang. We focus on provide the professional power leveling services. Different to other sites we do powerleveling ONLY, no any virtual goods trade. We have our own [wow powerleveling](http://www.coolingame.com) team and this make sure that your order will be done in time with high quality. A hands-on shopping with us will immediately tell the difference. We wrecked our brains to better cater to the needs of our dear customers and constantly meliorated our services to better entertain our clients. With flying delivery, around-the-clock customer service, sophisticated order processing system and guaranteed powerleveling security, coolingame has won the trust from thousands of customers. Perhaps around your friends as well as our customers. i like [wow power leveling](http://www.coolingame.com) service.[WoW Powerleveling](http://www.levelmyth.com) & World of Warcraft power leveling service.Do you feel bored while level rate increasing process? Don't worry about that. Let LevelMyth do it for you. Trust our professional level service. We will do our best in all of our orders. We have done a great number of orders for: [WOW power leveling](http://www.levelmyth.com) US, World of Warcraft power leveling EUand other games.

---

### Post by GordonCopestake on 2008-11-05
It might be worth noteing that ESXi has been released as a free download by VMWare now, which for some people would be a good alternative to a mini-ubuntu + vmware server.

Here is a guide for installing ESXi on IDE
[http://www.vm-help.com/esx/esx3i/ESXi_install_to_IDE_drive/ESXi_install_to_IDE_drive.php](http://www.vm-help.com/esx/esx3i/ESXi_install_to_IDE_drive/ESXi_install_to_IDE_drive.php)

---

