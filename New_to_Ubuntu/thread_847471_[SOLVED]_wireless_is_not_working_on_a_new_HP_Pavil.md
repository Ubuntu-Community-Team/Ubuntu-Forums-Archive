---
title: "[SOLVED] wireless is not working on a new HP Pavilion laptop"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by Friccy on 2008-07-02
Hi!
I just bought a new HP Pavilion laptop and installed Ubuntu Hardy on it.
The wireless card was detected as Broadcom, which is OK, but still not working.
Can anybody help me configure it or make it work?
Thanks!

---

### Post by pytheas22 on 2008-07-02
First, go to System>Administration>Hardware Drivers.  You should see an entry for enabling your wireless card.  Click to enable it, reboot and see if it makes a difference.

If not, please open a terminal (Applications>Accessories), run these commands and post the output here:
```

lshw -C Network
lspci
```

---

### Post by Friccy on 2008-07-03
Hi again!

I am trying for 2 days to paste the output and send it to you, but can't do it.
The network seems to be very slow.
Is there any other way I can send it to you.
I am desparate to make the wireless working, neither the wired connection is not working.
It's a brand new laptop and can't use it properly!

---

### Post by pytheas22 on 2008-07-03
Can you copy the output to a USB drive and then send it from another computer on which the Internet connection works?

If not, let me know and I will send you my email address, if you think it would be easier to send the information there.

---

### Post by Friccy on 2008-07-04
Here you have the output for the 2 commands:
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP65 Ethernet
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth0
       version: a3
       serial: 00:1b:24:d3:aa:4c
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

Thanks for your help!

---

### Post by Friccy on 2008-07-04
> **pytheas22 said:**
> First, go to System>Administration>Hardware Drivers.  You should see an entry for enabling your wireless card.  Click to enable it, reboot and see if it makes a difference.

If not, please open a terminal (Applications>Accessories), run these commands and post the output here:
```

lshw -C Network
lspci
```

I could send justt for the first command. Here is for the other one:
friccy@laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP65 SMU (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 045b (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by mysterymann78 on 2008-07-04
After you installed Ubuntu did you download software upgrades? I had to do this to get pavilion 6552 wireless to work.

---

### Post by Friccy on 2008-07-04
> **mysterymann78 said:**
> After you installed Ubuntu did you download software upgrades? I had to do this to get pavilion 6552 wireless to work.

No, because there is no connection to the internet.
I have a router and now neither the wired internet is working.
After I type 
sudo pppoeconf
it says that he couldn't find the eth0 to connect to.

---

### Post by pytheas22 on 2008-07-04
Yes, as the poster above says, you probably just need to install the firmware package to get it to work.  Unfortunately that's hard since you don't have any Internet connection on Ubuntu right now.  But you can still get the wireless to work like this:

1. download the firmware cutter from [http://packages.ubuntu.com/hardy/b43-fwcutter](http://packages.ubuntu.com/hardy/b43-fwcutter) (scroll to the bottom of the page and click the appropriate link for your system, i386 or amd64).  Then transfer that file to your Ubuntu computer's desktop.

2. also transfer this file to your desktop on Ubuntu: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

3. on Ubuntu, run these commands:
```

cd ~/Desktop
sudo dpkg --install b43*
sudo b43-fwcutter wl* /lib/firmware
```

then reboot and hopefully your wireless will work.  If not, let me know.  I'm not positive that the method above will work for you, because I don't have the same kind of wireless card.  If it doesn't, we can use ndiswrapper.

---

### Post by mysterymann78 on 2008-07-04
> **pytheas22 said:**
> Yes, as the poster above says, you probably just need to install the firmware package to get it to work.  Unfortunately that's hard since you don't have any Internet connection on Ubuntu right now.  But you can still get the wireless to work like this:

1. download the firmware cutter from [http://packages.ubuntu.com/hardy/b43-fwcutter](http://packages.ubuntu.com/hardy/b43-fwcutter) (scroll to the bottom of the page and click the appropriate link for your system, i386 or amd64).  Then transfer that file to your Ubuntu computer's desktop.

2. also transfer this file to your desktop on Ubuntu: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)

3. on Ubuntu, run these commands:
```

cd ~/Desktop
sudo dpkg --install b43*
sudo b43-fwcutter wl*
```

then reboot and hopefully your wireless will work.  If not, let me know.  I'm not positive that the method above will work for you, because I don't have the same kind of wireless card.  If it doesn't, we can use ndiswrapper.

I agree, the firmware cutter should work as this is one of the upgrades which downloads in system update. I am surprised that wired network not working. You should check in the BIOS that internal network card is switched on at boot because this is sometimes diabled to save power.

---

### Post by Friccy on 2008-07-04
It's not working!
I have the following:
Selecting previously deselected package b43-fwcutter.
(Reading database ... 95678 files and directories currently installed.)
Unpacking b43-fwcutter (from b43-fwcutter_011-1_i386.deb) ...
Setting up b43-fwcutter (1:011-1) ...
--23:04:01--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter

What should I try next?

---

### Post by pytheas22 on 2008-07-05
Sorry it's not working.  The problem is that it needs to install firmware to make your card work, which it wants to download from the Internet.  Obviously it can't download it because you're offline (instead you have to install it manually, which is why you copied over that wl_apsta file).  I thought it would be smart enough to realize this, but I guess not.  Try this though:

1. download this file and copy it to your desktop on Ubuntu: [http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2) (I ask you to do this because this is another version of the firmware file and may work better, although this doesn't have to do with the error you got above).

2. On your Ubuntu desktop, double-click on the b43-fwcutter package's icon.  An installer will open.  Install the program that way.  Hopefully it will run alright even though there's no Internet connection.  If you get an error again, please let me know.

3. now run:

```
cd ~/Desktop
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```

and reboot.  If the wireless still doesn't, please try this:

```
cd ~/Desktop
rm -rf /lib/firmware/b43*
sudo b43-fwcutter wl* /lib/firmware
```

Please let me know how it goes.  If you execute the steps above successfully but you are still unable to connect to the wireless, please paste the output of these commands:

```
iwconfig
lshw -C Network
dmesg
```

(that last one will be long, but it's good to see it)

---

### Post by Friccy on 2008-07-05
Finally I have managed to make the wired connection and download the updates.
Now I have the wireless icon next to the battery icon, saying that has full signal. But still not working!
If I move the cursor on the wireless icon I have the following:
"Wireless network connection to 'Home network' (0%)"
What else I have to configure? The Home network is a not secured network, so it has to work. It worked on the old laptop and XP.

---

### Post by pytheas22 on 2008-07-05
> If I move the cursor on the wireless icon I have the following:
"Wireless network connection to 'Home network' (0%)"

Probably a problem with the firmware or driver for your wireless card.  I think the b43 driver has problems like this with some cards; you may need to switch to bcm43xx, an older but more stable driver for your device.  Please connect to your wireless network, then immediately post the output of:
```

dmesg
```

so that we can troubleshoot it.

Also try this:

```
sudo ifconfig eth1 down
sudo rmmod b43
sudo modprobe b43
sudo ifconfig eth1 up
```

then wait a few seconds and try to connect again.  Does it work now?

---

### Post by Friccy on 2008-07-05
> **pytheas22 said:**
> Probably a problem with the firmware or driver for your wireless card.  I think the b43 driver has problems like this with some cards; you may need to switch to bcm43xx, an older but more stable driver for your device.  Please connect to your wireless network, then immediately post the output of:
```

dmesg
```

so that we can troubleshoot it.

Also try this:

```
sudo ifconfig eth1 down
sudo rmmod b43
sudo modprobe b43
sudo ifconfig eth1 up
```

then wait a few seconds and try to connect again.  Does it work now?

Hi!
Thanks for your help!
I am attaching the file with the result of the dmesg command.
Hope that you will see it!

---

### Post by pytheas22 on 2008-07-05
I don't see the file; did you attach it already?

---

### Post by Friccy on 2008-07-05
[   69.993698] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.077145] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.077841] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.161287] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.161999] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.245427] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.246170] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.329556] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.330270] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.413637] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.414787] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.499449] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.500176] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.585269] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.585992] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.669407] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.670134] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.755219] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.755936] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.839356] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.840356] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   70.925176] wlan0: associate with AP 00:14:d1:36:6d:14
[   70.926298] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.010991] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.011714] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.096812] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.098265] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.182635] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.183375] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.268455] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.269188] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.352584] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.353310] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.438396] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.439115] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.524220] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.524953] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.610035] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.610761] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.695857] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.696576] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.781673] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.782394] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.867493] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.868216] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   71.953309] wlan0: associate with AP 00:14:d1:36:6d:14
[   71.954028] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.039131] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.039861] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.124948] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.125677] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.209078] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.209803] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.293220] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.293969] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.379034] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.379764] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.463171] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.463886] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.547305] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.548030] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.631445] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.632183] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.717264] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.717997] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.803079] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.803814] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.888900] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.889834] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   72.974715] wlan0: associate with AP 00:14:d1:36:6d:14
[   72.975434] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.060528] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.061245] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.144668] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.145393] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.228807] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.229527] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.314625] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.315347] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.400443] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.401171] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.484608] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.485327] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.568709] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.569409] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.652846] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.653572] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.736981] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.737710] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.821116] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.821830] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.905253] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.905966] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   73.989388] wlan0: associate with AP 00:14:d1:36:6d:14
[   73.990510] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.073517] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.074244] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.157655] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.158381] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.241790] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.242816] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.325926] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.326652] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.410062] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.410784] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.494199] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.494924] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.578335] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.579058] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.664159] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.664896] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.748289] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.749020] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.834179] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.835024] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   74.918312] wlan0: associate with AP 00:14:d1:36:6d:14
[   74.918975] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.002450] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.003107] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.086585] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.087218] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.170721] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.171376] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.254857] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.255509] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.338993] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.339642] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.423131] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.423793] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.507264] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.507928] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.591396] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.592048] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.675535] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.676185] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.759674] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.760342] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.843810] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.844481] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   75.927943] wlan0: associate with AP 00:14:d1:36:6d:14
[   75.929068] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.012078] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.012768] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.096214] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.096879] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.180354] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.181812] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.264482] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.265157] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.348617] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.349274] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.432753] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.433465] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.516890] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.517574] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.601026] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.601680] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.685165] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.685829] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.769299] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.769952] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.853435] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.854184] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   76.937572] wlan0: associate with AP 00:14:d1:36:6d:14
[   76.938230] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.021706] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.022356] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.105843] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.106566] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.189979] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.190635] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.274112] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.274763] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.358252] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.358924] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.442317] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.443057] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.528128] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.528856] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.613949] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.614665] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.698082] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.698815] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.782235] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.782965] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.868041] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.868766] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   77.953854] wlan0: associate with AP 00:14:d1:36:6d:14
[   77.954579] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.039671] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.040498] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.125487] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.126577] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.211308] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.212379] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.297137] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.298480] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.382978] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.383702] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.468764] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.469508] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.554585] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.555313] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.640408] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.641124] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.726223] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.726964] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.812047] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.812790] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.896179] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.896905] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   78.981991] wlan0: associate with AP 00:14:d1:36:6d:14
[   78.982917] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.067814] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.069367] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.153630] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.154655] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.239451] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.241442] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.325268] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.326007] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.409401] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.410122] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.495224] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.495962] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.581040] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.581780] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.665178] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.668552] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.751047] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.751786] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.835186] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.835924] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   79.919327] wlan0: associate with AP 00:14:d1:36:6d:14
[   79.920070] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.003408] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.004147] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.087594] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.088443] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.171684] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.172415] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.257540] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.258352] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.341675] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.342415] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.425822] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.426565] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.509953] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.510611] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.594027] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.594774] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.678166] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.678899] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.764049] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.764774] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.848171] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.848828] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   80.932308] wlan0: associate with AP 00:14:d1:36:6d:14
[   80.932989] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.016443] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.017098] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.100519] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.101244] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.184662] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.185385] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.270470] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.271509] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.356293] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.357369] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.442111] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.443333] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.527922] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.528631] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.612064] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.612814] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.697881] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.698607] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.783703] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.784444] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.869523] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.870252] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   81.953658] wlan0: associate with AP 00:14:d1:36:6d:14
[   81.955092] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.037795] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.038524] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.121933] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.122665] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.206065] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.206779] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.290204] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.290943] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.374341] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.375074] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.458468] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.459198] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.542606] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.543330] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.626742] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.627549] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.712560] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.713281] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.796735] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.797470] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.880881] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.881586] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   82.965011] wlan0: associate with AP 00:14:d1:36:6d:14
[   82.965760] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.049149] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.049899] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.133292] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.134020] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.217435] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.218090] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.301573] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.302306] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.385711] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.386428] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.469854] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.470506] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.553906] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.554763] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.639724] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.640808] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.725549] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.726612] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.811379] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.812109] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.897208] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.897946] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   83.991476] wlan0: associate with AP 00:14:d1:36:6d:14
[   83.993143] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   84.195294] wlan0: associate with AP 00:14:d1:36:6d:14
[   84.196980] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   84.399077] wlan0: associate with AP 00:14:d1:36:6d:14
[   84.400749] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   84.602847] wlan0: associate with AP 00:14:d1:36:6d:14
[   84.604559] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   84.695670] wlan0: associate with AP 00:14:d1:36:6d:14
[   84.696393] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   84.779809] wlan0: associate with AP 00:14:d1:36:6d:14
[   84.780560] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   84.865625] wlan0: associate with AP 00:14:d1:36:6d:14
[   84.866675] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   84.951445] wlan0: associate with AP 00:14:d1:36:6d:14
[   84.952818] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.037262] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.038458] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.123081] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.125285] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.208902] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.210387] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.294715] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.295451] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.378853] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.379582] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.464671] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.465418] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.548808] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.549543] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.634624] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.635340] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.720438] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.721150] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.806258] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.806985] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.890402] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.891144] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   85.974537] wlan0: associate with AP 00:14:d1:36:6d:14
[   85.975268] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.060355] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.061089] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.144492] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.145223] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.230312] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.231356] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.316130] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.316867] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.400257] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.400977] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.486070] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.486788] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.571891] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.573027] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.657709] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.658439] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.743532] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.744246] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.829343] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.830071] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.913480] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.914210] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   86.997634] wlan0: associate with AP 00:14:d1:36:6d:14
[   86.998362] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.083436] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.084149] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.167574] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.168299] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.251709] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.252441] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.335844] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.336563] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.421662] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.422384] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.507485] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.508236] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.593298] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.594032] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.679111] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.679834] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.763249] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.763970] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.847384] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.848102] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   87.931525] wlan0: associate with AP 00:14:d1:36:6d:14
[   87.932254] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.015662] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.016829] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.101475] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.102608] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.187299] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.188616] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.271440] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.272173] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.355578] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.356358] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.441393] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.442128] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.527209] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.527939] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.611343] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.612080] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.695474] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.696200] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.779607] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.780334] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.865426] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.866158] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   88.949577] wlan0: associate with AP 00:14:d1:36:6d:14
[   88.950306] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.035375] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.036100] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.119517] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.120233] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.205335] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.206056] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.289467] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.290201] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.375288] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.376010] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.461105] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.461833] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.546948] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.547683] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.631078] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.631815] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.715221] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.715952] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.799360] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.800071] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.883494] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.884183] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   89.967632] wlan0: associate with AP 00:14:d1:36:6d:14
[   89.968329] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.051768] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.052474] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.135904] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.136597] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.220036] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.220750] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.304167] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.304839] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.388304] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.389012] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.472437] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.473126] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.556578] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.557265] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.640716] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.641425] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.724846] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.725538] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.808985] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.809690] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.893120] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.893948] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   90.977251] wlan0: associate with AP 00:14:d1:36:6d:14
[   90.977941] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   91.061386] wlan0: associate with AP 00:14:d1:36:6d:14
[   91.062095] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   91.145521] wlan0: associate with AP 00:14:d1:36:6d:14
[   91.146210] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   91.229661] wlan0: associate with AP 00:14:d1:36:6d:14
[   91.230365] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   91.313798] wlan0: associate with AP 00:14:d1:36:6d:14
[   91.314504] wlan0: RX disassociation from 00:14:d1:36:6d:14 (reason=1)
[   91.397931] wlan0: associate with AP 00:14:d1:36:6d:14
[   91.482066] wlan0: associate with AP 00:14:d1:36:6d:14
[   91.566202] wlan0: associate with AP 00:14:d1:36:6d:14
[   91.650331] wlan0: association with AP 00:14:d1:36:6d:14 timed out

---

### Post by pytheas22 on 2008-07-06
Thanks for all that information.  It's obvious that there's some problem with your wireless driver, probably the firmware, that's preventing it from staying connected to the router (hence all the messages about "RX disassociation").  This could either be because b43, the driver that you're using, doesn't like your card, or because of a weird bug in the particular build of the driver that you happen to be using.

Either way, it would be hard to troubleshoot this because you can only do so much when there's a firmware problem.  I think the best thing to do at this point is to try ndiswrapper, which will let you drive your card using the Windows driver.  Please try this (make sure you are connected to the Internet via the wire):
```

sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper* ndisgtk cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
ndiswrapper -i bcmwl5.inf
ndiswrapper -m
```

This should ndiswrapper installed with the appropriate Windows driver for you card (based on this [guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver")).  If all of the commands above run successfully, then you should be able to do:
```

sudo rmmod b43
sudo rmmod ssb
sudo rmmod b43legacy
sudo depmod -a
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

(or just reboot), and then you can connect.  Please let me know.

Also, my apologies for making you go through so much already and having it end up not working.  If I'd known that the b43 driver was going to be buggy for you, I obviously wouldn't have made you do all that.  But ndiswrapper should definitely work for you, according to that guide.

---

### Post by Friccy on 2008-07-06
Thanks!
I will try them early next morning.
I will let you know about the result.
You are extremly kind and THANK YOU for your time!
Best regards!

---

### Post by Friccy on 2008-07-07
Hello!
I have tried your last suggestion, but it didn't work.
Now I have downloaded again and made clean reinstall of Hardy and an interesting thing happened.
The wireless card was found instantly and the driver also. It has been installed at the Hardware Drivers. It is enabled and in use.
Still not connecting to the "Home network".
At the Ubuntu support I have found out that this Broadcom BCM4312 network controller is not supported.
What is going on here? 
Why is still unable to connect if it has found and installed the driver?

---

### Post by oldman129 on 2008-07-07
try installing open suse 11 It worked right from the get go no hard work at all  I like ubuntu have on 5 computer just dont like the hard work to fet things don

---

### Post by pytheas22 on 2008-07-07
> Why is still unable to connect if it has found and installed the driver? 

Even though the b43 driver (the Linux driver for your wireless card) is able to detect the device, it still doesn't work well.  This is a problem with a lot of Broadcom wireless cards and Linux.  The Broadcom drivers are still being developed and don't work well yet with all cards.  I think that Ubuntu should have waited for b43 to become more mature before pushing it out to users, but unfortunately it didn't.  This leads to a lot of confusion for Ubuntu users whose cards appear to work with b43 but in reality don't.  Unfortunately, unless you want to do really advanced things (recompile your kernel from scratch), there's not much you can do to make b43 work besides wait for the next Ubuntu release, which will include an updated version of b43.

The alternative to b43 is to install ndiswrapper in order to use Windows wireless drivers.  The directions for this again are:
```

sudo -s
echo 'blacklist b43' >> /etc/modprobe.d/blacklist
echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper* ndisgtk cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp34001-34500/sp34152.exe
cabextract sp34152.exe
ndiswrapper -i bcmwl5.inf
ndiswrapper -m
```

I'm not sure why this didn't work the first time, but it should, provided you are using a 32-bit kernel (if you are on 64-bit, that makes a difference; let me know).  If you run the code above again and it still doesn't work after a reboot of your computer, please post this information:
```

ndiswrapper -l
iwconfig
lshw -C Network
cat /etc/modprobe.d/blacklist
```
> 
try installing open suse 11 It worked right from the get go no hard work at all I like ubuntu have on 5 computer just dont like the hard work to fet things don

I haven't tried suse in a long time but there's no reason to believe that your wireless card is going to work better there than in Ubuntu.  b43 is included in the Linux kernel and therefore is the same in all Linux distributions.  You could try suse, but I don't think it would help.

---

### Post by Friccy on 2008-07-13
Hi again!
Sorry for being so late!
I want to thank you very much for your help!
I have reinstalled the router and tried again your "ndiswrapper" suggestion. IT WORKED! Now I am writing you using the wireless on Ubuntu.
Thanks again!

---

