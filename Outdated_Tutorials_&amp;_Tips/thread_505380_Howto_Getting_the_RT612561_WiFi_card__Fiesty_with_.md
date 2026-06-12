---
title: "Howto: Getting the RT61/2561 WiFi card  Fiesty with Network Manager WPA"
date: 2007-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by menisk on 2007-07-20
I have had a wireless card with the RT61/2561 chipset for about a year. When I first installed it under Ubuntu 6.10 Edgy, it worked absolutely perfectly. Then when the upgrade to Ubuntu 7.04 fiesty happened it all went to hell. The drivers that come with fiesty were hellishly inconsistent for me and would refuse to connect to my WPA networks, not to mention the fact I couldn't use it with the brand new network manager applet. After hours of searching I only found guides using native linux driver. This guide shows you how to use the ndiswrapper module to use the windows drivers under linux with full support for the network manager applet.

First we need to remove the ndiswrapper module that comes with Ubuntu 7.04 fiesty so we can compile our own.
> sudo rmmod ndiswrapper
> sudo apt-get remove ndiswrapper-utils

Now we need to get some addition packages to compile our new ndiswrapper module.
> sudo apt-get update
> sudo apt-get install build-essential linux-headers-`uname -r`

Now we need to download the ndiswrapper source to compile
> wget [http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/ndiswrapper/ndiswrapper-1.47.tar.gz)

We'll also need some Windows drivers to install with ndiswrapper.
> wget [http://asia.giga-byte.com/FileList/Driver/comm_wp01gs_v11.zip](http://asia.giga-byte.com/FileList/Driver/comm_wp01gs_v11.zip)[/QUOTE

Lets extract the ndiswrapper source so we can compile
[QUOTE]tar -xzvf ndiswrapper-1.47.tar.gz

Time to blacklist the native drivers so that we can use ndiswapper without any issues.
> sudo su
> sudo echo blacklist rt61 >> /etc/modprobe.d/blacklist

[SIZE="5"][COLOR="Red"]REBOOT NOW[/COLOR][/SIZE]

Time to compile the ndiswrapper module and install the drivers. So lets open the terminal again.
> cd ndiswrapper-1.47

Time to remove the crumbs of the old module. (Run this until it says there is nothing to remove)
> sudo make uninstall

Now we compile the new one.
> sudo make

Install it...
> sudo make install
Go back to the home directory.
> cd

Unzip our drivers.

> unzip ./comm_wp01gs_v11.zip

Into the drivers directory.
> cd GN-WP01GS/Drivers/xp2k

Now we install the drivers.
> sudo ndiswrapper -i rt61.inf

List all driver installed in ndiswrapper, to make sure ours appear.
> sudo ndiswrapper -l

You want an output like this...
> netrt61g : driver installed
	device (1814:0302) present (alternate driver: rt61)

It may look slightly different but something similar to that is good.

Finish installing the drivers.
> sudo ndiswrapper -m

Start the drivers
> sudo modprobe ndiswrapper

That should be it, test your wireless with the network applet. If you have any issues please post in the comments and I'll try to help you.

---

### Post by ForceAbuser on 2007-07-26
hi!

great guide!, although it didnt work for me :( now i dont see my wireless in the network manager applet....

it might be my bad, couse when i should type:
> sudo make **un**install
i typed
> sudo make install

plus in the beginning of the guide i should remove the old ndiswrapper, but i have the feeling that wasn't installed on my clean install of ubuntu x86_64.....

and you forgot to mention that you will have to unpack the .zip file, containing the drivers ;-)

---

### Post by menisk on 2007-07-27
ForceAbuser, Yes your right, I did forget to mention the unpacking of the zip. Thanks I'll change that.

The reason your having trouble is, I have written this guide for 32 bit processors and for 64bit you will need the 64bit windows drivers. I'll add an alternate thread with an edited guide for 64 bit. I'll add the link here when done.

---

### Post by fenwik on 2007-07-27
Worked perfectly for me, thanks for the howto.

---

