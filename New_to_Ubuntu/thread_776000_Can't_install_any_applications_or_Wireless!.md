---
title: "Can't install any applications or Wireless!"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Christian91 on 2008-04-30
Hey guys,

I just installed Ubuntu Hardy heron today and I am completely new to the Linux world. I am having a few complications getting with it though. Firstly, I can't get seem to get on the wireless network. I don't think I have a wireless driver installed because it can't find any wireless networks at all and the button on my PC that should be blue when the wireless is turned on is orange like when it's off! I also can't even install applications in the Add/Remove. When I try I get this message: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct this problem.
E: _cache->open() failed, please report"

I have no idea what that means, and I have been trying to get it running all day.. PLease help me anyone!! :D

---

### Post by forrestcupp on 2008-04-30
Well, firstly, about the error, open a terminal and type
```
sudo dpkg --configure -a
```

---

### Post by wolfen69 on 2008-04-30
open teminal and:
```
sudo dpkg --configure -a
```

---

### Post by forrestcupp on 2008-04-30
Also, in your terminal, type
```
sudo apt-get install linux-restricted-modules
```You should be able to install that off of your CD.  Then go to System->Administration->Hardware Drivers, and see if it has a driver for your wireless that you can enable.

---

### Post by Christian91 on 2008-04-30
Ok, thanks! I got the applications to work now. But I just can't get the wireless to work. In the Hardware Drivers there is a: "Broadcom B43 wireless driver" in use. But it still doesn't show any wireless networks in the network manager?

---

### Post by lswest on 2008-04-30
can you post the output of ```
lspci
``` and you can (as long as the card isnt a bcm4311 rev2) install the firmware via [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) otherwise you will need to use ndiswrapper to do it, but i can guide you through that if you need.

---

### Post by Christian91 on 2008-04-30
When i write lspci:


christian@christian-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
christian@christian-laptop:~$

---

### Post by lswest on 2008-04-30
> 03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01) is your wireless card, and (to the best of my knowledge) it should work after you follow the [instructions]("http://linuxwireless.org/en/users/Drivers/b43") i posted above (would require you to connect to the internet via an ethernet cable though)

---

### Post by Christian91 on 2008-04-30
Thanks mate, I followed the link and tried what it said but I can't really seem to make any sense of it. I'm completely new to Ubuntu so i'm pretty stupid in this matter :S

---

### Post by lswest on 2008-04-30
no problem.
> You are using the b43 driver from linux-2.6.24

If you are using the b43 driver from linux-2.6.24, follow these instructions.

Use version 011 of b43-fwcutter.
Download, extract the b43-fwcutter tarball and build it:

```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
```
Use version 4.80.53.0 of Broadcom's proprietary driver.
Download and extract the firmware from this driver tarball:

```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
```

Note that you must adjust the FIRMWARE_INSTALL_DIR path to your distribution. The standard place where firmware is installed to is /lib/firmware. However some distributions put firmware in a different place. 

Basically, what it needs you to do is:
run these commands (one line=one command, anything after a # is a comment, and is just meant to clarify commands)
```
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
#this downloads the archive with the required files for installing fwcutter
tar xjf b43-fwcutter-011.tar.bz2
#this extracts the archive
cd b43-fwcutter-011
#this changes directory to where you extracted the above archive to.
make
#this installs the program
cd ..
#this moves one directory up
``` should install the fwcutter program required.

then run these:
```

export FIRMWARE_INSTALL_DIR="/lib/firmware"
#creates a variable with the path to where the firmware will be stored
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
#again, it downloads the archive
tar xjf broadcom-wl-4.80.53.0.tar.bz2
#extracts it
cd broadcom-wl-4.80.53.0/kmod
#changes directory to the folder "kmod" in the directory "broadcom-wl-4.80.53.0"
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o
#extracts the firmware
```

Each of those commands can just be copied and pasted into your terminal (found under applications-->accessories-->terminal).  Once done, just reboot and wireless should be working.

---

### Post by Christian91 on 2008-04-30
Thank you, I'll try and get back to you in a bit :)

---

### Post by lswest on 2008-04-30
No problem, i remember when i first started off, i was dependent on a friend of mine for a while for translations ;) don't worry, you'll get used to those kinds of instructions soon enough lol.  Anyways, always happy to help.

---

### Post by Christian91 on 2008-04-30
I don't know if I'm just completely stupid but I still can't get it to work. When I click on the network configuration on the top of the screen it still only says manual configuration. And if I go into that it doesn't show any networks. Under connections you can choose: Wireless connection, Wired connection and Point to point connection and configure those.

Is that the way it should be or is it still not on ?

---

### Post by lswest on 2008-04-30
no, that's not the way it should be, can you post the output of ```
iwconfig

lshw -C network
``` it seems something isn't yet working.

Also, make sure your wireless card is set on "roaming mode"

---

### Post by Christian91 on 2008-04-30
christian@christian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

christian@christian-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:ec:e5:18
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
christian@christian-laptop:~$ 
christian@christian-laptop:~$

---

### Post by lswest on 2008-04-30
does setting the network manually work? ```
sudo iwconfig wlan0 essid [name of your wireless network] key [wireless key]

iwconfig
``` and check to see that the output of iwconfig (second time round) returns the info you gave in the first time.  Also, make sure your wireless card isn't turned off (the switch).  If the changes were saved, get an IP with this command:
```
sudo dhclient wlan0
```

---

### Post by fraser_m on 2008-04-30
Make sure you've done that dpkg reconfigure thing, the open up a terminal and type
```
sudo apt-get install b43-fwcutter
```

Make sure you have internet, Ethernet or summink, plugged in.

If you can't connect tell us, and I'll help you do it manually.

---

### Post by lswest on 2008-04-30
> **fraser_m said:**
> Make sure you've done that dpkg reconfigure thing, the open up a terminal and type
```
sudo apt-get install b43-fwcutter
```

Make sure you have internet, Ethernet or summink, plugged in.

If you can't connect tell us, and I'll help you do it manually.

i already had him do it manually, because i found it worked best, probably best if we finish doing it one way instead of doing it two ways at once.

---

### Post by Christian91 on 2008-04-30
This is what it says when I write what you said:


christian@christian-laptop:~$ sudo iwconfig wlan0 essid
Error for wireless request "Set ESSID" (8B1A) :
    too few arguments.
christian@christian-laptop:~$ key
usage:	key [-n num] [-f func] sequence seed
	key -i
christian@christian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"[name"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

christian@christian-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 7009
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:14:a5:ec:e5:18
Sending on   LPF/wlan0/00:14:a5:ec:e5:18
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
christian@christian-laptop:~$

---

### Post by lswest on 2008-04-30
ah, sorry, you misunderstood my instructions.  Say for example your wireless is called "home" and the key is "0b86828bc" the command would then be (one command) ```
sudo iwconfig wlan0 essid home key 0b86828bc
``` but replace the "home" and the "0b86828bc" with the name of your network, and replace the key as well (if there is one, if not, just leave out the "key" bit)

Also, can you post the output of ```
sudo iwlist scan
```

---

### Post by Christian91 on 2008-04-30
Ok :D but then it says:

christian@christian-laptop:~$ sudo iwconfig wlan0 essid HJEMME key **key** 
[sudo] password for christian: 
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "**key**".

I'm sure it is the right key and I am sure the switch is on for the wireless.

---

### Post by Christian91 on 2008-04-30
christian@christian-laptop:~$ sudo iwlist scan
[sudo] password for christian: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

christian@christian-laptop:~$

---

### Post by lswest on 2008-04-30
what encryption are you using? WEP Hex, or a WEP ascii password/passkey? if it's a password or passkey, add a "s:" before it so that it reads ```
key s:passkey
```where passkey is the password you're using.

If it's WPA, it may not work from terminal, and if it is a WPA key, skip the above step and just post the output of ```
sudo iwlist scan
```

---

### Post by Christian91 on 2008-04-30
I tried with the s: but didn't seem to work. How do I know which encryption is used?

outcome of sudo iwlist scan:
 
christian@christian-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

christian@christian-laptop:~$

---

### Post by lswest on 2008-04-30
well, the drivers don't seem to be installed properly, if you check in "system-->administration-->hardware manager" and see if it says the driver is in use, if not, mark the checkbox, and follow the prompts, which should install the proper firmware, if that still doesn't work, i'd say go with ndiswrapper and a windows driver, but that i can explain if the other method doesn't work.

---

### Post by Christian91 on 2008-04-30
Thank you so much Iswest for all your help, suddenly everything worked! Also the driver for the graphic card. I don't know what the **** was wrong when I couldn't activate any of the drivers. Now everything works.

Couldn't thank you enough :D

---

### Post by lswest on 2008-04-30
Great, and one last thing, it's not an "I" it's an "L" but hey :p thanks for the thanks, and glad it's working ^^

*EDIT* also, if you could be so kind as to mark this thread as solved people will know there is a solution here, it can be done via "thread tools" at the top of the page.

---

