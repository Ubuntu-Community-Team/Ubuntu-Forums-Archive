---
title: "HOWTO: Wireless with Rt2500 cards (wmp54g in particular) using WPA and latest driver"
date: 2006-08-22
forum: Outdated Tutorials &amp; Tips
---

### Post by bionnaki on 2006-08-22
**_I have updated this HOW-TO. Everything should work smoothly. Confirmed to work with Dapper and Edgy_**

Howto: Wireless with Rt2500 cards using WPA and latest driver

This howto is for wireless pci cards that use the rt2500 driver which is included in the stock ubuntu installation. For whatever reason, the rt2500 driver that ships with ubuntu can be a bit buggy and annoying. This Howto will show you how to update your driver and connect to a WPA protected wireless network (you should use WPA over WEP, anyways).

I use a linksys wmp54g card and this howto is based on my experiences. Not sure if it'll work for other cards, but for the wmp54g you should be good.

**1.** First, check to see if your card uses the rt500 driver

> lshw

check the output for Network, particularly under driver. If it says something else, then reconsider following this guide - this is probably not for you.

**2.** Be sure to set up WPA with your router. I find that you should use "wpa personal" and "TKIP" algorithm. A shared key of 52 alphanumerial characters is what I use. For some reason, whenever I try to use a higher number or non-alphanumerial characters, WPA does not work with ubuntu. I have also noticed that setting ESSID to be hidden makes wireless act slightly buggy, so make sure ESSID is visible (hiding the ESSID is a weak security method, so dont worry about it). Wireless MAC filtering is also buggy. These are just suggestions and your mileage may vary. I also recommend checking out these tips for tweaking your signal particularly if your router is a linksys: [http://www.linksysinfo.org/portal/forums/showthread.php?t=47284](http://www.linksysinfo.org/portal/forums/showthread.php?t=47284)

I also recommend disabling onboard LAN functions if you have an onboard ethernet card. You can do this by editing your BIOS.

**3.**  In order to use WPA, you must modify your /etc/network/interfaces file. 

> sudo gedit /etc/network/interfaces

substitute kate for gedit if you use kubuntu. or use nano if you prefer commandline. 

copy and paste the following into that text file and save. Be sure to replace the *** with your own information.

For DHCP, use the following:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

auto ra0

iface ra0 inet dhcp 
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "******"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="*********"
        pre-up ifconfig ra0 up


For static IP addresses, use the following instead (be sure to modify the address, netmask and gateway for your own personal settings):

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0
auto ra0

iface ra0 inet static
        address 192.168.x.xx
        netmask 255.255.255.0
        gateway 192.168.1.1
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up ifconfig ra0 up
        pre-up ifconfig ra0 down
        pre-up iwconfig ra0 essid "******"
        pre-up iwconfig ra0 mode Managed
        pre-up iwpriv ra0 set AuthMode=WPAPSK
        pre-up iwpriv ra0 set EncrypType=TKIP
        pre-up iwpriv ra0 set WPAPSK="*******"
        pre-up ifconfig ra0 up




Of course, essid is the name of your network; channel is the frequency that you use and have specified in your router; wpapsk is your wpa shared key (be sure to use quotation marks). 

Save and close the file.

You also need enter the DNS server information. This is essential:

> 
sudo nano /etc/resolv.conf


and enter your DNS info and search info. My resolv.conf looks like so:

> 
nameserver 208.67.222.222
nameserver 208.67.220.220
search hsd1.xx.xxxx.net.


Your DNS will be different according to your ISP. I recommend using those nameservers as they are from opendns.com which is very fast. Your search will be different. You can aquire this info from your ISP if you do not know it.

**4.** Now, to update your driver to the latest rt2500. 

**_I highly recommend updating the driver - it is quite easy to do if you simply follow the instructions line by line_**

> 
sudo apt-get install build-essential linux-headers-$(uname -r)


This will install necessary packages for the compilation, after typing your password.

and then:

> 
wget [http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz)
tar -xzf rt2500-cvs-daily.tar.gz
cd ./rt2500*/Module
make
sudo ifdown ra0
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt2x00-legacy/rt2500/
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/ubuntu/wireless/rt2x00-legacy/rt2500
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500
sudo depmod


Reboot your computer once installation is complete. If you get an error complaining about "***/kernel/drivers/net/wireless/rt2x00-legacy/rt2500" or so not being found, dont worry about it.

If your wireless is not "up" or enabled, you can enable it via commandline with:

> 
sudo ifup ra0


Your internet connection should work now. I will keep this howto up-to-date with suggestions. Let me know if it works or not. Credit to drag, jdong, AndyCooll, and the authors of [this](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500) wiki for your posts that helped form this howto.

---

### Post by bionnaki on 2006-08-27
has anyone tried this yet?

---

### Post by ttenpas on 2006-08-28
I tried it and it worked perfectly. I only did steps 1-3 though as the driver update seemed a little complex for a complete newb like me. Also, I used TKIP encryption because that's what my router uses and I couldn't find any way to change it. I didn't need to enter my DNS information either.
Thanks for the help. I was about ready to give up on ubuntu because I refuse to use anything less than WPA.

---

### Post by bionnaki on 2006-08-29
great! good to know.

updating the driver isnt so bad, but if it works for you, then it works :D

---

### Post by gannic on 2006-08-30
Hello, my card is a wmp54g but identified itself as an RT61 - I presume thats differnt

---

### Post by lkh on 2006-08-30
Hi,

I have a RT25000 based card too and it works nearly perfect (WLAN is not good for online games). The driver from the serialmonkey is always looking for a config file "RT2500STA.dat" in "/etc/Wireless/RT2500STA". For me it was easier to edit only this file:

```
[Default]
ProfileID=myProfile
SSID=MYNET
NetworkType=Infra
PreambleType=Auto
AuthMode=WPAPSK
EncrypType=TKIP
WPAPSK=absolutelytopsecret

```

You can also use a Qt programm to create this file. But for this few lines ...

**@gannic**: use this driver: [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz) and don't forget to read the README.

---

### Post by God.Jr on 2006-09-01
well i did something along these lines too......it worked at my friends house but when  i try at home there is no internet conection but a strong *98%* signal strenght but there is no net.....completely puzzled.......i have put in the DNS and it still won't let me in......

[this was what i followed to get my wireless to work.....]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500")

---

### Post by AndyCooll on 2006-09-14
I too want to add my thanks for this HOWTO.

I've been using Ubuntu for about a year and gone through the various trials of wireless. When I got my laptop working with WEP I've been too afraid to make any further changes in case I broke it!!!

Anyway took the plunge tonight. Like ttenpas I just followed steps 1-3, and that was enough. Wireless network with WPA works like a charm!

Just want to mention that for many folk using WPA, the default encryption type is TKIP so you might need to edit this line accordingly to your the encryption type your router is using :
```
pre-up iwpriv ra0 set EncrypType=AES
```
(When my initial attempt failed it was because I hadn't changed this setting)

Also thought it might be worth mentioning that this bit of your copy and paste isn't actually necessary for getting your wireless card working:
```
# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
```

bionnaki ...once again thanks very much for your HOWTO.

:cool:

---

### Post by timwoolsey on 2006-09-16
> **gannic said:**
> Hello, my card is a wmp54g but identified itself as an RT61 - I presume thats differnt
my card identified itself as this too.  but i know i bought a card with the rt2500 chipset. so i continued along.  however i just did steps 1-3 because wireless is my only way of connecting to the web.  but when i rebooted kubuntu hung up on "Configuring Network Interfaces..." and never got into KDE. 

any ideas?

---

### Post by velvet_undies on 2006-10-06
> **timwoolsey said:**
> my card identified itself as this too.  but i know i bought a card with the rt2500 chipset. so i continued along.  however i just did steps 1-3 because wireless is my only way of connecting to the web.  but when i rebooted kubuntu hung up on "Configuring Network Interfaces..." and never got into KDE. 

any ideas?

Mine has done this to any ideas on why??

---

### Post by timwoolsey on 2006-10-06
velvet_undies:

sorry, i haven't made any progress or tried to troubleshoot this any more.  all in all i'm fed up with the poor wireless support in linux in general.  

if i get anything working i'll post it here to let you know.  please do the same for me.

~tim

---

### Post by bionnaki on 2006-10-25
ok. I have modified this how-to. things should work better now.

---

### Post by Erik. on 2006-10-25
Hi,
i will try this when i am home.. i hope it will work for me!!!
I do not use WPA protected but i use web
What do i need to change into my interface file?
And whit the channel do i need to enter the frequentie or do i need to enter the channel?
i know out of my head that i have chanel 11 into my linksys router.

---

### Post by timwoolsey on 2006-10-25
> **bionnaki said:**
> ok. I have modified this how-to. things should work better now.
will it work for edgy?

---

### Post by bionnaki on 2006-10-25
I havent tried yet. I cannot imagine it would be any different.

---

### Post by timwoolsey on 2006-10-26
it is different... the device is now "wmaster" not "ra"...

must be using a different driver in edgy?  

i tried just following your instructions but with the new device name and i had the error i mentioned earlier with my pc not booting, but stalling when it got to "Configuring Network Interfaces..."

---

### Post by bionnaki on 2006-10-26
I just did a fresh installation of edgy and I can confirm that this how-to works. I followed the instructions line by line and my wireless works great.

ra0 is still ra0. I have never heard of wmaster.

are you sure you have a wmp54g that uses the rt2500 driver?

---

### Post by bionnaki on 2006-10-26
> **velvet_undies said:**
> Mine has done this to any ideas on why??

> **timwoolsey said:**
> my card identified itself as this too.  but i know i bought a card with the rt2500 chipset. so i continued along.  however i just did steps 1-3 because wireless is my only way of connecting to the web.  but when i rebooted kubuntu hung up on "Configuring Network Interfaces..." and never got into KDE. 

any ideas?

I would go with what your computer identifies your chipset as, not what the linksys packaging says. As such, this how-to is not for you.

---

### Post by bionnaki on 2006-10-27
for rt61, try this [thread](http://ubuntuforums.org/showthread.php?t=132980)

---

### Post by Sonic Reducer on 2006-10-27
i just want to make sure, but this does work in Edgy right?

---

### Post by bionnaki on 2006-10-27
yes, works with edgy. just be sure to follow the guide line by line.

---

### Post by bklebel on 2006-10-29
ok i will try and explain this as best as i can.  

I am living in an apartment complex with wireless internet provided free by the apartment.  Its a unsecure access point so there is no WEP. 

brb :D

---

### Post by bionnaki on 2006-10-29
that should be easy to set up. follow the instructions [here](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#head-930554cc0b7ea23e53c5897ed13a336cf960f874) for setting that up. basically all you do is just open system/administration/networking/properties and enter your essid, set as dhcp, leave password blank, click ok, and activate. and do this:

> sudo gedit /etc/network/interfaces

and add 

> auto ra0

at the end.

should work now.

I do, however, recommend updating your rt2500 driver for better performance.

---

### Post by bklebel on 2006-10-31
It's so hard to explain what i am doing on a different machine.  I wish I could just copy and paste but that would be too simple wouldn't it.  Is there a way to easily take a screen shot of the terminal, then transfer with my jumpdrive??

---

### Post by bionnaki on 2006-10-31
yes, accessories>take a screenshot
and then save the files to whatever media you prefer
and transfer over/upload.

or just copy/paste and save into a .txt file
and transfer over

---

### Post by Gauss256 on 2006-11-06
I just did this with a fresh installation of Edgy and it works.  Like some others I was too gutless to update my drivers.  Plus my wireless connection was the only network connection on this machine, so there was a chicken and egg problem

Thank you very much for posting this information!

---

### Post by bionnaki on 2006-11-07
glad to see that it worked for you. cheers.

---

### Post by Sonic Reducer on 2006-11-22
so i had it working, it loaded fark.com, which is what i set as my homepage.

then i tried to update the driver, simply copy/pasting the line that was given, and it said it couldn't find an essential file. now i can't connect.

i rebooted and it works now. does this mean the driver got updated?

---

### Post by Hasen_A on 2006-11-30
[quote]
tar -xzf rt2500-cvs-daily.tar.gz
cd ./rt2500*/Module
make
sudo ifdown ra0
sudo cp ~/rt2500*/Module/rt2500.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/
echo "alias ra0 rt2500" | sudo tee /etc/modprobe.d/rt2500
sudo depmod
[/qoute]

when i try to $make in that directy i get a bunch of errors, how come?

---

### Post by bionnaki on 2006-11-30
you'll need to post what errors come up.

---

### Post by hammerzeit on 2006-12-05
Thanks, great job! worked like a champ on my new edgy install. :) 
one thing though, Network Manager still shows me as being disconnected, and the Networking Administration window shows the interface being disabled....even though I'm sending this using said interface. :-k 
oh I followed the directions 1-3 and then did a /etc/init.d/networking restart command.. thanks in advance

---

### Post by Blaze1024 on 2006-12-05
Thanks for the How to it worked great for me. 
I just added a wireless access point to my IPcop firewall. The system is somewhat complex. There are 4 subnets a Red, Blue, Orange and Green.  The Wireless side is Blue and for security reasons only has access to the Internet and is not allowed access to resources on the wired local intranet which is the Green subnet. If someone needs to transfer files to the local net they need to plug into the wired lan which is a switched gigabit Lan. The Orange subnet is where my webserver and mysql servers are located and they are also isolated from the local and wireless lans. The Red side is the direct connection to the Internet. 

I had wanted to add a wireless link for quite sometime but for security reasons was hesitant. your how to helped me resolve my last hurdle. It also showed me how to setup the rest of the wireless  computers so they would automatically connect to just our network.

---

### Post by Ackshiel on 2006-12-05
It worked like a charm.. Even then driver update.  Thanks a million!!

One last question though.  Like others, I too see the card as being disabled in the network admin tool.  Is this normal?  If so, why?

Cheers!

---

### Post by touchlikefire on 2006-12-05
Thanks a bunch for the tutorial, like a few others, I had suffered with WEP until now.

Also like others, I'm noticing in System->Administration->Networking that all my interfaces are shown as disabled.  Why is this?

---

### Post by bionnaki on 2006-12-05
Mine is enabled. Try enabling it and see what happens.

---

### Post by k1001001 on 2006-12-17
I've tried just about every tutorial I can find, including this one. I even tried to install my WUSB54g card, but I couldn't get that working either. My patience is running very thin. I get very close to getting it, but I just can't seem to connect wirelessly.

When I boot up and start up Firefox, it should load up a page. Instead I get the error message. So then I try to activate my wireless card:
```

~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:11:09:07:c4:d1
Sending on   LPF/ra0/00:11:09:07:c4:d1
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.2.43
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```
So apparently, something is awry here since I am not getting any DHCP offers, but I know my router has DHCP activated. Any suggestions? Do I need to post more information? Sorry if I seem short-tempered at the moment, but I've been working on this for about the entire weekend and everything I do seems to have done nothing.

---

### Post by bionnaki on 2006-12-18
just to make sure, you have a wmp54g that uses the rt2500 driver?

---

### Post by k1001001 on 2006-12-18
I have an integrated Ralink RT2500 802.11 wireless network card, and I also tried to install the WUSB54G USB unit, but both of them had the same result.

---

### Post by bionnaki on 2006-12-18
what about:

> 
sudo ifup ra0


can you ping anything?
ping yahoo.com

please post your /etc/network/interfaces and the output of these:

modinfo rt2500
ifconfig

---

### Post by k1001001 on 2006-12-18
sudo ifup ra0 has the same result as dhclient did.
```

$ sudo ifup ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:11:09:07:c4:d1
Sending on   LPF/ra0/00:11:09:07:c4:d1
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Pinging Google resulted in 'unknown host www.google.com'.

Here's the rest of the information:
/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

mapping hotplug
script grep
map eth0

auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "Goodwin"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="key"
pre-up ifconfig ra0 up

auto rausb0
iface rausb0 inet dhcp

```

modinfo rt2500
```

filename:       /lib/modules/2.6.15-27-386/kernel/drivers/net/wireless/rt2500/rt2500.ko
author:         http://rt2x00.serialmonkey.com
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 CVS 2005/07/10
license:        GPL
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
srcversion:     87483C74300BD5B978A24E4
parm:           ifname:Network device name (default ra%d) (charp)
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)

```

ifconfig
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:CE:DF:29
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:630389 (615.6 KiB)  TX bytes:54262 (52.9 KiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13372 (13.0 KiB)  TX bytes:13372 (13.0 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:07:C4:D1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1399860 (1.3 MiB)
          Interrupt:193 Base address:0xc000

```

Thanks for any help you can offer. I really appreciate it.

---

### Post by bionnaki on 2006-12-18
your /etc/network/interfaces file is not as it should be. see the first page and *only* have what the example has in it. copy it exactly and delete whatever else is in that file.

---

### Post by k1001001 on 2006-12-18
I copied the file. Wireless still does not work. sudo ifup ra0 still brings up the same error. Maybe there's something else I have to do to become connected?

Or maybe I just need to fresh install from the Live CD? I have a feeling that I've tried so many methods that I've permanently screwed up my wireless drivers.

---

### Post by bionnaki on 2006-12-18
yeah, I recommend starting fresh. I've never seen such an error before. who knows what you've done to your system.

---

### Post by Aramis on 2006-12-22
**What a great How-To thank you so much!**

For months now I have been struggling with my Hawking 54G Wireless Card (PCMCIA intreface). In the first few days of switching to Ubuntu I did manage to make it work with my Wireless Network (WPA+TKIP) but a Kernel upgrade flushed that out, and now it seems that the RT2500 drivers are mature enough to support WPA w00t !

Well thank you for the good work! 

Ar@mi$ Happy Chappy

Note:
OS : Ubuntu 6.10 Edgy Eft
Wireless Drivers not updated !
Wireless Card with PCMCIA connection interface

---

### Post by esapfnSW on 2006-12-23
Hello. I am totaly new, i mean as fresh as one ever could be. My only experience prior to now is using Suse on a PC at work and messing around with ubuntu with my laptop. 
  Now, on my laptop everything worked out of the box. It was awsome, I could install most stuff I needed without any problem. But, it is mainly a work PC so I can't remove XP.

 But looking at all the possibilities I decided to convert my desktop to Linux. As long as Wow works then I have all I need. ;) . So I get an ekstra hdd (not to mess up my XP installation yet) and install Ubuntu. Alas, as quite a few other people here, my WlAN card won't work...  I now the router is fine because I am writing this from my laptop not one meter from my desktop.

 Ayway, being a total newb I have a lot of problems doing the simplest action on the pc, especially without being able to get anything from the net. And I can't connect it any other way since I am using a wireless router that is not in my home...
_______________________________________________________________
**THIS IS WHERE THE TROUBLESHOOTING STARTS**

First of all I checked i my device is detected. Running ```
sudo lspci
``` I get this:
> 02:05.0 Network controller: Ralink RT2561/RT61 802.11g PCI
So I presume that it detects my card.

 I then check the device manager:
Under > RT2561/RT61 802.11g PCI I Get "*Netwoking Interface*" and "*Unknown Device"*. And When I check the info it finds that it is a Lynksis Ralink card, but the Device Type, Capabilities (under Device) and OEM Product (under PCI) are marked as unknown.

 Using a floppy disk i have the latest RT61_Linux_STA_Drv1.1.0.0.tar.gz (currently in my home directory) and I have no idea how to make this work since I can't get any program from the web.

 Well, this is the only relevant info that I can think of for now. I know very little of the terminal since I am used to do most stuff from the GUI (which works just fine as long as one is connected to the net), so if you have an idea on how to help me installing the drivers on a pure out of the box copy of Edgy with no means of getting any program, I would much apreciate your help!

---

### Post by Sonic Reducer on 2006-12-30
so i'm trying this again on my computer, the drive completely crashed (as in the way a plane does, it wouldn't even spin up)

lucky i got a WD1600YJS for christmas huh?

so this is a copy/paste of the **sudo gedit /etc/network/interfaces** file i saved.
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0
auto ra0

iface ra0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "Jones Wi-Fi"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="\GZixsvJ'>%I-gtDroKL{fX}D.khNSW#N_%CD`w)~@yncKCp}HI,"
pre-up ifconfig ra0 up

under **Connections** it says "*wireless connection: The interface ra0 is not configured*". i seem to remember this still saying it was not active even while i was online before.

can anyone help me here? what am i doing wrong?

---

### Post by Sonic Reducer on 2007-01-03
ok, i've tried everything i can think of. i unplugged my wii (to prevent an IP conflict) updated the WRT54G's firmware to the most current, changed the broadcast to B-Only. i am all out of ideas.

i updated the info in my previous post and am posting again to send out another email to everyone who got theirs working and bump this to the top.

i need help, i'm out of ideas

---

### Post by mightyteegar on 2007-01-27
For those who have followed the instructions in this how-to and still can't get things to work properly, I have a suggestion.

Recently I "did some stuff to my computer" (some updates and installed a couple of packages) and my wireless stopped working.  I tried every single how-to I could find and nothing worked.  

Then I stumbled across this file on my system:

```
/etc/Wireless/RT2500STA/RT2500STA.dat
```

which contained some lines related to AuthType and some other things.  Figuring what the heck, I deleted it (actually, moved it to /root), checked to make sure /etc/network/interfaces was properly configured as described in this how-to, and then ran 

```
sudo ifdown ra0
sudo ifup ra0
```

and my wireless was back!  So if you're having trouble, check for this file and try removing it.

---

### Post by Sonic Reducer on 2007-02-01
now first off i'll admit my mom has been using my computer, so we can assume there is something wrong here i don't see

now my computer isn't going on the internet, i can connect to the router, even change settings and see them on my laptop when i refresh the link to the router (its a WRT54G) but it simply will not open a website.

it will say its loading for about 10 minutes, then sy it cannot be displayed. we just recently got the comcast hi-speed cable (6 megs!!!) and it stopped working about then, but i am typing this on my laptop over wireless connection! how come my laptop works (it's XP) and my desktop doesn't (Dapper Drake)?

---

### Post by bionnaki on 2007-02-08
sonicreducer: your WPA password is not good. just stick with alphanumeric. example: u8jf9kfe393589fjkd934kgf

---

### Post by bionnaki on 2007-02-08
SebZeNorse: you dont use the rt2500 driver. try the rt61 driver instead: [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)

---

### Post by Sonic Reducer on 2007-02-09
> **bionnaki said:**
> sonicreducer: your WPA password is not good. just stick with alphanumeric. example: u8jf9kfe393589fjkd934kgf

i'd like to be able to get online first...

---

### Post by bionnaki on 2007-02-09
change your password then.

---

### Post by Sonic Reducer on 2007-02-09
> **bionnaki said:**
> change your password then.

i can't figure it out man, i can connect to my router no problem (connect to 192.168.1.1), but then it won't load webpages.

---

### Post by bionnaki on 2007-02-09
sounds like a dns problem.
open the terminal and enter

> 
ping [www.google.com](www.google.com)


see if that works. if not try:

> 
ping 66.249.93.104


if that works, then you have a DNS problem.

did you edit your resolv.conf like the howto says?
post your /etc/resolv.conf.

---

### Post by Sonic Reducer on 2007-02-13
it was a DNs problem, they got changed when we switched to comcast i assume

---

### Post by jugger18 on 2007-02-19
Will this affect my ability to use non WPA secured access points.  Specifically at home we use a WPA secured AP, but I also take my laptop to school which uses an unsecured netwrok that directs you to a webpage to log in using my university ID.  If i set up the interfaces file for home, will it make me unable to use it at school?

---

### Post by Arko on 2007-04-01
After hours of trying, finally I got my DWL-G510 card working with rt61. I have tried everything I found on tutorials and forums and did the following script that I put in /etc/init.d directory to start on boot (Ubuntu 7.04):

```

#!/bin/bash
ifconfig ra0 192.168.0.128 up
route add default gw 192.168.0.1 ra0
route del default
ifconfig ra0 down
ifconfig ra0 192.168.0.128 up
iwconfig ra0 mode managed
iwpriv ra0 set AuthMode=WPAPSK
iwpriv ra0 set EncrypType=TKIP
iwconfig ra0 essid MYHOME
iwpriv ra0 set WPAPSK=d23fd94e6c344514adce7549591dc7b265426e793aabb13b767b06958c9c7b1c
iwconfig ra0 essid MYHOME
ifconfig ra0 192.168.0.128 up
route add default gw 192.168.0.1 ra0

```

But there is still a problem: about 50% of boots I do not get Internet working. Then I have to run "route del default gw; ifconfig ra0 down; ifconfig ra0 192.168.0.128 up; route add default gw 192.168.0.1 ra0" as root to get it working again. Eventually I have to type that three or four times, which is very annoying.

Please, any help for that?

---

### Post by AlanV on 2007-04-09
I was able to get my Hawking Tech HWP54g pci card to work using the STATIC instructions. Just would not work with the DHCP instructions. Router is Linksys WRT54g.

I am happy as it is. Just wanted to share my experiences!

Thanks!

---

### Post by nuttiplutt on 2007-04-13
I've moved this post to "networking & Wireless"

---

### Post by raul_ on 2007-05-04
This didn't work for me. When i tried to do "/etc/init.d/networking restart" it said "ignoring unknown interface ra0=ra0" . So i tried "iwconfig <TAB>" and one of the choices was "rausb0". I replaced ra0 with rausb0 everywhere and still nothing. I didn't have those directories you said to move the files to, i had them in /lib/modules/..../ubuntu/wireless/....

i created the ones you said and nothing....

I have a d-link dwl-g122 vB1 . Could you help me here?

---

### Post by Sonic Reducer on 2007-05-05
is there an easier way to do this? perhaps with NDIS wrapper or network manager?

i only ask because i installed ubuntu on an external HDD on my laptop and network manager installed easily and wifi worked no problem. the chipset on my lappy is a IPW-3945ABG though, maybe it only appliesto certain chipsets

---

### Post by skandia2 on 2007-05-06
> **k1001001 said:**
> I've tried just about every tutorial I can find, including this one. I even tried to install my WUSB54g card, but I couldn't get that working either. My patience is running very thin. I get very close to getting it, but I just can't seem to connect wirelessly.

When I boot up and start up Firefox, it should load up a page. Instead I get the error message. So then I try to activate my wireless card:
```

~$ sudo dhclient ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:11:09:07:c4:d1
Sending on   LPF/ra0/00:11:09:07:c4:d1
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
Trying recorded lease 192.168.2.43
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.

--- 192.168.2.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```
So apparently, something is awry here since I am not getting any DHCP offers, but I know my router has DHCP activated. Any suggestions? Do I need to post more information? Sorry if I seem short-tempered at the moment, but I've been working on this for about the entire weekend and everything I do seems to have done nothing.


Was this DHCP problem resolved?
I have exactly the same the same problem as above using Feisty on an ACER laptop with a Belkin PCMCIA card using the RT2500 chipset. 

I tried the fixed IP approach  and the results are odd!

Checking the Wireless AP (from another PC) indicates that the Laptop WIFI card is connected and authorized but I cannot ping any addresses from the laptop and I cannot ping the laptop from any other PC!

Has anyone managed to get Feisty and a RT2500 base d WIFI card working with a WPA, or a WPA2 encrypted network?

---

### Post by w4xwa on 2007-05-14
I have been struggling with Ubuntu wireless for 2 months.  I finally got it to work by following this HOWTO.  I removed network-manager and network-manager-gnome first.  I am running Feisty.  Worked perfectly on the first re-boot.  Thank you so much.  I really appreciate your help.  I think this proves there is a problem with Network Manager in Feisty.  Jim

---

### Post by Nadstar on 2007-05-15
Hi, this has even prompted me to write my first post! Worked for me on Feisty too....after weeks of trying. Thank you, I was just about to try Mandriva or SUSE! In a nut shell I did this: 

1.) Updated to serial monkey driver 
2.) Uninstalled Network Manager
3.) Installed RutilT
4.) Deleted /etc/Wireless/Ralink/
5.) edited /etc/network/interfaces and /etc/resolv.conf with info at beginning of this thread

Cant believe it actually worked - cheers!!!

---

### Post by mazz on 2007-05-21
> **k1001001 said:**
> sudo ifup ra0 has the same result as dhclient did.
```

$ sudo ifup ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ra0/00:11:09:07:c4:d1
Sending on   LPF/ra0/00:11:09:07:c4:d1
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
Pinging Google resulted in 'unknown host www.google.com'.

Here's the rest of the information:
/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

[COLOR="Red"]mapping hotplug
script grep
map eth0[/COLOR]

auto ra0
iface ra0 inet dhcp
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up ifconfig ra0 up
pre-up ifconfig ra0 down
pre-up iwconfig ra0 essid "Goodwin"
pre-up iwconfig ra0 mode Managed
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="key"
pre-up ifconfig ra0 up

auto rausb0
iface rausb0 inet dhcp

```

modinfo rt2500
```

filename:       /lib/modules/2.6.15-27-386/kernel/drivers/net/wireless/rt2500/rt2500.ko
author:         http://rt2x00.serialmonkey.com
description:    Ralink RT2500 802.11g WLAN driver 1.1.0 CVS 2005/07/10
license:        GPL
vermagic:       2.6.15-27-386 preempt 486 gcc-4.0
depends:
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
srcversion:     87483C74300BD5B978A24E4
parm:           ifname:Network device name (default ra%d) (charp)
parm:           debug:Enable level: accepted values: 1 to switch debug on, 0 to switch debug off. (int)

```

ifconfig
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:CA:CE:DF:29
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:630389 (615.6 KiB)  TX bytes:54262 (52.9 KiB)
          Interrupt:177 Base address:0x1400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13372 (13.0 KiB)  TX bytes:13372 (13.0 KiB)

ra0       Link encap:Ethernet  HWaddr 00:11:09:07:C4:D1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1399860 (1.3 MiB)
          Interrupt:193 Base address:0xc000

```

Thanks for any help you can offer. I really appreciate it.

Ok the lines i highlighted you need to delete, they are not needed.

---

### Post by t_tovenaar on 2007-07-10
I have installed Feisty and my WMP54G v4 worked right out of the box! There is a catch however... the wireless connection works as long as I use only WEP encryption. I cannot seem to get it working with WPA.

Like many others I have tried quite a few guides and howtos but none of them yielded the expected result.
This one sure looks like a good howto (but so do the other guides ;)). Nevertheless I am gonna try this one at home (currently at work).

I will keep you informed!

---

### Post by t_tovenaar on 2007-07-10
):P Here I am, surfing the net using WPAPSK on Kubuntu Feisty!

Following steps 1, 2 and 3 did the job for me :mrgreen:
I didn't even had to do a reboot but just ifdowned and ifupped my wireless interface.

If I could I would give you kudos; thank you for this howto! =D>  =D>


[EDIT: Let's see if I can still get online after a reboot...]
[EDIT: And I can! Whoohoo...]

---

### Post by acabre on 2007-08-11
Thanks again to bionnaki!

Steps 1-3 worked flawlessly on a fresh install of Ubuntu 7.04 (Fiesty Fawn) for amd64 with a linksys wmp54g. 

Excellent, since I spent a couple days screwing with RaConfig2500 et al until I found this. So simple!

-acabre

---

### Post by andrew_howlett on 2007-09-04
Worked for me. I had to edit /etc/dhcp3/dhclient.conf and change the timeout to 60 seconds. But that might  be my base station, not the rt2500 card.

later,
andrew.

---

### Post by kebajonathan on 2007-09-09
Hi,

I need to be able to connect to different networks using my rt2500, and it would be great if this was possible using networkmanager. So is there a possibility to do so? If not, why? Thanks for your answers

---

### Post by booyip on 2007-09-23
Hello ubuntu - I'm new.  :smile:

I dual boot with XP on a x86 system, and although the WPA wireless is fine with XP, when I booted with Ubuntu it wouldn't connect at all.  I followed all the steps from the 1st post, including the driver update.  Also removed Network Manager, and tried a static IP, still no joy.  And then I found out why....

Ultimately, the MAC filtering on my router was for some reason preventing the connection in Ubuntu - even though the same MAC-address was successfully connecting via XP.  I disabled this, and now have connectivity from both OS', using WPA.  I'm very happy, as was about to buy a new wireless card.  No need now.

I suppose the lesson I wanted to share is to remove all security measures on routers/modem's, even if there seems no logical reason to do so.  I am using an otherwise great Dynalink RTA1025W, if anyone needs to know.

Just thought I'd share this nugget, as newbs like me can be flummoxed by the simplest thing.  Thanks to all who have contributed in this thread, as I pretty much followed it start to finish.  So many people selflessly wanting to help because they believe in Ubuntu.  I really want to ditch XP, and this community is going to make it a whole lot quicker and easier.  Thanking You.  :KS

---

