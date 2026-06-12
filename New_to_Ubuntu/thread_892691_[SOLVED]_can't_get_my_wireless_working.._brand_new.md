---
title: "[SOLVED] can't get my wireless working.. brand new.. please help"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by binobooks on 2008-08-17
Here is the info from the NDISwrapper site about my card
Card: Netgear WG311 v2 (TI ACX 111 Chipset)

    *
      Chipset: TEXAS INSTRUMENTS ACX 111 54Mbps Wireless Interface
    *
      pciid: 0000:00:0b.0
    *
      Driver: acx_pci from acx100.sf.net w/o enc or NDISwrapper

I am brand new to linux and have no clue what I should do to get this working.  I have the new Ubuntu 8.0.4 distro.  I also have a linksys wireless usb adapter (WUSB54GS) but tried connecting it through usb and nothing happened.

Please help... I have spent hours looking for info****

---

### Post by nothingspecial on 2008-08-17
Ok what have you tried so far.

---

### Post by binobooks on 2008-08-17
I tried most of the steps in the help menu on the desktop except that I couldn't find windows wireless drivers under admin so I couldn't install the .inf driver file... the help says to install ndisgtc under synaptic package manager and I could not find that as well then it says to open ndisgtk under windows wireless driver in admin and couldn't find that.   I tried some other posts online but they were for older versions and things were not matching up.

---

### Post by binobooks on 2008-08-17
I tried most of the steps in the help menu on the desktop except that I couldn't find windows wireless drivers under admin so I couldn't install the .inf driver file... the help says to install ndisgtc under synaptic package manager and I could not find that as well then it says to open ndisgtk under windows wireless driver in admin and couldn't find that. I tried some other posts online but they were for older versions and things were not matching up.

---

### Post by lswest on 2008-08-17
go to this site: [http://kbserver.netgear.com/products/WG311v2.asp](http://kbserver.netgear.com/products/WG311v2.asp)

download the newest drivers (it's a zip archive), then extract it by right-clicking and choosing "extract here".

then do:
```
sudo ndiswrapper -i /*path to extracted files*/Driver/Windows\ XP/wg311v2.inf
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```
please replace "path to extracted files" with the actual path.

if that does not work, please post the output of ```
sudo lshw -C network
``` in case we have to blacklist any other drivers.

if it does work, do this: ```
sudo gedit /etc/modules
``` and add "ndiswrapper" (without the quotes) to the end of that file, so that it loads on login.

---

### Post by binobooks on 2008-08-17
thanks, I will try this... I don't have any internet connectioin to my ubuntu desktop so I will burn a cd with the zip file

---

### Post by lswest on 2008-08-17
> **binobooks said:**
> thanks, I will try this... I don't have any internet connectioin to my ubuntu desktop so I will burn a cd with the zip file

I assumed you'd have some way of transporting it to the other PC, CD or USB stick or anything would be fine, it's a pretty small zip file.  Good luck.

---

### Post by nothingspecial on 2008-08-17
> **binobooks said:**
>  the help says to install ndisgtc 

It`s ndisgtk

---

### Post by binobooks on 2008-08-17
it keeps on saying command not found

---

### Post by binobooks on 2008-08-17
here is my output of lshw -C network
binobooks@binobooks-desktop:~$ sudo lshw -C network
[sudo] password for binobooks: 
  *-network:0             
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: wlan0
       version: 00
       serial: 00:0f:b5:07:7c:dc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:98:9e:b0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
binobooks@binobooks-desktop:~$

---

### Post by nothingspecial on 2008-08-17
> **binobooks said:**
> it keeps on saying command not found

When you type what?

---

### Post by binobooks on 2008-08-17
i could not find ndisgtk (thats what I meant)

---

### Post by binobooks on 2008-08-17
when I was typing in lswest's command directions he posted.... the first set of sudo ndiswrapper

---

### Post by nothingspecial on 2008-08-17
Have you typed -
```
sudo apt-get install ndisgtk
```

---

### Post by nothingspecial on 2008-08-17
I`m hoping someone else can help because I have to go now.
Make sure you have installed ndisgtk 
Download the drivers
Install them using ndisgtk
Its in your menus somewhere (sorry not on my laptop)
I`ll check back tommorow when I have more time.
Don`t worry, it will work, and when you`ve got it working you`ll realise that you know a good bit about linux.:)

---

### Post by binobooks on 2008-08-17
i tried installing ndisgtk but it said could not get lock var/lib/dpkg/lock - open (11 resource temp unavailable)
unable to lok the adminisration directory (is another process using it?

---

### Post by ilovelinux33467 on 2008-08-17
> i tried installing ndisgtk but it said could not get lock var/lib/dpkg/lock - open (11 resource temp unavailable)
unable to lok the adminisration directory (is another process using it?

Are you doing any other apt-get install or have the update manager or synaptic manager open? If you do then you have to close/wait until they are finished before you can install ndisgtk

---

### Post by binobooks on 2008-08-17
I tried it again with everything closed... it said:
Reading package lists... Done
Building dependency tree
REading state information... Done
E: coudn't find package ndisgtk

---

### Post by binobooks on 2008-08-17
I can't find ndisgtk at all when I search for it in synaptic package manager

---

### Post by ilovelinux33467 on 2008-08-17
> I tried it again with everything closed... it said:
Reading package lists... Done
Building dependency tree
REading state information... Done
E: coudn't find package ndisgtk

Please do:

```
sudo apt-get update
```

Then try again:

```
sudo apt-get install ndisgtk
```

---

### Post by binobooks on 2008-08-17
all i get is a bunch of errors when I enter tbis sudo apt-get update into the terminal.  I get a whole list of err and failed to fetch.. 

the computer with ubuntu is not connected to the internet

---

### Post by ilovelinux33467 on 2008-08-17
The computer has to be connected to the internet somehow before you can install the package. Maybe connect it to a wired network somehow?

---

### Post by binobooks on 2008-08-17
i can't connect it any other way... I searched the boot cd and I saw it had ndisgtk on it... is there any way to get it from there

---

### Post by binobooks on 2008-08-17
Thanks everyone.. I finally got it working.. since I didn't have connection to the internet, I installed ndisgtk from the live cd... then put the new driver into the windows wireless driver program and restarted the computer... it worked... amazing..... thanks for all the help...

---

### Post by nothingspecial on 2008-08-18
Glad you got it sorted:guitar:

---

