---
title: "WLan Problem"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by pete-the-meat on 2008-06-19
I have an unusual problem with my wireless on Hardy Heron which is beyond me. I installed my wlan interface using ndiswrapper (a Belkin PCI card which installed and occassionally runs as it is meant to, once in a blue moon). The problem is as follows...

When I click on the networks icon in the top left my wireless network is listed correctly. When I click on the network it prompts me for the WEP key, which I enter correctly. It the deliberates over connecting for a while and prompts me again, and again, and again. I know the network works fine and that the key is correct as I use the same network and key to access the net on my windows machine, which works just fine.

Can anyone help me?

Thanks

(Also, I hope this is posted in the right place!)

I've posted my iwconfig output as well, perhaps this will help?

```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:46 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by issih on 2008-06-19
This probably won't help, but have you checked you are using the right kind of WEP? Try the password with all of the WEP types, i.e. passphrase, hex and asci.

Probably not that, but worth checking anyway.

---

### Post by pete-the-meat on 2008-06-19
Oh yes, definitely using the right type of WEP

---

### Post by issih on 2008-06-19
Ok then time to try a few things:

1) try uninstalling the windows driver in ndiswrapper then reinstalling it.

2) check that the hardware is functioning correctly with encryption turned off.(if not check on the ndiswrapper website to see which driver they recommend using for your hardware)

3) try associating via the command line:

```
sudo iwconfig wlan0 essid <yourssid>
sudo iwconfig wlan0 key <yourkey>
```

if your key is hex just replace <yourkey> with it, if you have an asci one, use:

```
s:<yourascikey>
```

Let us know what happens and good luck :)

---

### Post by pete-the-meat on 2008-06-19
So I uninstalled the driver from ndiswrapper and re-installed it to no avail. The hardware is not listed on the ndiswrapper site but when i first installed it I used -a to force the driver-hardware pairing thing but it worked just fine for a week or two before skipping out. Very occassionally, maybe once a week, it will work again, but only for half an hour or so.

Associating via the command line seemed to have no discernible effect whatsoever.

---

### Post by issih on 2008-06-19
Can you post the output of:

```
sudo lshw -C network
```

That should tell us exactly what hardware you are using, and we can hunt about for a solution :s

---

### Post by pete-the-meat on 2008-06-19
```
  *-network:0
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 05
       serial: 00:50:8d:70:83:69
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=32 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:1
       description: Wireless interface
       product: Belkin
       vendor: Belkin
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: wlan0
       version: 20
       serial: 00:17:3f:2f:09:2e
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8185 driverversion=1.52+Realtek,03/21/2008,5.1105.0 latency=32 link=no maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network:2
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 04
       serial: 00:50:8d:70:83:68
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

```

---

### Post by issih on 2008-06-19
Hmmn, helpful list that, almost no information to identify the device properly, "Belkin" isn't helpful really is it...Useless vendors :(.

I doubt it will help but could you try "lspci" instead? It might help if you happen to know the card/dongle name if its an add on device

It would also be very useful to know if the wireless functions correctly with wep turned off, just so we can establish that the hardware is functioning properly.

---

### Post by pete-the-meat on 2008-06-19
I took the encryption off of the hetwork and it functioned for a brief period of time before ceasing to work again. Now it just sits and attempts to connect with no result again. Here's my lspci output...

```
00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
02:01.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller (rev 05)
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:05.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
02:06.0 Ethernet controller: Belkin Unknown device 700f (rev 20)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE Ethernet Controller (rev 04)

```

The card is a Belkin FSD7000

---

### Post by issih on 2008-06-20
Oops, I wanted the output of:

```
lspci -n
```

my fault sorry....

This thread looks hopeful though 
[http://ubuntuforums.org/showthread.php?t=381878](http://ubuntuforums.org/showthread.php?t=381878)

---

### Post by pete-the-meat on 2008-06-20
```
00:00.0 0600: 8086:2584 (rev 0e)
00:01.0 0604: 8086:2585 (rev 0e)
00:1b.0 0403: 8086:2668 (rev 04)
00:1d.0 0c03: 8086:2658 (rev 04)
00:1d.1 0c03: 8086:2659 (rev 04)
00:1d.2 0c03: 8086:265a (rev 04)
00:1d.3 0c03: 8086:265b (rev 04)
00:1d.7 0c03: 8086:265c (rev 04)
00:1e.0 0604: 8086:244e (rev d4)
00:1f.0 0601: 8086:2640 (rev 04)
00:1f.1 0101: 8086:266f (rev 04)
00:1f.2 0101: 8086:2652 (rev 04)
00:1f.3 0c05: 8086:266a (rev 04)
01:00.0 0300: 10de:01d1 (rev a1)
02:01.0 0200: 8086:1076 (rev 05)
02:02.0 0c00: 104c:8024
02:05.0 0400: 14f1:8800 (rev 05)
02:05.2 0480: 14f1:8802 (rev 05)
02:06.0 0200: 1799:700f (rev 20)
02:08.0 0200: 8086:1065 (rev 04)

```

---

### Post by issih on 2008-06-20
This post appears to be dealing with your exact card, I'd try using the drivers they suggest and doing the special bit to associate with the card.

[http://ubuntuforums.org/showthread.php?p=3539832#post3539832](http://ubuntuforums.org/showthread.php?p=3539832#post3539832)

Hope that gets you going, let us know how it goes

---

### Post by pete-the-meat on 2008-06-20
Thanks very much for all your help so far. This is how I originally installed the drivers for the lan card, along with the following commands...

```
sudo depmod -a
duso modprobe ndiswrapper
sudo ndiswrapper -m
```

and appending ndiswrapper to /etc/modules

I have repeated the steps as instructed and still no difference.

---

### Post by issih on 2008-06-21
A couple of possibilities..

First suggestion is to blacklist a few possibly competing driver modules:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-549bfd5abadd89c84fb999343fa775cc876c07f3](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#head-549bfd5abadd89c84fb999343fa775cc876c07f3)

The other is to modify the linux native drivers and compile them:

[http://ubuntuforums.org/showthread.php?t=713058&page=2](http://ubuntuforums.org/showthread.php?t=713058&page=2)

---

### Post by chili555 on 2008-06-21
> **issih said:**
> Ok then time to try a few things:

1) try uninstalling the windows driver in ndiswrapper then reinstalling it.

2) check that the hardware is functioning correctly with encryption turned off.(if not check on the ndiswrapper website to see which driver they recommend using for your hardware)

3) try associating via the command line:

```
sudo iwconfig wlan0 essid <yourssid>
sudo iwconfig wlan0 key <yourkey>
```

if your key is hex just replace <yourkey> with it, if you have an asci one, use:

```
s:<yourascikey>
```

Let us know what happens and good luck :)I think your *iwconfig* and your *lshw* look healthy. What happened when you tried the manual way, therefore isolating Network Manager out of the equation? In my opinion, many of us here and on the Networking and Wireless forum, have healthy wireless cards but twitchy Network Manager issues. We then install different drivers on a perfectly working wireless card and, because that wasn't the problem at all, it doesn't work either.

If you can connect manually, then you do not have a driver issue.

---

### Post by pete-the-meat on 2008-06-21
OK...

Firstly those modules were already in my /etc/modprobe.d/blacklist file - but thanks :)

When I tried to connect manually absolutely nothing happened. I entered those lines, waited about a minute and tried to ping the router but received no response.

I followed that guice but it doesn't seem to have worked, in fact it has made matters worse. Now my card isn't installed at all, or at least it doesn't show up in the network manager.

When I run ./wlan0up I get the following output:

```
insmod: cat't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: cat't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: cat't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: cat't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: cat't read 'ieee80211-rtl.ko': No such file or directory
insmod: cat't read 'r8180.ko': No such file or directory
wlan0: ERROR while getting interface flags: No such device
```

When I run ./wlan0dhcp I get the following output:

```
cp: cannot create regular file `/etc/sysconfig/network-scripts/': No such file or directory
Pre-dhclient not exist!
There is already a pid file /ver/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client v3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
wlan0: error fetching interface information: Device not found
get ip:
```

my ifconfig output now looks like this:
```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:70:83:69  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0xb000 Memory:d3020000-d3040000 

eth1      Link encap:Ethernet  HWaddr 00:50:8d:70:83:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4100 (4.0 KB)  TX bytes:4100 (4.0 KB)


```

and my lshw output now looks like this:

```
           *-network:0
                description: Ethernet interface
                product: 82541GI Gigabit Ethernet Controller
                vendor: Intel Corporation
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 05
                serial: 00:50:8d:70:83:69
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=32 mingnt=255 module=e1000 multicast=yes
           *-network:1 UNCLAIMED
                description: Ethernet controller
                product: Belkin
                vendor: Belkin
                physical id: 6
                bus info: pci@0000:02:06.0
                version: 20
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=64 mingnt=32
           *-network:2
                description: Ethernet interface
                product: 82562ET/EZ/GT/GZ - PRO/100 VE Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:02:08.0
                logical name: eth1
                version: 04
                serial: 00:50:8d:70:83:68
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
```

---

### Post by pete-the-meat on 2008-06-21
In fact I just noted, upon retrying the steps, that the ./makedrv command output ended in the following lines:

```
make[2]: *** [/home/pete/drv/rt8185l/rt8185/rt8180_core.o] Error 1
make[1]: *** [_module_/home/pete/drv/tr8185l/rtl8185] Error 2
make[1]: Leaving directore `/usr/src/linux-headers-2.6.24-18-generic'
make: *** [modules] Error 2
```

So the makedrv ends in an error, which I guess is why it didn't work.

Now I'm really stumped (as if I wasn't before ;b)

---

### Post by issih on 2008-06-21
Looks like those drivers need patching to work with the 2.6.24 kernel series. As this page confirms:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196285](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196285)

Fortunately one of the people posting in that thread has done the necessary work :) His site looks very promising indeed:

[http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy](http://willdaniels.co.uk/articles/howto-guides/10-howto/12-r8180-hardy)

I'd give that a go if I were you, it sounds like it might even work this time...you'll still need to add the pciid from the other thread to patch the driver to know about your specific belkin card, i.e. add this to:

```

        {       /* Belkin F5D7000 */
	        .vendor = PCI_VENDOR_ID_BELKIN,
                .device = 0x700f,
                .subvendor = PCI_ANY_ID,
                .subdevice = PCI_ANY_ID,
                .driver_data = 2,
        },

```

into the rtl8185/r8180_core.c folder as before then do make clean and make in that folder.

Hope you follow that :)

---

### Post by pete-the-meat on 2008-06-21
This may seem like a silly question but can you confirm if I am meant to completely disable the ndiswrapper module before I perform this?

---

### Post by issih on 2008-06-21
Yeah, I would, otherwise you'll have two kernel modules both trying to load for the hardware. You can either uninstall it:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

Or you can probably just add it to the blacklist you looked at earlier if you want, I'd get rid of it completely though, it doesn't work for you after all :(

Oh yeah, I checked, and the drivers do at least compile to the .ko files from the patched sources, so thats a good start. I can't go any further as I don't actually have the relevant hardware :s

---

### Post by pete-the-meat on 2008-06-21
Well I blacklisted ndiswrapper and made sure it was also removed from /etc/modules so there was no chance of running. I then rebooted and followed the steps. WhenI ran the wlan0up script It returned the following:

```
wlan0: ERROR while getting interface flags: No such device
```

---

### Post by pete-the-meat on 2008-06-21
(and ./makedrv ran jsut fine without errors)

---

### Post by issih on 2008-06-21
Hmmn, well I'm about out of ideas, is the wireless interface visible if you do ifconfig or ifconfig -a now? or is it not being seen at all?

Did you modify the code to see your card as before?

If those don't work for you then I think you are screwed short of trying compiling the very latest ndiswrapper to see if you have any more luck that way

---

### Post by pete-the-meat on 2008-06-21
I forgot to modify the code to see my card, sorry about that - yes the driver works well and I can now connect to my network. Thank you so very much! :DDD

---

### Post by issih on 2008-06-21
Excellent, it would be helpful (if its possible) if you could change the thread title to something describing your hardware and mark it as solved, that way someone else might stumble on the answer with a little bit less pain than we had to go through.

Ah well, we got there in the end at least, enjoy your internets :)

---

### Post by pete-the-meat on 2008-06-22
May I re-open this thread? The card has reverted to it's old behaviour. For about two hours the card would connect to the network, although data transfer was painfully slow and everything was looking up. Now, however, the card doesn't show any signal for any networks, including the one I want to connect to. I know the card is in perfect working condition since I tested it in my windows machine and it worked flawlessly at full speed. (The machines are next to each other, so no (or discountably minimal) difference in signal strength.)

---

### Post by pete-the-meat on 2008-06-22
So it turns out that msot of the trouble was caused by an offending card in the next PCI slot. I also have a TV tuner installed and a friend of mine suggested that there may be an IRQ or addressing clash. I moved the TV tuner one slot down and right enought the wlan card now works perfectly. Thanks to you all for your help! :)

---

### Post by issih on 2008-06-23
I'm glad it was something simple like that causing the slowdown...I may have cried if those drivers hadn't worked after all that :D

---

