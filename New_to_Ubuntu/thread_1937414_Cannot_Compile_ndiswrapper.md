---
title: "Cannot Compile ndiswrapper"
date: 2012-03-07
forum: New to Ubuntu
---

### Post by tj7572 on 2012-03-07
Hi all,

I am trying to install a wireless device with ndiswrapper.  I have followed the steps in this tutorial:
[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)

That is, I have:

1) installed build-essential
2) downloaded the Windows driver
3) extracted ndiswrapper (tar -xzvf)

When I cd into the ndiswrapper directory and run make, I get (warnings?) about a 'char' is expected but argument is of type 'iwe_stream_add_point'

Then 2 errors:

*** [/home/tim/ndiswrapper-1.51/driver/iw_ndis.c] Error1
*** [_module_/home/tim/ndiswrapper-1.51/driver] Error2


Any thoughts?
Thanks, Tim

---

### Post by anewguy on 2012-03-07
*DON'T*, I repeat *DON'T* compile ndiswrapper.

If you need ndiswrapper you can install it directly from the media you installed Ubuntu with.

I have posted instructions for this many, many times, but will try a short version here:

- boot Ubuntu
- put the distribution cd (or usb flash drive if you used it) in the drive
- use the file navigator to explore the media
- go to the /pool/main/n/ndiswrapper folder
- double click on the ndiswrapper common file to start its'install, and wait for it to finish
- double click on the ndiswrapper utilities file to start its' install, and wait for it to finish
- go to the /pool/main/n/ndisgtk folder
- double click on the ndisgtk folder to start its' install and wait for it to finish
- now go to windows wireless drivers (I think that's what it's called in the menus) or type ndisgtk and press enter in the command line.
- select new/add whatever it is
- point it to your .inf file for your driver and ok/add whatever it

That should do it. Wait a minute or 2, be sure wireless is enabled in the network manager icon, then look to see if wireless networks are showing,

REMEMBER:

- Windows XP drivers only
- you need the .inf and .sys file(s) for the driver
- the driver architecture must match your Ubuntu architecture - 32 or 64 bit

For you and others:  the thread you were looking at is "ancient" in terms of things now.  I'm glad to see someone who actually tried to do something themselves before asking a question, so please don't let that deter you.  Just remember when you do a search in the forums or on the net to look for the newest posts - they'll usually have the most current information for you.

If you have ANY problems or questions, just post!

Best of luck,
Dave ;)

---

### Post by tj7572 on 2012-03-09
Hi Dave,
 
Thanks for the reply.
 
Unfortunately, I still have problems.  What I am trying to install is an old Netgear wireless adaptor to  get online w/ Ubuntu.
 
I followed the instructions you sent and ended up with the message that the driver is installed.
 
However I still do not have internet (using a Windows set up for this, tryig to get Ubuntu going on a desktop).
 
More information:
It is a Netgear WPN111 wireless adaptor (works fine w/ Windows)
The drive I am trying to install I got from the tutorial I lined to previously:
[http://ubuntuforums.org/showthread.php?t=652910](http://ubuntuforums.org/showthread.php?t=652910)
After going through the instructions in your post, Ubuntu tells me the driver is installed.
 
 
 
Any other ideas are appreciated, thanks,
Tim

---

### Post by anewguy on 2012-03-10
can you "Enable Wireless" under network maanager?

BTW - if you did anything in the past or after my instrutions that are from another thread, you need to reverse all of those things. Not doing so,so as to start with a clean slate when you go to Windows Wireless Drivers will only compound problems.  Please explain in detail the steps you took prior to posting and since following my instructions.

dave ;)

---

### Post by edm1 on 2012-03-10
Does it start if you load the ndiswrapper module using

```
sudo modprobe ndiswrapper
```
?

If so you can use this command to automatically load ndiswrapper when you boot
```

su
echo "ndiswrapper" >> /etc/modules
exit

```

---

### Post by lkraemer on 2012-03-10
ndiswrapper should be a LAST RESORT CHOICE, but sometimes it's the ONLY way
you can get your Wifi working.  Most newer Distro's Wifi work out of the
BOX, or by just adding the Firmware.................


**1. How do I know if I have XXXXX Hardware?**

Open a Terminal Window and use these commands to get more information
on your hardware, wireless, Windows loaded drivers, and Linux drivers
that are currently blacklisted. Copy & Paste to prevent errors!
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
Post the output of each command........

**#1 - NDISWRAPPER**
To install the Windows Drivers that are located on your Desktop in a
folder named xyzdriver (.sys & .inf files) and have already been extracted:
```

cd ~/Desktop/xyzdriver
sudo ndiswrapper -i somefilenamed.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
lsmod
ifconfig
iwconfig

```
To make sure it starts on boot:
```

echo ndiswrapper | sudo tee -a /etc/modules

```
Then I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

SKIP to FINISH below.......


**REMOVE WINDOWS DRIVERS:**
If you want to REMOVE the Windows Drivers:...............
If the output of ndiswrapper -l shows any drivers loaded,
remove ALL of them. The following commands are an EXAMPLE ONLY and
your will/may be different **USE SOMETHING SIMILAR TO**:
```

sudo ndiswrapper -e bcmwl5
sudo ndiswrapper -e ssb

```
This should clean up nidswrapper & drivers and:
```

ndiswrapper -l

```
should return nothing as being loaded.

Then remove ndiswrapper:
```

sudo modprobe -r ndiswrapper

```
Remove from startup file by editing:
```

sudo nano /etc/modules

```
to remove ndiswrapper.


**FINISH:**

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```

Click on the Wifi Icon in the top right toolbar and select the Network.

OR use:

**Manual Choice:**
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```
example......for Airlink and wlan0
sudo iwconfig wlan0 essid "Airlink"

To verify that your Wifi is connected and working use:
```

ping -c 3 www.google.com

```
or
```

ping -c 3 74.125.224.241
ping -c 3 8.8.8.8

```


It shouldn't take more than about 15 minutes......

lk

---

### Post by tj7572 on 2012-03-11
Hi again, thanks for the help.

Still no wireless connection, though I believe I have the driver installed (for the Netgear adapter).

lkraemer, here are the output from the commends you asked to see:
(the ndiswrapper -l output shows a problem, I think...)

Thanks agian.
Tim

lspci:
00:00.0 Host bridge: Intel Corporation Device 0100 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Device 1c5c (rev 05)
00:1f.2 SATA controller: Intel Corporation Cougar Point 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 677b
01:00.1 Audio device: ATI Technologies Inc Device aa98
05:00.0 Network controller: RaLink Device 5390
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)


lsusb:
Bus 002 Device 007: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Bus 002 Device 006: ID 0461:0010 Primax Electronics, Ltd 
Bus 002 Device 005: ID 04a9:173a Canon, Inc. 
Bus 002 Device 004: ID 050d:0234 Belkin Components F5U234 USB 2.0 4-Port Hub
Bus 002 Device 003: ID 046d:c52b Logitech, Inc. 
Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


sudo lshw -C network:
*-network UNCLAIMED     
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fe500000-fe50ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 38:60:77:b9:87:87
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:d000(size=256) memory:d0004000-d0004fff(prefetchable) memory:d0000000-d0003fff(prefetchable)

ndiswrapper -l:
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netwpn11 : driver installed
    device (1385:5F01) present


cat /etc/modprobe.d/blacklist.conf:
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac


iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by lkraemer on 2012-03-12
OK,
One thing I forgot to mention is that your Windows Drivers must be the same 32 or 64 Bit Drivers
as your *NIX Version 32 or 64 Bit.  If that isn't the case, it doesn't work.....

Will you be using WEP or WPA/WPA2?  Better do some reading at the URL's below before proceeding......


Another site describes your Hardware as:
> 
# Card: Netgear WPN111 108Mbps RangeMAX USB (with super G/MIMO)

* Chipset: Atheros USB
* pciid: 1358:5f01

* Driver: Windows XP driver available on the Netgear CD: netwpn11.inf + wpn111.sys + ar5523.

If you have the CDROM that came with the unit, you are going to need the ar5523 Firmware file......
or you can jump to the **ALTERNATE WAYS:** section below and follow the information at the bottom
of the first URL to use Wine to extract your firmware file that you will need............
I've attached a link at the bottom of the posting to Version 2 of the drivers............

I need the following commands executed in a Terminal and the results posted:
```

lsusb -v -d 1385:5f01
ndiswrapper -v

```

Your Device:ID is shown in the list at: [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
(DEVICE ID 1385:5f01)

NOTE:  Don't worry about the ndiswrapper WARNING.

And I think more good information is located at: [http://wiki.debian.org/ar5523](http://wiki.debian.org/ar5523)
where it states how to download the Firmware and install it.
BUT, before you do this, let's make sure it's the correct Firmware
associated with your Hardware by checking what you posted............for > lsusb -v -d Device:ID

**Download & Extract the Firmware, or copy from your included CDROM, or extract it with Wine:**
```

wget http://verein.lst.de/~hch/ar5523.tgz
cd /path/to/ar5523.tgz
tar xvf ar5523.tgz ar5523/uath-ar5523.bin --strip 1
sudo mv uath-ar5523.bin /lib/firmware

```
And that should put the proper Firmware where it should be located.

Now, repeat the following commands and re-post their output:
```

sudo /etc/init.d/networking restart
ls -alt /lib/firmware
lsmod
ifconfig
iwconfig

```
If iwconfig shows:
> 
wlan0     IEEE 802.11bgn  ESSID:"your-essid-shown-here"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 67:67:F0:0D:67:67   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

then you have made progress, so try one of the ping commands:
```

ping -c 3 www.yahoo.com

```


**CLEANUP ndiswrapper Compile attempt:**
Also, let's cleanup what you have previously tried by using these commands in a Terminal:
```

cd /ndiswrapper-1.51
make clean
exit

```
Now from your GUI tag the ndiswrapper-1.51 subdirectory and delete it.


**Alternate ways:**
Also, Here are two completely different ways you can always try:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WPN111](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WPN111)
[http://ubuntuforums.org/archive/index.php/t-1059251.html](http://ubuntuforums.org/archive/index.php/t-1059251.html)
but, for the second way, you will have to remove the windows drivers and ndiswrapper following
the previously posted information.  Just don't mix-n-match different methods......


**Version 2 of the Windows Drivers & Firmware:**
[http://ubuntuforums.org/attachment.php?attachmentid=83057&d=1219873086](http://ubuntuforums.org/attachment.php?attachmentid=83057&d=1219873086)

**REF:**
[http://ubuntuforums.org/showthread.php?p=5670733](http://ubuntuforums.org/showthread.php?p=5670733)


lk

---

### Post by verymadpip on 2012-03-12
Hi folks.

I got the WPN111 working using this guide:

[http://only4geeks.net/?p=37](http://only4geeks.net/?p=37)                                                             

I used ndisgtk for the driver install & followed the terminal commands to do all the checking & module loading stuff.

It's seems a bit old, yet it worked very well with Oneiric.  (I'm currently having a problem with ndiswrapper in Precise beta1 but maybe I'm expecting a bit much at this point in the cycle).

---

### Post by tj7572 on 2012-03-13
Hi
Thanks for the help.

OK, no wireless yet, this is getting a tad frustrating.
Let me give you some info/answers to your questions, then I'll paste the results to the commands you asked for.

First, I am running 64 Bit Ubuntu 10.04.3

I do not have the CD for the wireless device, and I have to say I did not understand the instructions to install with WINE.

I cleaned-up ndiswrapper-1.51 as per your instructions.

The instructions you left regarding the FIRST link under "**Alternate ways:**" were followed, and I moved the uath-ar5523.bin under the /lib/firmware directory, to no success.  

I have 2 questions:
In reading through the links you left, it seems this Netgear device often does not get along with Ubuntu.  IS IT A GOOD IDEA TO PURCHASE ANOTHER DEVICE?  Cisco or something?

I did not understand what to do with the netgear_v2.tar.gz or the ubuntu_packages,tar,gz files ... ?   I got these from the REF link you posted.  I worked thorough the instructions, but when I saw I did not have the blinking light nor a connection, I stopped.

Thanks for hanging with me here, appreciate it,
Tim


Here are the results of the commands:

lsusb -v -d 1385:5f01
Bus 002 Device 006: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1385 Netgear, Inc
  idProduct          0x5f01 WPN111 (no firmware)
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


ndiswrapper -v
ERROR: modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
[http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)



lsusb -v -d 1385:5f01
Bus 002 Device 006: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          255 Vendor Specific Class
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1385 Netgear, Inc
  idProduct          0x5f01 WPN111 (no firmware)
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 3 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
can't get device qualifier: Operation not permitted
can't get debug descriptor: Operation not permitted
cannot read device status, Operation not permitted (1)


sudo /etc/init.d/networking restart
* Reconfiguring network interfaces...


ls -alt /lib/firmware
drwxr-xr-x 48 root root    4096 2012-03-13 18:14 .
drwxr-xr-x 16 root root   12288 2012-03-05 11:51 ..
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 3com
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 acenic
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 adaptec
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 advansys
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 asihpi
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 av7110
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 bnx2
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 cis
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 cpia2
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 cxgb3
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 dabusb
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 dsp56k
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 e100
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 ea
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 edgeport
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 emi26
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 emi62
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 ess
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 kaweth
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 keyspan
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 keyspan_pda
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 korg
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 libertas
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 matrox
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 mwl8k
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 myricom
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 ositech
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 qlogic
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 r128
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 radeon
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 RTL8192E
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 RTL8192SE
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 sb16
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 scripts
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 slicoss
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 sun
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 sxg
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 tehuti
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 tigon
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 ttusb-budget
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 usbdux
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 vicam
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 yam
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 yamaha
drwxr-xr-x  2 root root    4096 2012-02-14 05:46 zd1211
drwxr-xr-x 32 root root    4096 2012-02-14 05:45 2.6.32-38-generic
-rw-r--r--  1 root root  340696 2011-03-03 11:00 iwlwifi-5000-5.ucode
-rw-r--r--  1 root root  463692 2011-03-03 11:00 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root   70624 2011-02-18 13:01 ar7010_1_1.fw
-rw-r--r--  1 root root  444128 2011-02-11 09:26 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-11 09:26 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root   22622 2010-12-14 11:26 aic94xx-seq.fw
-rw-r--r--  1 root root   15960 2010-12-14 11:26 ar9170.fw
-rw-r--r--  1 root root   30348 2010-12-14 11:26 atmel_at76c502_3com.bin
-rw-r--r--  1 root root   31764 2010-12-14 11:26 atmel_at76c502.bin
-rw-r--r--  1 root root   31764 2010-12-14 11:26 atmel_at76c502d.bin
-rw-r--r--  1 root root   31776 2010-12-14 11:26 atmel_at76c502e.bin
-rw-r--r--  1 root root   35180 2010-12-14 11:26 atmel_at76c504_2958.bin
-rw-r--r--  1 root root   39928 2010-12-14 11:26 atmel_at76c504a_2958.bin
-rw-r--r--  1 root root   31748 2010-12-14 11:26 atmel_at76c504.bin
-rw-r--r--  1 root root   31824 2010-12-14 11:26 atmel_at76c506.bin
-rw-r--r--  1 root root 1142480 2010-12-14 11:26 i2400m-fw-usb-1.3.sbcf
-rw-r--r--  1 root root  209190 2010-12-14 11:26 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 2010-12-14 11:26 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 2010-12-14 11:26 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 2010-12-14 11:26 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2010-12-14 11:26 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2010-12-14 11:26 ipw2200-sniffer.fw
-rw-r--r--  1 root root  469780 2010-12-14 11:26 iwlwifi-6050-5.ucode
-rw-r--r--  1 root root   15664 2010-12-14 11:26 NPE-B
-rw-r--r--  1 root root   15664 2010-12-14 11:26 NPE-C
-rw-r--r--  1 root root  262144 2010-12-14 11:26 v4l-cx2341x-dec.fw
-rw-r--r--  1 root root  376836 2010-12-14 11:26 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root  155648 2010-12-14 11:26 v4l-cx2341x-init.mpg
-rw-r--r--  1 root root    8192 2010-12-14 11:26 v4l-pvrusb2-24xxx-01.fw
-rw-r--r--  1 root root    8192 2010-12-14 11:26 v4l-pvrusb2-29xxx-01.fw
-rw-r--r--  1 root root   62484 2010-12-14 11:26 zd1201-ap.fw
-rw-r--r--  1 root root   70612 2010-12-14 11:26 zd1201.fw
-rw-r--r--  1 root root   50698 2010-12-14 11:25 agere_ap_fw.bin
-rw-r--r--  1 root root   65046 2010-12-14 11:25 agere_sta_fw.bin
-rw-r--r--  1 root root   83968 2010-12-14 11:25 ar9170-1.fw
-rw-r--r--  1 root root    3508 2010-12-14 11:25 ar9170-2.fw
-rw-r--r--  1 root root  246804 2010-12-14 11:25 ath3k-1.fw
-rw-r--r--  1 root root    9726 2010-12-14 11:25 atmsar11.fw
-rw-r--r--  1 root root  165768 2010-12-14 11:25 bnx2x-e1-4.8.53.0.fw
-rw-r--r--  1 root root  162800 2010-12-14 11:25 bnx2x-e1-5.2.7.0.fw
-rw-r--r--  1 root root  192400 2010-12-14 11:25 bnx2x-e1h-4.8.53.0.fw
-rw-r--r--  1 root root  205488 2010-12-14 11:25 bnx2x-e1h-5.2.7.0.fw
-rw-r--r--  1 root root   12401 2010-12-14 11:25 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root   33768 2010-12-14 11:25 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root 1251036 2010-12-14 11:25 i2400m-fw-usb-1.4.sbcf
-rw-r--r--  1 root root   34304 2010-12-14 11:25 intelliport2.bin
-rw-r--r--  1 root root  335056 2010-12-14 11:25 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  150100 2010-12-14 11:25 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-12-14 11:25 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-12-14 11:25 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-12-14 11:25 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  337400 2010-12-14 11:25 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  462280 2010-12-14 11:25 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root   13847 2010-12-14 11:25 mts_cdma.fw
-rw-r--r--  1 root root   14067 2010-12-14 11:25 mts_edge.fw
-rw-r--r--  1 root root   13847 2010-12-14 11:25 mts_gsm.fw
-rw-r--r--  1 root root   76802 2010-12-14 11:25 ql2100_fw.bin
-rw-r--r--  1 root root   84566 2010-12-14 11:25 ql2200_fw.bin
-rw-r--r--  1 root root  123170 2010-12-14 11:25 ql2300_fw.bin
-rw-r--r--  1 root root  132978 2010-12-14 11:25 ql2322_fw.bin
-rw-r--r--  1 root root  228056 2010-12-14 11:25 ql2400_fw.bin
-rw-r--r--  1 root root  199776 2010-12-14 11:25 ql2500_fw.bin
-rw-r--r--  1 root root    8192 2010-12-14 11:25 rt2561.bin
-rw-r--r--  1 root root    8192 2010-12-14 11:25 rt2561s.bin
-rw-r--r--  1 root root    8192 2010-12-14 11:25 rt2661.bin
-rw-r--r--  1 root root    8192 2010-12-14 11:25 rt2860.bin
-rw-r--r--  1 root root    4096 2010-12-14 11:25 rt2870.bin
-rw-r--r--  1 root root    4096 2010-12-14 11:25 rt3070.bin
-rw-r--r--  1 root root    4096 2010-12-14 11:25 rt3071.bin
-rw-r--r--  1 root root    2048 2010-12-14 11:25 rt73.bin
-rw-r--r--  1 root root   13765 2010-12-14 11:25 ti_3410.fw
-rw-r--r--  1 root root   13764 2010-12-14 11:25 ti_5052.fw
-rw-r--r--  1 root root    7614 2010-12-14 11:25 tr_smctr.bin
-rw-r--r--  1 root root     999 2010-12-14 11:25 usbduxfast_firmware.bin
-rw-r--r--  1 root root    1770 2010-12-14 11:25 usbdux_firmware.bin
-rw-r--r--  1 root root   16382 2010-12-14 11:25 v4l-cx231xx-avcore-01.fw
-rw-r--r--  1 root root  141200 2010-12-14 11:25 v4l-cx23418-apu.fw
-rw-r--r--  1 root root  158332 2010-12-14 11:25 v4l-cx23418-cpu.fw
-rw-r--r--  1 root root   16382 2010-12-14 11:25 v4l-cx23418-dig.fw
-rw-r--r--  1 root root   16382 2010-12-14 11:25 v4l-cx23885-avcore-01.fw
-rw-r--r--  1 root root   16382 2010-12-14 11:25 v4l-cx23885-enc.fw
-rw-r--r--  1 root root   16382 2010-12-14 11:25 v4l-cx25840.fw
-rw-r--r--  1 root root   23554 2010-12-14 11:25 whiteheat.fw
-rw-r--r--  1 root root    5626 2010-12-14 11:25 whiteheat_loader.fw
-rw-r--r--  1 tim  tim   147664 2006-09-16 13:09 uath-ar5523.bin


lsmod
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_atihdmi     3023  1 
joydev                 11104  0 
snd_hda_codec_realtek   279072  1 
usbhid                 41116  0 
hid                    83888  1 usbhid
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                65040  0 
serio_raw               4918  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            50633  1 
ahci                   38350  1 
r8169                  39714  0 
mii                     5237  1 r8169


ifconfig
eth0      Link encap:Ethernet  HWaddr 38:60:77:b9:87:87  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7088 (7.0 KB)  TX bytes:7088 (7.0 KB)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by 3rdalbum on 2012-03-13
I have no experience with this device, but I don't think you need ndiswrapper.

The device is listed with the "(no firmware)" warning in the info you just posted. This suggests to me that there is a driver loaded, and all you need is the device's firmware file. Once you provide that and reboot, you should be in business.

Do a search for the device's name plus the word 'firmware' and you should be able to find the file you need.

To answer your other question, it is definitely better to buy a device that works out of the box on Ubuntu. I believe all of Alfa's USB wireless devices work on Ubuntu, so that may be a good option. I have two that work out of the box.

---

### Post by wildmanne39 on 2012-03-13
Hi, you have an internal wireless card is there a reason that you do not want to install the driver for it?
thanks

---

### Post by lkraemer on 2012-03-13
Tim,
It appears as I have overwhelmed you with information.  I should have
refined my posting after finding the Version 2 Drivers and posting the
link.  It appears that you have removed ndiswrapper as lsmod doesn't show
it in the loaded modules.  Is this correct?

Let's correct the one thing I noticed in the firmware, and then have you reboot.  Copy & paste this:
```

cd /
cd /lib/firmware
sudo mv uath*.bin ar5523.bin
sudo chown root:root ar5523.bin
sudo chmod 644 ar5523.bin
ls -alt ar5523.bin

```
then list the output of ls -alt ar5523.bin

Did you install the Windows Version 2 drivers with ndisgtk?

Don't worry about not having the CDR of Drivers, or installing them in Wine.  (It just allows you to install the drivers in Wine to get them extracted, but you have the Version 2 Drivers available from the other link.)

Post the output of:
```

ndiswrapper -l

```

lk

---

