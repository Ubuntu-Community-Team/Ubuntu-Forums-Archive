---
title: "trying to share a wirless connection between ubuntu machines"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by 118118 on 2011-11-24
hi,

using an ethernet connection. 
i have set up network manager so that there is a wired connection that shares the internet on the machine with internet access but i do not know how to access it on the second machine - i do not yet have internet access on it.

thanks for any help.

---

### Post by cavh on 2011-11-24
You need a crossover cable between the two machines, I think, not just a standard Ethernet cable - see [http://en.wikipedia.org/wiki/Ethernet_crossover_cable]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")

---

### Post by 118118 on 2011-11-24
i have already managed to share files with another computer with a standard ethernet cable and thought that a crossover cable was no longer needed in general.


i do not even know if the machine without internet [the desktop] connection has an ethernet card, though it has a socket. might i be able to share an internet connection with firewire - because i have that cable and know that the desktop has a firewire card.


hope that all made sense!

---

### Post by sudodus on 2011-11-24
Do you want a wired or wireless connection? I am thinking of the title of your thread.

Do you have a router, or do you want to connect directly between the computers?

Please check if there is an ethernet card in that computer! You can buy one if necessary, it is not that expensive. Anyway, I think that is is complicated to use firewire in linux.

---

### Post by 118118 on 2011-11-25
> **sudodus said:**
> Do you want a wired or wireless connection? I am thinking of the title of your thread.

Do you have a router, or do you want to connect directly between the computers?

Please check if there is an ethernet card in that computer! You can buy one if necessary, it is not that expensive. Anyway, I think that is is complicated to use firewire in linux.
i was asking about sharing with ethernet a wireless internet connection.
i want to connect the two computer to one another with just an ethernet cable.
i do not know how to check that. does anyone want to confirm that using firewire would be impractical?

---

### Post by sudodus on 2011-11-25
The standard way to share an internet connection is via a router. There are small boxes with dedicated hardware and software for that purpose. It is also possible to make a linux computer do the job, but ***I*** can't do it. You need to know how to run a server and configure the services needed for sharing the internet. I would say it is easier to connect directly between the computers.

Please post the output of the terminal command
```
ifconfig
```
This should show if you have a working ethernet card or chip.

---

### Post by 118118 on 2011-11-25
i don't understand your last post - am i not directly connecting two computers with an ethernet cable?
there seems to be a very simple tutorial on how to do exactly what i want [to share a computer's wireless internet connection via ethernet to a second computer] [http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/](http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/) but it doesn't work.

```

eth0      Link encap:Ethernet  HWaddr 88:ae:1d:1e:7a:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21248 (21.2 KB)  TX bytes:21248 (21.2 KB)

wlan0     Link encap:Ethernet  HWaddr c4:46:19:1d:9c:a1  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c646:19ff:fe1d:9ca1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30460 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29659447 (29.6 MB)  TX bytes:5569236 (5.5 MB)

```

---

### Post by sudodus on 2011-11-25
Thanks for sharing that interesting link :KS

I have no idea why it is not working. Are you sure that you do not need a cross-over cable?
**[COLOR=SeaGreen]Let us hope that someone reading this knows about it and can  tell, if should work also for the present Ubuntu version or what scripting or tweaking is actually  doing the job.[/COLOR]**

*Edit: Yes, you have both wired and wireless connections on this computer. What about the other one? And which one is the 'server'?*

---

### Post by mlentink on 2011-11-25
So you have an ethernet card as well as a WiFi-adapter. How do you connect to the internet? With the wifi? If so, There must be a wireless router on the other end, and it would be just as easy to install a wifi card in the second computer and connect with the router as well.

---

### Post by 118118 on 2011-11-25
both computers have a wireless card but the one in the destop that i quoted above does not detect the wireless signal. i think it may be because it's too weak, though i'm not at all sure!

---

### Post by sudodus on 2011-11-25
Can you move the wireless router / gateway / access point (the device that you are connecting to in order to reach the internet)?

Or move the computer closer, to find out if it is the signal strength?

---

### Post by 118118 on 2011-11-25
wait, i copy and pasted the output from the wrong computer above.
here is the correct output

```

eth0      Link encap:Ethernet  HWaddr 00:25:22:c9:3e:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31600 (31.6 KB)  TX bytes:31600 (31.6 KB)

wlan0     Link encap:Ethernet  HWaddr f4:ec:38:d0:40:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by 118118 on 2011-11-25
> **sudodus said:**
> Can you move the wireless router / gateway / access point (the device that you are connecting to in order to reach the internet)?

Or move the computer closer, to find out if it is the signal strength?
not without annoying the owner of the router.

---

### Post by sudodus on 2011-11-25
This one seems to have both wired and wireless LAN up and running. No data transfer is reported in contrast to the other one (in post #7, where several MB has been transferred  via wlan0).

Maybe you can move your equipment to find out if you can get a wireless connection to both computers?

---

### Post by sudodus on 2011-11-25
> **118118 said:**
> not without annoying the owner of the router.
I see ;-)

---

### Post by 118118 on 2011-11-25
my twin brother - he's happy to let me use his connection but is kind of annoying...

---

### Post by 118118 on 2011-11-25
hi,

THIS thread for trying to get a wired connection running and
this [http://ubuntuforums.org/showthread.php?t=1845824&page=4](http://ubuntuforums.org/showthread.php?t=1845824&page=4) one for the wireless connection.


thanks!

---

### Post by 118118 on 2011-11-26
hi,

no help with this? i'm not piggybacking!

---

### Post by sudodus on 2011-11-26
Maybe it would work if you have a local router between your two computers. I think it is important that there is proper management of the network addresses, and a router is doing that. Maybe you can borrow a router to test if it helps get your connection working. Click on the thumbnail to look at the attached picture!

---

### Post by anewguy on 2011-11-27
You shouldn't need a router.  All you should need is internet connection sharing.  This would in your case entail 2 computers connected via a hardwire ethernet cable and 1 of those computers being connected wirelessly to the net.

If nobody has suggested it yet, or if you haven't read it, see the following link:

[https://help.ubuntu.com/community/Internet/ConnectionSharing]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

All you need to do is:

- connect to the net wirelessly on one of the computers
- connect the 2 computers via a hardwire ethernet cable (I also think these are auto-sense now)
- on the PC with the wireless connection to the net, click on the network manager icon, click on edit connections, go to the wired tab, then click on the adapter/network shown there and then edit.  On the edit window click on IPv4 settings tab and change the method via the pull-down to shared with other computers.  Save and exit.  You may need to restart the PC's and connect the same one wirelessly and then the 2nd should be able to access the net as well.

If all you want to do is share the internet connection, pay no attention to the rest of the thread in the how-to - it is for more advanced user.

Dave ;)

---

### Post by sudodus on 2011-11-27
> **anewguy said:**
> You shouldn't need a router.  All you should need is internet connection sharing.  This would in your case entail 2 computers connected via a hardwire ethernet cable and 1 of those computers being connected wirelessly to the net.

If nobody has suggested it yet, or if you haven't read it, see the following link:

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

All you need to do is:

- connect to the net wirelessly on one of the computers
- connect the 2 computers via a hardwire ethernet cable (I also think these are auto-sense now)
- on the PC with the wireless connection to the net, click on the network manager icon, click on edit connections, go to the wired tab, then click on the adapter/network shown there and then edit.  On the edit window click on IPv4 settings tab and change the method via the pull-down to shared with other computers.  Save and exit.  You may need to restart the PC's and connect the same one wirelessly and then the 2nd should be able to access the net as well.

If all you want to do is share the internet connection, pay no attention to the rest of the thread in the how-to - it is for more advanced user.

Dave ;)
Great news :-) This help page is updated recently: Internet/ConnectionSharing  (edited 2011-10-22) so it is probably better than the previous how-to texts. Furthermore, there should be no need for this (extra) router.

If you succeed, 118118, I will recommend this method to a friend of mine.

---

### Post by 118118 on 2011-11-27
> **anewguy said:**
> All you need to do is:

- connect to the net wirelessly on one of the computers
- connect the 2 computers via a hardwire ethernet cable (I also think these are auto-sense now)
- on the PC with the wireless connection to the net, click on the network manager icon, click on edit connections, go to the wired tab, then click on the adapter/network shown there and then edit.  On the edit window click on IPv4 settings tab and change the method via the pull-down to shared with other computers.  Save and exit.  You may need to restart the PC's andconnect the same one wirelesslyand then the 2nd should be able to access the net as well.

If all you want to do is share the internet connection, pay no attention to the rest of the thread in the how-to - it is for more advanced user.

Dave ;)Hi
Thanks for the reply. But I have already tried this approach.

---

### Post by anewguy on 2011-11-27
Well, all I can do is just try to repeat a little and see if it's what you have done or not - I would try again:



(----======--==========)
((    internet        ))
(----======--==========)
|
|
|
|  wireless connection
| 
|
|
------------------------
|   PC #1              |
------------------------
|
|
|
|  hard wired ethernet connection    EDIT:  Change the IPv4 settings on this PC
|
|
|-----------------------
|   PC #2              |
------------------------


So, be sure PC #1 is connected wirelessly FIRST and can indeed access the internet.

Then connect the hard wire.

Then change the IPv4 settings.

It might be that a reboot is not needed and may wipe out the changes - I haven't tried this in ages!


Internet connection sharing is usually pretty easy, so I don't know what might be going on.  If you have added any packages, made changes to any files, etc., in your work on this so far I would suggest backing all of those out so you are starting with a clean slate at approaching this.

Dave ;)

---

### Post by 118118 on 2011-11-30
hi,

no this isn't working... i definitely have a wifi connection on the first pc and have connected the ethernet cable to both machines. i don't see how selecting internet sharing on the first pc can go wrong... though i am not using the original wired connection but added a new one - "wired connection one". might this be set up in the wrong way?

---

### Post by 118118 on 2011-11-30
might i be using the wrong cable? looking at the one i am using it seems to be crossed over, might that actually be a problem?

---

### Post by 118118 on 2011-11-30
hi,

i found another cable and tested it on the computer with the wireless connection and a third computer which worked fine - i was able to share my wireless network. 
however, as soon as i plug it into the computer i want to share internet with, the wired network connection established message flashes up then rapidly switches between to disconnected and back again.

and i can't access the internet.

any help?

---

### Post by 118118 on 2011-11-30
i can access the internet via this cable in windows but get the same annoying error message on the screen of the wireless computer.

---

### Post by anewguy on 2011-11-30
Without actually seeing things, the only thing I can guess at is that in the PC with 2 adapters - the original plus what you added - it may be looking at the 1 that is not being used.  Just guessing again without seeing it, if it's showing the connection you are trying to use as eth0 my guess would be that's the on board 1 you aren't using.  Try going into you BIOS to see if there is a way to disable the on board adapter.

Failing that, try removing the 1 you added and just use the on board 1 and see if that works.

Obviously, since it works with a different computer, it's just something with the 2nd.  I'd be willing to bet it's just confused as to which adapter it's using.

Open a terminal and do the following, and post the results back here:

ifconfig

iwconfig



Dave ;)

---

### Post by 118118 on 2011-11-30
```
luke@luke-AOD260:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:1e:7a:20  
          inet6 addr: fe80::8aae:1dff:fe1e:7a20/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2363 errors:0 dropped:0 overruns:0 carrier:7
          collisions:0 txqueuelen:1000 
          RX bytes:206726 (206.7 KB)  TX bytes:1491417 (1.4 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9216 (9.2 KB)  TX bytes:9216 (9.2 KB)

wlan0     Link encap:Ethernet  HWaddr c4:46:19:1d:9c:a1  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c646:19ff:fe1d:9ca1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2066446 (2.0 MB)  TX bytes:610727 (610.7 KB)

luke@luke-AOD260:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Apples"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 90:01:3B:1B:C0:C2   
          Bit Rate=28.9 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:133   Missed beacon:0
```

i only have one wired network connection as i deleted the standard one. are you talking past each other?

---

### Post by anewguy on 2011-12-01
Could you also post back the results of:

lspci

lshw -C network


Thanks!
Dave ;)

---

### Post by 118118 on 2011-12-01
hi,

```
^[[Aluke@luke-AOD260:~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
luke@luke-AOD260:~$ sudo lshw -C network
[sudo] password for luke: 
  *-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 88:ae:1d:1e:7a:20
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:57000000-5703ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: c4:46:19:1d:9c:a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.0.0-13-generic firmware=N/A ip=192.168.0.8 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:56000000-56003fff
luke@luke-AOD260:~$ 

```


thanks! so does anyone developing ubuntu get paid? just curious if i'm talking to any staff staff.... like charitable donations to "linux" or something..?

---

### Post by 118118 on 2011-12-01
so that's without the ethernet connected :)


:( !

---

### Post by anewguy on 2011-12-01
I guess I've been stupid here - the 1st machine obviously works as you can share the connection with a 3rd PC.

So, what I should have had you doing is posting this information from the 2nd PC - it may be that the ethernet controller in it isn't working yet.

So......

- Post back the specs of the 2nd PC and the OS it's running

- post back the outputs from the following: <<<<  EDIT:  NOTE:  THESE NEED TO BE ON THE 2nd PC  >>>>

lspci

lshw -C network

iwconfig

ifconfig


Sorry about that - I guess I had another brain "zeypher".

Dave ;)

---

### Post by 118118 on 2011-12-02
```
luke@luke-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
luke@luke-desktop:~$ sudo lshw -C network
[sudo] password for luke: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: f4:ec:38:d0:40:cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:fbff0000-fbffffff
luke@luke-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
luke@luke-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:22:c9:3e:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16416 (16.4 KB)  TX bytes:16416 (16.4 KB)

wlan0     Link encap:Ethernet  HWaddr f4:ec:38:d0:40:cf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

luke@luke-desktop:~$ 

```

---

### Post by 118118 on 2011-12-02
it's running 11.10

---

### Post by anewguy on 2011-12-02
Okay, that all helps.  It appears the ethernet adapter - the MCP61 ethernet - requires a driver be installed.  From what I have found on the net that driver is called the NFE driver.  What I don't know is if the module is delivered and not being loaded, or if you have to get the entire driver. 

So, try this, with the understanding it probably won't work, but is worth a try:

sudo modprobe nfe


*IF* that doesn't return an error, wait a couple of minutes and then see if the interface is working.  If so, we can walk you through the very simple process of making that load at each boot.

*IF* it fails, like I suspect it will, I'll have to do a little more research as the how-to for Ubuntu I found for this is still in dealing with BSD, not Ubuntu.  I believe the driver can also be downloaded from nVidia, so I'll check that as well.

Dave ;)

---

### Post by phreakkyphroggy on 2011-12-02
> **118118 said:**
> hi,

using an ethernet connection. 
i have set up network manager so that there is a wired connection that shares the internet on the machine with internet access but i do not know how to access it on the second machine - i do not yet have internet access on it.

thanks for any help.
what is the OS on the machine with Internet?
In windows you will need to change you "homegroup" setting or "network" settings.

I am right now doing the same with an iBook G4 with Meercat and a Cat 5 Ethernet connection to my Desktop with Ubuntu 11.10

It worked! went right to my homepage. That is Linux to Linux.

The "Yellow Cable" should work for you also.

---

### Post by 118118 on 2011-12-03
> **anewguy said:**
> Okay, that all helps.  It appears the ethernet adapter - the MCP61 ethernet - requires a driver be installed.  From what I have found on the net that driver is called the NFE driver.  What I don't know is if the module is delivered and not being loaded, or if you have to get the entire driver. 

So, try this, with the understanding it probably won't work, but is worth a try:

sudo modprobe nfe


*IF* that doesn't return an error, wait a couple of minutes and then see if the interface is working.  If so, we can walk you through the very simple process of making that load at each boot.

*IF* it fails, like I suspect it will, I'll have to do a little more research as the how-to for Ubuntu I found for this is still in dealing with BSD, not Ubuntu.  I believe the driver can also be downloaded from nVidia, so I'll check that as well.

Dave ;)module not found!

---

### Post by anewguy on 2011-12-03
I suspected that would be the case.

=============   EDIT   ==============

On my system (11.10) the driver is delivered but not loaded.

You may want to try:

sudo modprobe forcedeth

Then wait a couple of minutes and check in the network manager on the 2nd machine to see if it shows an ethernet connection.  If it does, and if it works, we can make the change permanent quite easily.

=========== END OF EDIT =============



nVidia also has a driver source called forcedeth on their site ([http://www.nvidia.com/object/linux_nforce_1.21.html]("http://www.nvidia.com/object/linux_nforce_1.21.html")).  You may want to download it, however it is C source, so I need to find out what has to be done to install it. I assume I create the object module and then modprobe it, but I'm not sure.

In the mean time, download that source and also be sure you have the build-essential package installed (it contains the compilers, etc., that will be needed for building the program).

Dave ;)

---

### Post by 118118 on 2011-12-05
it worked fine for a few moments and then i get the message disconnected then connection establish then diconnected etc in rapid succession. and seemingly no connection...

---

### Post by 118118 on 2011-12-05
no, i do still have a connection. but why the error message and is it running at full capacity given it.

when i go to connection information i see eth0 with forcedeth driver.

---

### Post by anewguy on 2011-12-05
Not sure why the error message or about the speed at this point.  I'll do some more checking and see if perhaps someone has developed a patch for the driver.

In the mean time, is PC 2 able to share the internet connection now?

EDIT:  BTW - I didn't specifically say so, but you did the modprobe of forcedeth on PC 2, correct?

Dave ;)

---

### Post by 118118 on 2011-12-05
yes it appears to be.

i think the problem is that i should configure a static ip address. but i am lost as to what numbers [gatewat, netmask and address] to use :(

---

### Post by anewguy on 2011-12-05
Well, I really don't know what those would - I suspect something from your PC 1 - but I have no idea at this time.

Perhaps someone else might be able to help you there - I'll keep looking for information in the mean time.

Dave ;)

---

### Post by 118118 on 2011-12-05
yes... modprobe on pc2.

---

### Post by anewguy on 2011-12-05
I do see some posts, most not recent, about the forcedeth driver and various MPCxx ethernet adapters disconnecting and reconnecting quickly in almost a loop.  I haven't seen anything yet for solving that, but I'll keep looking.

In the meantime, since the modprobe did load the driver and it does work to some degree, we need to make that permanent.  To do so, just do the following and reboot:


sudo gedit /etc/modules

go to the bottom of that file and add a new line that simply says:

forcedeth <press enter>

Then save the file and exit the editor.

Dave ;)

---

### Post by Bala_cbe on 2011-12-06
> **118118 said:**
> hi,

using an ethernet connection. 
i have set up network manager so that there is a wired connection that shares the internet on the machine with internet access but i do not know how to access it on the second machine - i do not yet have internet access on it.

thanks for any help.

1) IF DHCP is OFF in the Router:
Try connecting with Static IP address range, 192.168.1.x, Subnet Mask 255.255.255.0 and Gateway <Your Router IP Addr>. Also, in the DNS entries, <Your Router IP addr>. 

Then once the network is reached, it will ask for the "passphrase", give it as well. 

This is enough to get connected.

2) IF DHCP is ON in the Router:

Just select "Obtain Address automatically" and try connecting. Then once the network is reached, it will ask for the "passphrase", give it as well. 

If it doesn't work, please let me know your Router configuration and 2nd System configuration. 

Thanks and regards, 
Bala_cbe

---

### Post by 118118 on 2011-12-06
[http://askubuntu.com/questions/64494/wired-connection-shared-with-other-computers-connects-then-disconnects-in-11-10](http://askubuntu.com/questions/64494/wired-connection-shared-with-other-computers-connects-then-disconnects-in-11-10)

was the solution. thanks - working fine now! just need to see if i can sort it out wirelessly...

---

### Post by sudodus on 2011-12-06
> **118118 said:**
> [http://askubuntu.com/questions/64494/wired-connection-shared-with-other-computers-connects-then-disconnects-in-11-10](http://askubuntu.com/questions/64494/wired-connection-shared-with-other-computers-connects-then-disconnects-in-11-10)

was the solution. thanks - working fine now! just need to see if i can sort it out wirelessly...
Congratulations :-)

I'm glad also on behalf of my friend, who will now try to do the same thing.

---

### Post by anewguy on 2011-12-07
I'm glad you found and followed that link to get around the disconnects.  As for the rest - you're welcome, and just play it forward when you can.

Dave ;)

---

