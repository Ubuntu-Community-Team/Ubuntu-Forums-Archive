---
title: "Acer Aspire One - Wireless Issue"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by chairmanofthebored on 2008-08-28
Hi

I am a real beginner with Ubuntu so please bear with me here.

I have an Acer Aspire One UMPC that I have just loaded with Ubuntu.

I followed the setup guide here [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) and the wireless connection seemed to work fine initially.

After a few restarts and a little tweaking it seems to have stopped detecting any wireless networks however.

I can confirm that there are at least 4 networks available where i'm located with another machine but network manager shows none available.

Not sure what information you require so just ask and I shall provide.

Many Thanks

---

### Post by nothingspecial on 2008-08-28
if you open a terminal (accessories > terminal) and type 

```
lspci -v
```

A load of gobbledygook will appear, copy and paste it into a reply.

Also what tweaking did you do?

---

### Post by chairmanofthebored on 2008-08-28
OK, gobbledygook is as follows:

As regards the "Tweaking", basically I followed the steps in the guide I linked to in my initial post.

Thanks



00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 38480000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 60c0 [size=8]
    Memory at 20000000 (32-bit, prefetchable) [size=256M]
    Memory at 38500000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, fast devsel, latency 0
    Memory at 38400000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 38540000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 37300000-383fffff
    Prefetchable memory behind bridge: 0000000030000000-0000000030ffffff
    Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: 36300000-372fffff
    Prefetchable memory behind bridge: 0000000031000000-00000000320fffff
    Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 35200000-362fffff
    Prefetchable memory behind bridge: 0000000032100000-00000000330fffff
    Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 34100000-351fffff
    Prefetchable memory behind bridge: 0000000033100000-00000000340fffff
    Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 6080 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 6060 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6040 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 6020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 38544400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 60a0 [size=16]
    Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: medium devsel, IRQ 11
    I/O ports at 6000 [size=32]

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 219
    I/O ports at 3000 [size=256]
    Memory at 31010000 (64-bit, prefetchable) [size=4K]
    Memory at 31000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 31020000 [disabled] [size=128K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Unknown device e008
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 35200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

---

### Post by DemonBob on 2008-08-28
Do you run an update? 

If you did it's possible that you receieved a kernel update...which means you'll have to recompile the wireless drivers. Anytime thier is a kernel update this will need to be done. 

```

wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
tar -xvf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
cd madwifi-hal-0.10.5.6-r3835-20080801
sudo apt-get install build-essential linux-headers-$(uname -r)
sudo make
sudo make install

```

---

### Post by nothingspecial on 2008-08-28
> **chairmanofthebored said:**
> 

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: medium devsel, IRQ 11
    I/O ports at 6000 [size=32]

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Unknown device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 219
    I/O ports at 3000 [size=256]
    Memory at 31010000 (64-bit, prefetchable) [size=4K]
    Memory at 31000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 31020000 [disabled] [size=128K]
    Capabilities: <access denied>

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Unknown device e008
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 35200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>

Ok I`ve got to go for a bit now but ,these are the important bits. Try googling

```
Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter Ubuntu
```

and
```
RTL8101E Ubuntu
```

This is fixable,  I`ll check back later to see how you`re doing

---

### Post by nothingspecial on 2008-08-28
Demon bob just showed you how!

---

### Post by nothingspecial on 2008-08-28
> **nothingspecial said:**
> Demon bob just showed you how!

Do demon bobs suggestion one line at a time though;)

---

### Post by chairmanofthebored on 2008-08-28
OK, tried recompiling as suggested but still not detecting any networks.

Don't know if it helps but here is what I get when I do ```
ifconfig
```

ath0      Link encap:Ethernet  HWaddr 00:22:69:1b:f2:bc  
          inet6 addr: fe80::222:69ff:fe1b:f2bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:1e:68:b8:3c:09  
          inet addr:172.31.156.28  Bcast:172.31.156.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:feb8:3c09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:3725912219 overruns:0 frame:0
          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11342 (11.0 KB)  TX bytes:5055 (4.9 KB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56100 (54.7 KB)  TX bytes:56100 (54.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-22-69-1B-F2-BC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:6946 (6.7 KB)
          Interrupt:18 

and ```
iwlist ath0 scan
```

ath0      No scan results

Anything else you want just let me know.

Thanks

---

### Post by chairmanofthebored on 2008-08-28
Well I've sorted it.

had to enable the drivers in System - Administration - Hardware Drivers

Should have known it'd be something simple.

Thanks all for your help

---

### Post by seelumirun on 2008-10-03
Hi guys,

I'm having a similar problem in that I can't detect any networks. I've tried the two solutions in this thread (updating and re-enabling the drivers) and I'm still unable to detect any networks.

Any ideas?

Thanks

---

### Post by s34nn4 on 2008-10-09
Same here. There is thread were you need to configure aes-ccmp on this machine.

what are the outputs when you type?

```

iwconfig
```

---

### Post by snakeman21 on 2009-02-01
Okay, I'm going to try to help out here.  You don't actually have to download the files for the driver every time you get a kernel update.  I'm going to link to a webpage where you can download an archive.  Put the archive on your desktop and extract it to your home folder.  You will get a folder called "madwifi."  It has all the files you need to get your AA1 wireless working.  I know, because I HAVE and Aspire One.  I'm using it right now, with my dear Intrepid.  

Anyways, cd into that madwifi folder and into madwifi-hal-0.10.5.6 and type

```
make
```

It will think for a minute and display a bunch of info that will mean nothing to you.  Once it finishes, type

```
sudo make install
```

once that finished, type

```
sudo gedit /etc/modules/
```

and add "ath_pci" (without the quotes) to the bottom of the document, save, and exit.  You only have to do that last step the first time you do this.  Thereafter, simply open a terminal and run the first two commands every time you get a kernel update.  Then restart and your wireless should work.  

The reason I offer this folder is to make it a little simpler than downloading from the repositories.  It's a good idea to save this folder to a usb stick or something for future use.  Download the archive here:  [http://www.mediafire.com/?n2waz5qewzr]("http://www.mediafire.com/?n2waz5qewzr")

Hope this is helpful!

---

