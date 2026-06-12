---
title: "Broken internet"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by BackBack on 2008-10-16
I've just installed Ubuntu Gutsy 7.1 and I can't get the computer to connect to the internet, not even with the Live CD; however, the Windows partition connects just fine.  I've tried using the sudo ifconfig eth0 up command as I've been told to, but that didn't help.  Is there another solution I could try?

---

### Post by Ryadt on 2008-10-16
How are you trying to connect?

---

### Post by BackBack on 2008-10-16
> **Ryadt said:**
> How are you trying to connect?

Via ethernet cable

---

### Post by FreewheelinFrank on 2008-10-16
Do you have DHCP enabled on your router?

If the router is expecting the computer to have a static IP address, you may have to tell Ubuntu this, or ask the router to assign an address to Ubuntu.

It depends how you set the router up.

---

### Post by BackBack on 2008-10-16
> **FreewheelinFrank said:**
> Do you have DHCP enabled on your router?

If the router is expecting the computer to have a static IP address, you may have to tell Ubuntu this, or ask the router to assign an address to Ubuntu.

It depends how you set the router up.No, I'm fairly sure that's not the case, which is why the problem, lol

---

### Post by handydan918 on 2008-10-16
> **BackBack said:**
> No, I'm fairly sure that's not the case, which is why the problem, lol

Maybe you could just post the output of ```
sudo dhclient
``` and eliminate the doubt.

---

### Post by FreewheelinFrank on 2008-10-16
If the router expects a static address, you'll have to enter the details in Network Manager.

---

### Post by BackBack on 2008-10-24
On sudo dhclient I get> There is already a pid file /var/run/dhclient.pid with pid 10642
Killed old client process, removed PID file
Internet Systems Consortium HDCP Client v.3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All right reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0c:29:2d:e1:2e
Sending on LPF/eth0/00:0c:29:2d:e1:2e
Sending on Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 5.0.0.1
bound to 5.62.53.22 -- renewal in 118 seconds.
Sorry about the late reply, but I just got back to my computer.  Anyway, no internet even off the LiveCD, so I have no idea what to do

---

### Post by BackBack on 2008-10-24
Oh, I should add that it's both with 7.1 and 8.04 that I've had this problem now

---

### Post by mikewhatever on 2008-10-25
Can you also post the output of ifconfig command. If you are connected through a router (haven't been confirmed yet), verify you can ping it.

---

### Post by BackBack on 2008-10-25
Here's what I get on ifconfig
> 
eth0 
Link encap:Ethernet HWaddr 00:0c:29:2d:e1:2e
inet addr:5.62.53.22 Bcast:5.255.255.255 Mask:255.0.0.0
inet6 addr: fe80::20c:29ff:fe2d:e12e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX Packets:2 errors:0 dropped:0 overruns:0 frame:0
TX Packets:46 errors:0 dropped:0 overruns:0 carried:0
collisions:0 txqueuelen:1000
RX bytes:608 (608 b) TX bytes:5779 (5.6 KB)
Interrupt:16 Base address:0x2000

lo
Link encap:Local Loopback
inet addr:127.0.0  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:182 errors:0 dropped:0 overruns:0 frame:0
TX Packets:182 errors:0 dropped:0 overruns:0 carried:0
collisions:0 txqueuelen:1000
RX bytes:15704 (15.3 KB) TX bytes:15704 (15.3 KB)
Interrupt:16 Base address:0x2000

---

### Post by ibuclaw on 2008-10-25
Since it seems like you are using this thread now, I'll give you a quick run through on what to test.

**First** test to see if Linux has picked up the Ethernet card and it functions fine... ping yourself
```
ping -c4 127.0.0.1
```
If this fails, then your card, for whatever reason, has not been setup properly, or the drivers to control the card aren't present in the 2.6.24 kernel.
If it works, move onto the second test.

**Second** test to see if you have ping your router.
This will depend on your router, some use 192.168.0.1 ... others use 192.168.1.1
```
ping -c4 192.168.1.1
```
If this fails, then you probably have a faulty RJ45 cable, or you haven't connected the cable in properly ;).
If it works, move onto the third test.

**Third** test to see if you can call the outside world.
```
ping -c4 91.189.94.12
```
If this fails, then your ethernet settings aren't configured properly with the router. If all seems fine, then you might need to check your router settings. Check that it isn't MAC filtering (blocking your ethernet card's MAC address).

If it works, I'm not too sure what to suggest....

[EDIT]
A successful test will look like this:
> 
--- 91.189.94.12 ping statistics ---
**4 packets transmitted, 4 received, 0% packet loss,** time 2998ms
rtt min/avg/max/mdev = 25.236/25.667/25.896/0.265 ms

You are looking for **0% packet loss**.

Other than that, give us a bell when you've tried that.

Regards
Iain

---

### Post by BackBack on 2008-10-25
It seems like the second test fails but I know I have a good cable and it's plugged in properly.  I'm currently on Vista and it connects just fine, but Ubuntu on VMware (I do this so I dont have to switch partitions constantlu) does does not.

---

### Post by mikewhatever on 2008-10-25
> **BackBack said:**
> It seems like the second test fails but I know I have a good cable and it's plugged in properly.  I'm currently on Vista and it connects just fine, but Ubuntu on VMware (I do this so I dont have to switch partitions constantlu) does does not.

Well, good to know it's a vmware install, should have told that in post #1. Apparently, ifconfig shows you get an IP, so it's likely a vmware problem.

---

### Post by BackBack on 2008-10-25
No it's not a VMWare problem because I've actually run the LiveCD, and I've tried installing Ubuntu on a second partition and booting that, still no go.  I was just tried of having to swap between the two partitions to relay data because I couldn't connect to the internet on the one that I needed

---

### Post by Shazaam on 2008-10-25
BackBack...
Go to the Windows folder where your Ubuntu virtual machine is, right-click the .vmx file and open it with a text editor. Scroll down to the ethernet entry and change "Bridged" to "NAT"...
```
ethernet0.connectionType = "nat"
```
Then go to Windows ControlPanel>Network Connections and see if there are any icons for vmnet. Configure that/those connection(s) for nat networking and DHCP. Open any Windows firewall programs and configure it/them to allow VMware access to the internet (not as a server).

---

### Post by BackBack on 2008-10-26
I did that and it's no go.  The problem isn't that I can't connect while using it in VMWare, even if Ubuntu is the only operating system on the entire computer and I boot it, still no internet.  You can ignore everything about VMWare, that doesn't matter, what I'm getting at is that Ubuntu itself refused to connect.

---

