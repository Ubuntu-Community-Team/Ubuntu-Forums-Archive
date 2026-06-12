---
title: "Trendnet TEW-643PI issue: ndiswrapper install error free, no wlan0"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by zepolmot on 2011-10-25
Hi there,  I'm running 11.10 and the title pretty much says it all.  

I have a Trendnet TEW-643PI installed and I installed the windows 2000 driver (as per the wiki's suggestion) with no issues.  After modprobe ndiswrapper  I still do not have a wlan0.  sudo ifconfig wlan0 throws an error saying that no such device exists.  any suggestions would be greatly appreciated.

---

### Post by zepolmot on 2011-10-25
Wanted to give a little more info.  sudo lshw -C network returns

```

network UNCLAIMED
description: Network controller
product: realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 6
bus info: pci@0000:05:06.0
version: 00
width: 32 bits
clock: 33 MHz
capabilities: pm bus_master cap_list
configuration: latency=64 maxlatency=64 mingnt=32
resources: ioport:e800(size=256) memor: fbfff000-fbffffff

```

---

### Post by zepolmot on 2011-10-26
bump

---

### Post by anewguy on 2011-10-26
As far as I have ever known, ndiswrapper only works with Windows XP drivers, and they must match the OS architecture (32 or 64 bit).

Using other drivers can result in the device not working at all, or in the device being seen but not working.

do the following in a terminal window and post the results back here:

- lspci

- iwconfig

- ifconfig

- if it's a USB device:  lsusb

- sudo ndiswrapper -l (lower case "L" for "list")

Also, please post the links to whatever instructions you were following for ndiswrapper and that said to use the Windows 2000 driver.

This will give us a better view of what is going on.

Dave ;)

---

### Post by anewguy on 2011-10-26
I was hoping you'd be back by now, but I guess not.  If you do come back to this thread, do the following:

- open a terminal window

sudo ndiswrapper -l (lower case "L" for "list")

for each device returned:

sudo ndiswrapper -r xxxxxxx  (where xxxxxx is the device name)

until no more devices show.

-close the terminal window

Reverse any blacklisting, etc., you may have tried with ndiswrapper.

- put the Windows XP driver files (the .inf and .sys files) for your adapter on your desktop

- either via exploring the LiveCD /pool/main/n or synaptic package manager, be sure the following 3 packages are installed:

ndiswrapper  (on the CD in /pool/main/n/ndiswrapper)
ndiswrapper utilities (on the CD in /pool/main/n/ndiswrapper)
ndisgtk (on the CD in /pool/main/n/ndisgtk)

Now go to system/administration/windows wireless drivers - this starts up ndisgtk.  Select add/new, point it to the .inf driver file on your desktop and ok it.

Check network manager to be sure Enable Wireless is checked.

Check to see if network manager is seeing any networks now.


Dave ;)

EDIT:  Forgot to mention that everything I have found on the net indicates your adapter may not work in Linux if you are using WEP on the router.  WPA is supported.

---

### Post by zepolmot on 2011-10-27
Hey Dave, thanks for the reply.  I'm not at the computer with the issue at the moment, but I wanted to reply with the site that referenced using the win2000 driver: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Trendnet_TEW-643PI](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Trendnet_TEW-643PI)

Edit: 
I'm not sure the WEP/WPA issue will really effect whats going on, as the computer cannot even recognize the presence of the card.  Though that is a helpful piece of intel once this step gets sorted.

---

### Post by anewguy on 2011-10-27
If you go to Trendnet's website you will find a single zipped file containing the drivers for 2000, XP, Vista and 7, both 64-bit and 32-bit.  If you download this file, select the option to save it.  When the download completes, open it with the archive manager, go to the XP folder and then to the 32-bit folder (assuming you installed "normal" Ubuntu) and extract the 3 files there to your desktop as the driver files mentioned in my previous post.  Then just follow the instructions in my previous post.  Remember to back out anything you may have done prior to this as per the instructions in that post.

Let me know how that turns out.  If errors, please provide the full text (a snapshot of the desktop would work nicely).

Dave ;)

---

### Post by zepolmot on 2011-10-27
Same basic results.  Some diagnostic outputs:

```
  [FONT=&quot]zepolmot@ZepDesk:~$ lspci
[/FONT][FONT=&quot]00:00.0 Host bridge: ATI Technologies Inc RD780 Northbridge only dual slot PCI-e_GFX and HT1 K8 part
00:03.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (external gfx0 port B)
00:06.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port C)
00:07.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: ATI Technologies Inc RD790 PCI to PCI bridge (PCI express gpp port E)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood PRO [Radeon HD 5500 Series]
01:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6315 Series Firewire Controller
04:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6121 SATA II Controller (rev b2)
05:06.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190
zepolmot@ZepDesk:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

zepolmot@ZepDesk:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:d7:5b:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47520 (47.5 KB)  TX bytes:47520 (47.5 KB)

zepolmot@ZepDesk:~$ sudo ndiswrapper -l
zepolmot@ZepDesk:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       [/FONT][FONT=&quot]version: 03
       serial: e0:cb:4e:d7:5b:78
       [/FONT][FONT=&quot]size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:b800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:fbcf0000-fbcfffff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:fbfff000-fbffffff
zepolmot@ZepDesk:~$ 

 [/FONT]
  
```

And then trying again with ndiswrapper and XP drivers:
```
zepolmot@ZepDesk:~$ 
zepolmot@ZepDesk:~$ cd Drivers/Wireless/XP/x64/
zepolmot@ZepDesk:~/Drivers/Wireless/XP/x64$ sudo ndiswrapper -i net819xp.inf
installing net819xp ...
zepolmot@ZepDesk:~/Drivers/Wireless/XP/x64$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modules.conf ...
zepolmot@ZepDesk:~/Drivers/Wireless/XP/x64$ sudo modprobe ndiswrapper
zepolmot@ZepDesk:~/Drivers/Wireless/XP/x64$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

zepolmot@ZepDesk:~/Drivers/Wireless/XP/x64$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:d7:5b:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:47520 (47.5 KB)  TX bytes:47520 (47.5 KB)

zepolmot@ZepDesk:~/Drivers/Wireless/XP/x64$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: e0:cb:4e:d7:5b:78
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:b800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:fbcf0000-fbcfffff
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=64 mingnt=32
       resources: ioport:e800(size=256) memory:fbfff000-fbffffff
zepolmot@ZepDesk:~/Drivers/Wireless/XP/x64$ sudo ndiswrapper -l
net819xp : driver installed
    device (10EC:8190) present


```

---

### Post by anewguy on 2011-10-27
(a) Any reason you're not using ndisgtk?  It takes care of all that typing for ndiswrapper.  Please, back everything out and try ndisgtk.

(b) Did you reboot?

EDITS:

======
- try lspci -v, find the wireless controller again, then post back the output of lspci -v -d xxxx:yyyy are the manufacturer id and device id in the lspci -v output
======

Found this in an answer from wildmanne39. You already have ndiswrapper and the utilities so you can skip that install step in Step 1.  Also, pay no attention for now to the version of ubuntu the post is for, and you'll want the 64-bit driver if available (if it's not, you kind of out of luck for this try):

jlucio
First Cup of Ubuntu
 
Join Date: Jan 2010
Beans: 1
	
Re: Realtek RTL8190 PCI card and ndiswrapper help.
I have used this tutorial here:
[https://help.ubuntu.com/community/Wi...eisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

But, of course, I've changed the commands that depended on the driver. The one I used was exactly the one that came with the product, more precisely the WinXP x86 driver named "rtl8190p.sys" and "net8190.inf".

The commands, used on Ubuntu 9.10 were:

Step 1:- Install NDISWrapper and Blacklist Native Driver
echo -e 'blacklist rtl8190\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/rtl8190; cd ~/rtl8190

Step 2: Copy "rtl8190p.sys" and "net8190.inf" to ~/rtl8190

Step 3: Configure NDISWrapper (and WPA Supplicant)
sudo ndiswrapper -i net8190.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Last edited by jlucio; October 8th, 2010 at 05:28 PM..

I would try this and see what happens.
======

---

