---
title: "Unstable Wifi With Ubuntu"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by mathiashu on 2013-07-09
Hi!
I have seriously annoying problems with the Wifi on Ubuntu 12.04 LTS 32 Bit. So the story is that I've triedseveral distros now on my computer, and on *all* of them, I've had the same problem: The Wifi is not working proberly! I have tried everything I can imagine including: WICD Network Manager, turn off IPV6, turn off IPV4, restart router and much more but nothing works! :( Then recently I googled: Lenovo G575 (which is my computer) Linux, and found more articles about how to fix the problem. I had to take the Network Boot (or whatever that was) to the first slot in BIOS, so I did that. But. That doesn't work either!!!!!?! Well it's better now, because now it works like 5 minutes and then I don't have connection anymore, well it displays that the connection is fine (in thee right corner) but it doesn't work, and then I will have to reconnect again and again, until it works for another 5-8 minutes. I love Ubuntu and would really like to use it insted of Windows 7, but not if the Wifi doesn't work.
Here is my Iwconfig if that can make it easier.
```
wlan0     IEEE 802.11bgn  ESSID:"My WLAN connection"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: F4:55:9C:A2:DE:94   
          Bit Rate=19.5 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:141  Invalid misc:9   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.
```

If you have suggestions or any kind of help it will really be appreciated.
Thanks.
Mathias.

---

### Post by dannyboy79 on 2013-07-09
what wifi chip is in that computer, can you post the output of the following command please? it's possible that you have a lot of interference (in which you could maybe try a different wifi channel) OR your card just isn't supported well in linux (in which case you may be able to use windows drivers and ndiswrapper)

```
lspci
```

and

```
lshw -class network
```

---

### Post by mathiashu on 2013-07-09
lspci:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6320]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```
And lshw -class network:
```
*-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c1
       serial: dc:0e:a1:87:f1:20
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 multicast=yes port=twisted pair
       resources: irq:41 memory:f0100000-f013ffff ioport:2000(size=128)
  *-network
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:17 memory:f0000000-f0003fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: c0:18:85:4f:7a:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.5.0-36-generic firmware=N/A ip=192.168.2.105 multicast=yes wireless=IEEE 802.11bgn
```

---

### Post by dannyboy79 on 2013-07-09
give this a read [http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working](http://askubuntu.com/questions/127633/how-do-i-get-a-broadcom-bcm4313-wireless-card-working)

---

### Post by ptn107 on 2013-07-09
Use bcmwl-kernel-source.  The trick, though, is to use this version [_here_]("http://mirror.pnl.gov/ubuntu//pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb")** instead of the newest one through apt-get (version 6.20.155.1 is a plague).  At some point in the recent past the latest version was backported from 13.04 to 12.04 LTS and ever since wireless has been crappy at best.

Download it and do the following to install it:
```
sudo apt-get install dkms
sudo dpkg -i bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64.deb
```

**this is the 64-bit package.  If you need the 32-bit one get it [_here_]("http://mirror.pnl.gov/ubuntu//pool/restricted/b/bcmwl/bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_i386.deb").

---

### Post by mathiashu on 2013-07-09
Hi I'm sorry but I don't know how to install tar.gz files and I can't open the .deb file. Yep, welcome to the Ultra-Noob thread. Sorry :(
EDIT: Wait, I'm installing the bcmwl-kernel-source now!!! I will let you know if it works!!!

---

### Post by mathiashu on 2013-07-09
Hi there I'm back, on Windows, because now the Internet does not work at all. So the new Driver sadly didn't help :/ Im uninstalling Ubuntu now...

---

### Post by dannyboy79 on 2013-07-09
did you bother even reading what I linked you? it appears like you just did what the first person sugested instead of any research on your own which of course will get you no where in anything. A user has done a ton of leg work in relation to that chipset and has a solution. IF you had bothered reading what I had linked you.

OR

you could read about it here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by mathiashu on 2013-07-09
YES! I couldn't install the tar.gz file, it just didn't work!! But what should I do if I couldn't acces the Internet in Ubuntu? In fact your post was the first I read, that sadly wouldn't work for me, I tried all the Solutions in that post, but then I saw the second post, that I actually could download! But after that nothing would work! And of course!! I have spent so much time searching on the web and there was no solution, if there was I wouldn't have posted this thread. :(

---

### Post by dannyboy79 on 2013-07-09
are you using 32bit or 64bit ubuntu?

---

### Post by wildmanne39 on 2013-07-09
It is possible that after you installed the deb file you had two drivers loaded at the same time creating a conflict so you need to be patient please and give people time to help you through the process.

Please copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by mathiashu on 2013-07-10
> **dannyboy79 said:**
> are you using 32bit or 64bit ubuntu? As I said in the title I use 32 bit, but, I've also tried with 64, it doesn't make difference.

---

### Post by mathiashu on 2013-07-10
And the link for the tarball [http://sdrv.ms/1bmR916](http://sdrv.ms/1bmR916)

---

### Post by wildmanne39 on 2013-07-10
Hi, first you have an eth2 connection but the dmesg is showing your card using eth1, I recommend you remove all wireless connections from network manager and then reboot and let network manager find the connection.

Also try channel 1 or 11 in your router.

Go into your router and change 802.11b/g/n to 802.11b/g.
Then do:
```
echo -e '#!/bin/bash\n/sbin/iwconfig wlan0 power off' | sudo tee -a /etc/pm/power.d/wireless

```
Reboot computer
Thanks

---

### Post by mathiashu on 2013-07-11
> **Wild Man said:**
> Hi, first you have an eth2 connection but the dmesg is showing your card using eth1, I recommend you remove all wireless connections from network manager and then reboot and let network manager find the connection.

Also try channel 1 or 11 in your router.

Go into your router and change 802.11b/g/n to 802.11b/g.
Then do:
```
echo -e '#!/bin/bash\n/sbin/iwconfig wlan0 power off' | sudo tee -a /etc/pm/power.d/wireless

```
Reboot computer
Thanks

Hi. Thanks for the help. This might sound "crazy", but actually, after a reinstall of Ubuntu (Yesterday) the internet has worked without problems. I don't know how this has fixed itself, but I'm very happy it works! Anyways thanks for the help, if I ever run into problems again I will re-read this thread.

Thanks. :D

---

### Post by BBQdave on 2013-07-11
> **mathiashu said:**
> Hi!
I have seriously annoying problems with the Wifi on Ubuntu 12.04 LTS **32 Bit**. ...Lenovo G575

The proper distro for that hardware is 64-bit.

Under Windows 7, you have no trouble connecting to your router and maintaining a connection; otherwise, the behavior of dropped connection would seem like your router is failing. What makes me suspicion your router, is that you are able to connect with Ubuntu for a few minutes - improper wireless configuration would most likely not allow any connection.

Though I am unsure the side effects of running a 32-bit distro on 64-bit hardware.

---

### Post by dannyboy79 on 2013-07-11
> **BBQdave said:**
> 
Though I am unsure the side effects of running a 32-bit distro on 64-bit hardware.it just wouldn't utilize any RAM over 4GB.

---

### Post by mathiashu on 2013-07-11
Really?! I tought it would slow down my computer to run the 64 bit version. Well thanks for letting me know. :)

---

### Post by dannyboy79 on 2013-07-11
> **mathiashu said:**
> Really?! I tought it would slow down my computer to run the 64 bit version. Well thanks for letting me know. :)
ok, maybe I mispoke but it won't "slow" down your computer but it clearly won't run as fast as it could IF it were running 64 bit versions of code which is optimized to run on 64bit CPU's

---

### Post by deri on 2013-07-11
I have ralink made wifi usb stick. And I get constant timeouts on dmesg. " 2139.797061] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0"

---

### Post by mathiashu on 2013-07-12
> **dannyboy79 said:**
> ok, maybe I mispoke but it won't "slow" down your computer but it clearly won't run as fast as it could IF it were running 64 bit versions of code which is optimized to run on 64bit CPU's

Ok thanks for the help. I'll set the thread as solved.

---

