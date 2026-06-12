---
title: "Getting wireless card to work"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by random turnip on 2008-10-20
I have a HP Pavillion dv9000 and im having trouble getting Ubuntu Hardy to work with the Wireless Card (802.11 a/b/g).

Anyone got any ideas?
I'm a noob to Linux, so please give simple instructions/solution.

Thanks very much for any help!

---

### Post by Kevbert on 2008-10-20
First of all we need to find out what the wireless chipset is as you will need firmware drivers for the wireless adapter.  Go to Applications-Accessories-Terminal and enter the following
```
lspci
ifconfig
```
Please copy the outputs for each command in turn by highlighting the output with the mouse, then press Ctrl-Shift-C (to copy) and Ctrl-V to paste here in a new post.

---

### Post by tsedrey on 2008-10-20
Same boat as this guy...I can see networks, but I can't connect to any of them. I've been searching for days,,,thank you.


00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)


ifconfig:
david@david-laptop:/usr/bin$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1f:e1:c7:44:b2  
          inet6 addr: fe80::21f:e1ff:fec7:44b2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1c:25:ba:c8:f1  
          inet addr:129.81.89.116  Bcast:129.81.89.127  Mask:255.255.255.192
          inet6 addr: fe80::21c:25ff:feba:c8f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6538 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5602 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6427794 (6.4 MB)  TX bytes:855287 (855.2 KB)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-1F-E1-C7-44-B2-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110019 errors:0 dropped:0 overruns:0 frame:267456
          TX packets:491 errors:15 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:12121002 (12.1 MB)  TX bytes:22738 (22.7 KB)
          Interrupt:17

---

### Post by tsedrey on 2008-10-20
PS I am on a Thinkpad (T61) with a :
  ThinkPad 11a/b/g Wireless LAN Mini Express Adapter

This is a WiFi Adapter that is installed in a Mini-PCI Express slot
Features

    * Chipset: Atheros AR5006EX (As printed on card AR5BXB6) or AR5212
    * Integrated Mac Processor and Radio Chip: Atheros 5423
    * IEEE Standards: 802.11a, 802.11b, 802.11g
    * PCI ID: 168c:1014 


...I believe.

---

### Post by Kevbert on 2008-10-21
> **tsedrey said:**
> PS I am on a Thinkpad (T61) with a :
  ThinkPad 11a/b/g Wireless LAN Mini Express Adapter

This is a WiFi Adapter that is installed in a Mini-PCI Express slot
Features

    * Chipset: Atheros AR5006EX (As printed on card AR5BXB6) or AR5212
    * Integrated Mac Processor and Radio Chip: Atheros 5423
    * IEEE Standards: 802.11a, 802.11b, 802.11g
    * PCI ID: 168c:1014 


...I believe.

Can you try this command as it doesn't look as Ubuntu even sees a wireless adapter
```
lshw -C network
```
You need firmware drivers to be installed as the wireless is in standby mode.
If it is you may like to look at this [COLOR="Red"][post]("http://ubuntuforums.org/showthread.php?t=792158")[/COLOR]. Please note that Atheros wireless is not the most Ubuntu friendly adapter and it's possible that you may get more problems. Good luck.

---

### Post by tsedrey on 2008-10-21
*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:ba:c8:f1
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.3-0 ip=129.81.89.116 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:e1:c7:44:b2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by tsedrey on 2008-10-22
> **Kevbert said:**
> Can you try this command as it doesn't look as Ubuntu even sees a wireless adapter
```
lshw -C network
```
You need firmware drivers to be installed as the wireless is in standby mode.
If it is you may like to look at this [COLOR="Red"][post]("http://ubuntuforums.org/showthread.php?t=792158")[/COLOR]. Please note that Atheros wireless is not the most Ubuntu friendly adapter and it's possible that you may get more problems. Good luck.


Hm, I tried that fix and no luck. Any other ideas?

---

### Post by Kevbert on 2008-10-22
An old one to [[COLOR="Red"]try[/COLOR]]("http://ubuntuforums.org/showthread.php?t=38972"). Again it's quite involved. It looks like [[COLOR="Red"]Madwifi[/COLOR]]("http://madwifi.org/") is your best bet for the dreaded Atheros adapters.

---

### Post by random turnip on 2008-10-26
I'm begining to think it isn't.

I've had numerous problems with getting Ubuntu to work with my wireless driver, I've done trouble shooting, followed loads of advise and even asked a professional to help.

So seriously, does Ubuntu even support wireless internet?
Got any ideas that i might not have tried?
It could be the simpelist thing cos I'm a total noob at Linux.

[More info on my problems here]("http://www.gamelair.com/gameforums/linux-general-discussion/15579-little-help-ubuntu-please.html")

---

### Post by hiasakite on 2008-10-26
Yes...  see my reply here:

[http://ubuntuforums.org/showthread.php?p=6036081#post6036081](http://ubuntuforums.org/showthread.php?p=6036081#post6036081)


The short is- I've been using Ubuntu 8.04 for 5 days on an old Dell C610 laptop with new harddrive - I plugged a Belkin F5D7050 wireless usb stick in..  and once I'd figured out how to find the wireless networks tab etc and entered by wifi password in, it 'just worked'....

- I've no idea how, it just did- bear in mind I have not installed any drivers etc-    

...maybe because mine's a new install or something?

---

### Post by beidache on 2008-10-26
> **random turnip said:**
> I'm begining to think it isn't.

I've had numerous problems with getting Ubuntu to work with my wireless driver, I've done trouble shooting, followed loads of advise and even asked a professional to help.

So seriously, does Ubuntu even support wireless internet?
Got any ideas that i might not have tried?
It could be the simpelist thing cos I'm a total noob at Linux.

[More info on my problems here]("http://www.gamelair.com/gameforums/linux-general-discussion/15579-little-help-ubuntu-please.html")
Check this one that works for me after 4 day figth

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Hope hel you with your problem

---

### Post by JeppeM on 2008-10-26
It's working fine for me on my work laptop... i get up to 20 MB/s in the office network, so i'd say that it works like it should...

But i agree, there's a lot of people having issues with wifi, but i dont think that ubuntu is to blame, it's rather the producers of the hardware sadly... but hopefully, once the marketshare of ubuntu starts to raise, they'll get much more into supporting linux :)

---

### Post by nephilim2k2k on 2008-10-26
works perfectly for me. I got home, work, gfs house and friends house wireless networks saved for when i go to the specific places. admittedly it did take me about 1 hour per location to get them set up and saved but once done it worked perfectly.

---

### Post by caeroe on 2008-10-26
It was working fine, after countless hours trying to get it to work.  Then Update Manager killed my wireless with the 2.6.24-21 update.  I moved back to "-19", and my wifi light is back on.  However I can no longer detect any network.  

I just gave up, and am shopping for another OS to throw on my notebook.  Wireless should just work these days, I shouldn't have to dig through hundreds of pages of topics and possible fixes, and mash in hundreds of commands into a terminal.  Is it 1992 in here?

---

### Post by Ayuthia on 2008-10-26
> **random turnip said:**
> I'm begining to think it isn't.

I've had numerous problems with getting Ubuntu to work with my wireless driver, I've done trouble shooting, followed loads of advise and even asked a professional to help.

So seriously, does Ubuntu even support wireless internet?
Got any ideas that i might not have tried?
It could be the simpelist thing cos I'm a total noob at Linux.

[More info on my problems here]("http://www.gamelair.com/gameforums/linux-general-discussion/15579-little-help-ubuntu-please.html")

Can you go into the Terminal and try the following:
```
sudo modprobe -r b43 b44 b43legacy ndiswrapper bcm43xx wl
sudo modprobe ndiswrapper
sudo iwlist scan
```Does it return any wireless sites?  If not, please go back to the Terminal and post the results of:
```
lspci -nn
lshw -C network
ndiswrapper -v
ndiswrapper -l
cat /etc/init.d/wifiFix.sh
```
This will provide us the information about your wireless card, the version of ndiswrapper you are using, if there are any problems with the driver in ndiswrapper, and what the script that you installed is doing.

---

### Post by Mic_Droz on 2008-10-26
Everything was so perfect when I initially installed Ubuntu, but then i decided to update the kernel like the arrow in my task bar told me to...

The lesson here is not to listen to red arrows in your taskbar - they are the technological equivalent of Satan...

In all seriousness though, I should have just kept the kernel at -18, because -21 ruined suspend/resume wireless for me... and I have no idea why. 

For those that have no more wireless since the kernel update, switch to the older kernel, and re-download all the restricted-driver kernel additions for the new kernel - it *should* work. god knows that I've had to do it a few times now, and am frankly baffled that I have to do that at all - shouldn't the update manager grab all the new replacements for the old kernel additions you had? Maybe I'm just crazy...

---

### Post by WileyHunter on 2008-10-27
Yeah MD, same here...  I installed Ubuntu on a Compaq Laptop for a guy I used to work with.  Got him all set up with everything he'd need.  My last week at work, he asks about the "updates", so I said sure might as well get them done while we are working together...  Lost WiFi...  

Now I'm sitting here with his Compaq on my dining room table with no WiFi, and for some reason unknown to me, no Hardwire LAN either...

I've installed both 7.10 (again) and 8.04 tonight and neither of them are fixing my problem...  I know I had this working 3 weeks ago, what a PITA.

Well, I will be right back at this again tomorrow.  I know they can't make this a walk in the park for everyone with auto recognition and install of only the components we need, but it sure would be nice for the HW companies to get with the program and help support their product within the OS.

As was said earlier though.  Stay Away from the Red Arrow!!!:lolflag:

---

### Post by random turnip on 2008-10-27
Is there a chance this will be fixed with the release of 8.10?
Cos, judging by this site, it's a pretty common occuring problem.

Also, @  Ayuthia I will try this when i get chance and post the exact results here, thanks for the code/help so far!

---

### Post by knix on 2008-10-27
I'm using intrepid, and wireless is working nicely. It features wl installed by default.
I took a look at your link, and my comment is that the "broadcom installer" in the screenshot is not super reliable.

So, from the start, here's what to do:

open a terminal
```
sudo lshw -C net
```
if you get information about a broadcom wireless card, then good. If you get information about an intel wireless card, then that's why the broadcom drivers won't work.
If it is broadcom, you have a couple options: wl, or ndiswrapper.
ndiswrapper uses windows drivers, and wl is native. I prefer wl. It can be simpler too. Also, ndiswrapper doesn't do too well with the latest broadcom cards.
Anyhow, use synaptic or apt to update your system, because in hardy wl is only in the later kernels. Or you can install intrepid (I would still update). A fresh install might not hurt in hardy as well.
```
sudo apt-get update
sudo apt-get upgrade
```
now, make sure linux-restricted-modules is installed.
next, load the wl driver
```
sudo modprobe -r b43
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe -r wl
sudo modprobe wl
sudo modprobe b44
```
now, check whether it works
```
sudo iwlist scan
```
If it works, great. If not, then
```
sudo lshw -C net
```
check and see if you driver is listed as wl.
if not, then
```
lsmod | grep wl
```
you may have to modprobe wl twice.
or not modprobe -r wl.
you can add the modprobe lines to your /etc/rc.local without the sudos


If you want to use ndiwrapper, that's a little less simple. You will need to install ndiswrapper-common and ndiswrapper-utils. You can install ndisgtk to install the drivers graphically.
After you install that stuff, you will need to make sure you ahve the windows drivers in a folder. cd into that folder (in a terminal), then install the driver
```
sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -m
```
then all the modprobing from above, just replace wl with ndiswrapper in the commands.

good luck. also, for ndiswrapper, it helps to have the drivers for your specific card (i.e., if you have a dell, get the divers for the dell card)

that said, I like to use wl, although if you connect in the command line you will need to put "mode Managed" in your iwconfig line.

After installing either driver, run
```
sudo iwlists scan
```
to make sure it works.

---

### Post by Yarbo on 2008-10-27
I had some problems getting Wi-fi enabled on a Dell Laptop, but it only took me about half an hour of searches using Google and on these forums to find a solution.

If it takes a few days to get it working, it may just be that the wi-fi device in your laptop has no Linux drivers, in which case getting it to work might be tough.

---

### Post by random turnip on 2008-10-31
I bought this wireless card off the internet which stated it has the ability to run on any Linux distribution, so yesterday it arrived, i shoved the CD in as it told me to, and i looked in the setup files, only to find drivers for almost every type of Linux except for Ubuntu.  Is there a chance that if I installed the files for a different distribution it would also run on my Ubuntu?

---

### Post by Mark224 on 2008-10-31
I'm a newbie to Ubuntu but it is based on Debian.  I would try the Debian drivers and see if this works.

---

### Post by random turnip on 2008-10-31
Ah, Debian was one of them that ws included, so I'll try that, thanks very much!

I'll change to solved if it works.

---

### Post by random turnip on 2008-11-06
I have never managed to get my wireless internet working on my laptop.  Is it possible that if I upgrade to 8.10 it will start working?
Or am I just speaking non-sence?

---

### Post by LowSky on 2008-11-06
8.10 might help but I dont know what wifi card your using, could you help us out with that, maybe we can get it running under 8.04 for ya.

in terminal type ```
 lspci
```

---

### Post by th89 on 2008-11-06
I would say its quite possible. I had Ubuntu 8.04 installed previously on this laptop, and I had to use ndiswrapper and blacklist stuff, and in general a big pain, and it wasnt that great once it was working (painfully slow re-connect times). When I did a fresh install of Ubuntu 8.10 it listed the correct drivers as a Proprietary Driver, and once I enabled it through the interface and rebooted, its worked every since. Give it a shot. Try loading up the live CD and see if it detects your wireless, of if its listed in the Restricted Drivers list. You'd only be out one CD, and 30-60 mins of time spent downloading it.

---

### Post by bumanie on 2008-11-06
If it's an atheros wifi card, it won't work without extra configuring - strangely, it worked in beta version, but a change was made s
during RC version and I've only been able to get it work with ndiswrapper. I have read it can be enabled via backports, but have not tried.

---

### Post by nhasian on 2008-11-06
in the release notes it says if you have an Atheros or Intel wifi adaptor to install the intrepid backports.  you dont need to use the ndiswrapper ;)

---

### Post by random turnip on 2008-11-21
Kinx, I entered the first command into the terminal and got this result...

```
paul@paul-laptop:~$ sudo lshw -C net
[sudo] password for paul: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:8d:bf:87
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.36 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: da:28:d4:e9:70:ed
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
paul@paul-laptop:~$ 

```

When I did this I was connected to an eithernet connection.

---

### Post by random turnip on 2008-11-27
*BUMP*
Sorry for bumping, but I could really di with help, I need the wireless to work on my laptop, any more help will be greatly appreciated!

---

### Post by darthfruitloop on 2009-11-23
I have the same laptop, simple fix, hook it to a wired connection and it will detect your "restricted drivers" and from there you install them and BAM it works :) 

hope this helps

---

