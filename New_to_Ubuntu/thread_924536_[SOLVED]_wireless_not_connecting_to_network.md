---
title: "[SOLVED] wireless not connecting to network"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by pgar23 on 2008-09-19
Hi all. Its been a while since I've used ubuntu again..so to get right to the point. I have my wireless adapter installed and all of the drivers, the wireless is detecting the networks but is not allowing me to connect to my network. I clicked the network, entered the passkey..but when I try firefox, no luck. Please Help. Thanks in advance.

---

### Post by houbysoft.xf.cz on 2008-09-19
I think I'll not be able to help, but maybe post the output of ifconfig or iwconfig, it'll help others to help you.

---

### Post by pgar23 on 2008-09-19
output of lshw -C network:
[code:]

payton@the-Desktop:~$ sudo lshw -C network
[sudo] password for payton:
  *-network               
       description: Ethernet interface
       product: 82557/8/9 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 10
       serial: 00:08:74:c8:39:6e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A ip=192.168.0.12 latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:39:05:c0:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wusb54gsv2 driverversion=1.45+Linksys,01/25/2005, 4.01.20 link=no multicast=yes wireless=IEEE 802.11g

---

### Post by pgar23 on 2008-09-19
probably an easy fix and I am just overlooking something..

---

### Post by styfle on 2008-09-19
I might be having a similar problem. I made a thread here [http://ubuntuforums.org/showthread.php?t=924554](http://ubuntuforums.org/showthread.php?t=924554)

Try doing a manual connection because that wored for me

---

### Post by pgar23 on 2008-09-19
I tried the manual connection..I can see my network(TheCrib), I click it..and it does nothing??

---

### Post by styfle on 2008-09-19
Did you go to network > (unlock it) > wireless > properties > uncheck roaming > select your network and encryption type
then just type in the password
I also selected automatic DHCP or something

---

### Post by pgar23 on 2008-09-19
roaming was not checked..so i didnt need 2 uncheck it..and I already have dhcp selected..

---

### Post by pgar23 on 2008-09-19
bump:popcorn:

---

### Post by styfle on 2008-09-20
Here's what mine looks like:
[img]http://img146.imageshack.us/img146/1898/wlanyh8.png[/img]

---

### Post by pgar23 on 2008-09-20
yea that is also how my screen is looking, but still I am unable to connect to a network. I tried linksys(an unsecured network) but am still unable to connect. Anyone else have advice??

---

### Post by serian on 2008-09-20
Hi. 
Sorry for my bad english. I'm buy a new notebook(HP Pavilion dv5-1002nr, with Atheros wireless card), one week ago. And I have same problem. In vista it's card work, but in ubuntu not.:(

---

### Post by pgar23 on 2008-09-20
bump

---

### Post by pgar23 on 2008-09-21
bump. still waiting for sum1 to give useful advice or at least point me 2 the thread that would solve the problem..THANKS!

---

### Post by serian on 2008-09-23
> **pgar23 said:**
> bump. still waiting for sum1 to give useful advice or at least point me 2 the thread that would solve the problem..THANKS!

We will waiting for new useful ideas. :confused:

---

### Post by pytheas22 on 2008-09-24
First of all, you may want to try using [wicd]("http://wicd.sourceforge.net") to connect instead of Network Manager.  A lot of people have better luck with wicd.

If that doesn't help, please post the output of:
```

lsusb
lspci -nn
dmesg | grep -e ndis -e wlan
```

Also, if you turn off encryption on your router (if you have the authority to do that), can you connect then?

---

### Post by serian on 2008-10-01
> **pytheas22 said:**
> First of all, you may want to try using [wicd]("http://wicd.sourceforge.net") to connect instead of Network Manager.  A lot of people have better luck with wicd.

If that doesn't help, please post the output of:
```

lsusb
lspci -nn
dmesg | grep -e ndis -e wlan
```

Also, if you turn off encryption on your router (if you have the authority to do that), can you connect then?

lsusb

Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. 

Bus 005 Device 002: ID 0408:03ba Quanta Computer, Inc. 

Bus 005 Device 001: ID 0000:0000  

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 001: ID 0000:0000 


lspci -nn

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]

00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]

00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]

00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]

00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]

00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]

00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]

00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]

00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]

00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]

00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller [1002:4398]

00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]

00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3a)

00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]

00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]

00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]

00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]

00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]

01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] [1002:9612]

01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]

08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

dmesg | grep -e ndis -e wlan

nothing

---

### Post by nothingspecial on 2008-10-01
Are you using madwifi. That fixes this card.

---

### Post by pytheas22 on 2008-10-01
serian,

Please run these commands; they should fix your connection (you will need to be connected to the Internet somehow to run these commands; if that's impossible, let me know):

```
sudo apt-get install build-essential
wget [http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz](http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz)
tar -xzvf compat-wireless-ath9k-20080916.tar.gz
chmod +x compat-wireless-ath9k-20080916.sh
./compat-wireless-ath9k-20080916.sh
sudo dpkg --install compat*deb
echo 'ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
```

Then restart and your wireless connection should work.  If not, please post the output of:
```

lshw -C Network
dmeg | grep -e ath -e wlan
sudo iwlist scan
lsmod | grep ath
```

---

### Post by pgar23 on 2008-10-03
ok so i solved my own problem. duh! i shoulda tried this in the first place. I clicked enable roaming. waited til it changed configuration (about 5 secs) then i right clicked the network icon..a list of netwroks appeared and i happen to have a linksys(unsecured) network around my house so im juz gonna borrow their internet for the time being..lol Thanks guyz.

---

### Post by serian on 2008-10-05
Yes, I'm using madwifi.

> **pytheas22 said:**
> serian,

Please run these commands; they should fix your connection (you will need to be connected to the Internet somehow to run these commands; if that's impossible, let me know):

```
sudo apt-get install build-essential
wget [http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz](http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz)
tar -xzvf compat-wireless-ath9k-20080916.tar.gz
chmod +x compat-wireless-ath9k-20080916.sh
./compat-wireless-ath9k-20080916.sh
sudo dpkg --install compat*deb
echo 'ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
```

Then restart and your wireless connection should work.  If not, please post the output of:
```

lshw -C Network
dmeg | grep -e ath -e wlan
sudo iwlist scan
lsmod | grep ath
```

Ok, I will try again. Thanks, for answer.

---

### Post by paulsjv on 2011-01-09
> **pytheas22 said:**
> serian,

Please run these commands; they should fix your connection (you will need to be connected to the Internet somehow to run these commands; if that's impossible, let me know):

```
sudo apt-get install build-essential
wget [http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz](http://burnthesorbonne.com/files/compat-wireless-ath9k-20080916.tar.gz)
tar -xzvf compat-wireless-ath9k-20080916.tar.gz
chmod +x compat-wireless-ath9k-20080916.sh
./compat-wireless-ath9k-20080916.sh
sudo dpkg --install compat*deb
echo 'ath_pci' | sudo tee -a /etc/modprobe.d/blacklist
```

Then restart and your wireless connection should work.  If not, please post the output of:
```

lshw -C Network
dmeg | grep -e ath -e wlan
sudo iwlist scan
lsmod | grep ath
```

I gave this a shot but when I try to untar gz the file I get the following error.

```

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

```

---

### Post by pytheas22 on 2011-01-09
> I gave this a shot but when I try to untar gz the file I get the following error.

I just tried it and it works alright on my end.  Your download may have gotten corrupted, which prevented the file from being extracted properly.  I'd try removing the compat-wireless-ath9k-20080916.tar.gz and then run the commands again.  If it fails on a second try, please post the exact commands you're typing in, along with all of the output.

Also keep in mind that this thread is more than a couple years old and I'm not sure whether the instructions here will still work on more recent Ubuntu releases.  But they shouldn't hurt either.

---

