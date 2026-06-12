---
title: "Installed 11.10, absolutley no internet"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by JonBruce on 2011-12-29
Hello, I'm new to Ubuntu (first install) and and have a small snag.

Installed on a compaq presario v5000, wireless says it's disabled by hardware switch- however pressing the switch does not turn it on.

Also, wired connections do not work either, it cyclically tries to connect and disconnects.

How do I start the troubleshooting process?

This laptop a gift I gave for Christmas, i rally need to make it work :(

---

### Post by halitech on 2011-12-29
if you open a terminal and enter
```
sudo ifconfig
```
what is the output?

---

### Post by JonBruce on 2011-12-29
I'm looking and retyping what I see on the laptop, so forgive me for taking so long, but here it is:

eth0     Link encap: Ethernet HWaddr 00:16:d4:42:a4:08
         inet 6 addr: fe80::216:d4ff:fe42:a408/64 Scope:Link
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0  txqueuelen:1000
         RXbytes:0(0.0B)  TX bytes:0(0.0B)
         Interrput:22 Base address: 0xa000
         
lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets: 96 errors:0 dropped:0 overruns:0 frame:0
         TX packets: 96 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:7584(7.5KB)   TX bytes:7584(7.5KB)

---

### Post by halitech on 2011-12-29
okay, it is seeing the network card but not the wireless. 

still in the terminal, whats the output of
```
lspci
```
and 
```
lsusb
```

specifically anything related to network

---

### Post by JonBruce on 2011-12-29
after typing 'lspci', I found this:

06:02.0 Network controller: Broadcom Corp BCM4318 [AirForce One 54g]802.11g Wireless LAN controller
also see something a a modem controller if you need it..

Code: 'lsusb' returned three root hubs, 2.0, 1.1 and another 1.1

---

### Post by halitech on 2011-12-29
for the wireless, look here

[http://mikebeach.org/2011/05/09/bcm4318-airforce-one-54g-in-ubuntu-natty/](http://mikebeach.org/2011/05/09/bcm4318-airforce-one-54g-in-ubuntu-natty/)

you will need to get the wired connection working first though. I wonder if you are having the same problem I'm having with an HP where it seems to see the network card but won't get an ip. I put another nic in and it worked. 

Another question, do you have any kind of MAC filtering or encryption on the router?

---

### Post by thats no moon on 2011-12-29
had this problem on a BT5 machine once,
type 

```
rfkill list 
```

soft and hard block should read no for the wireless

---

### Post by JonBruce on 2011-12-29
thats no moon- you are correct, all readouts said 'no'

halitech- I don't think so. I've tried connecting wirelessly and by ethernet cable in three locations, where in all cases the computer reacted the same way.

And what's a nic?

---

### Post by thats no moon on 2011-12-29
network interface card

---

### Post by wildmanne39 on 2011-12-29
Hi, this will allow you to install the firmware needed for your driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal ctrl+alt+t and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run those commands one line at a time, now you should have a working wireless connection.
Thanks

---

### Post by JonBruce on 2011-12-30
> **wildmanne39 said:**
> Hi, this will allow you to install the firmware needed for your driver.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal ctrl+alt+t and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
Run those commands one line at a time, now you should have a working wireless connection.
Thanks

wildmanne39, thank you so much!! 
I appreciate everyone's time and help!!!

---

### Post by wildmanne39 on 2011-12-30
Hi, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by jdjames on 2012-02-29
Hello All,
Figured I would post on this thread, as it is pretty much the same situation as I'm having.  However, When I try to perform the steps for this solution, it doesn't work. I downloaded and extracted the b43 zip file with no problems.  I believe I am running into some problems when I try and run the terminal commands. For instance, when I run the first command this is the result:

jonathan@SolidSnake:~$ sudo mkdir .lib/firmware/b43
[sudo] password for jonathan: 
mkdir: cannot create directory `.lib/firmware/b43': No such file or directory

If anyone could respond, I would greatly appreciate it as I've been trying to fix this for the last 3 nights.  Im about at my wit's end.  I have a compaq V5000, and I'm running Ubuntu 11.10.  I do, however have a working Ethernet connection.

Thanks in advance!(hopefully)

---

### Post by jdjames on 2012-02-29
Also, here are my results to the previously requested terminal commands if this helps:
jonathan@SolidSnake:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:fe:54:be  
          inet addr:192.168.2.105  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fefe:54be/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10771121 (10.7 MB)  TX bytes:1799144 (1.7 MB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


jonathan@SolidSnake:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

jonathan@SolidSnake:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

jonathan@SolidSnake:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


I know that was alot, hope it helps?  Also, I've tried a few other fixes from different websites, so that may be interfering?

---

### Post by wildmanne39 on 2012-03-03
Hi, first the commands you typed are not correct, please copy and paste all commands for accuracy, also since you have a wired connection you can just run this command:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
unplug wired connection and it should work unless you have installed other drivers or there is something else going on that requires more troubleshooting, just so you know I am not available much at this time so I will be slow at responding.
Thanks

---

### Post by SylasL on 2012-03-03
i, too, am having trouble getting my wireless working. i tried the suggestions posted here, and i got an error message saying my wireless network was disconnected and then it went back to saying my firmware was missing. i've been trying to figure out what to do based on the guidance [here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers") but with no luck. i do not have a wired connection. this is making me feel rather stupid. please help, i am anxious to get this figured out! thanks in advance...

---

### Post by wildmanne39 on 2012-03-04
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
I may or may not be able to help you depending on what wireless card you have since you do not have a wired connection.
Thanks

---

