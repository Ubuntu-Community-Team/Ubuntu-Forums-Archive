---
title: "Broadcom 4306 wireless problem--how enable my card"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by litboy21 on 2008-05-19
Ubuntu Hardy
I installed Hardy yesterday and I cannot get wireless to work. I am running a Dell Inspiron 5150, Pentium 4 3.06Ghz, 1GB RAM. 
I have installed the windows driver for my wireless card, but it is not enabled. How do you enable the wireless card?

thanks!

---

### Post by mmb1 on 2008-05-19
I'm not sure if this will help, (I'm a wireless infant) but here ya go:

[http://ubuntuforums.org/showthread.php?t=773774](http://ubuntuforums.org/showthread.php?t=773774)

---

### Post by spiderbatdad on 2008-05-19
[https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

---

### Post by litboy21 on 2008-05-19
> **spiderbatdad said:**
> [https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)

I tried that. I have the driver listed in Windows Drivers, but I am unable to see any wireless. I ran a terminal command and the results said that my network card is enabled, but my wireless card is disabled.
How do you enable a wireless card when it is there and has the drivers?

Thanks.

---

### Post by litboy21 on 2008-05-19
Here is the response I received from the terminal command:
 *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:38:a1:7c
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.101 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:62:7b:01
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by drs305 on 2008-05-19
Here's a very good hardy howto:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by spiderbatdad on 2008-05-19
check your network monitior applet for a wireless access point. Left click on the applet in your panel should show you available networks. Try rebooting but first make sure ndiswrapper is listed in /etc/modules: run: ```
gksu gedit /etc/modules
``` add the word ndiswrapper on a line by itself above or below any other modules listed. Save the file and reboot. If you don't have a network monitor applet or no wireless interface up after reboot, please post back with result of ```
iwconfig
```

---

### Post by spiderbatdad on 2008-05-19
> **drs305 said:**
> Here's a very good hardy howto:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

+1

---

### Post by litboy21 on 2008-05-19
> **drs305 said:**
> Here's a very good hardy howto:
[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

The first set of instructions done, but the response was that the driver was already installed.

---

### Post by drs305 on 2008-05-19
> **litboy21 said:**
> The first set of instructions done, but the response was that the driver was already installed.

If you mean you have completed step 1, continue doing everything in his post until you get to the end. Just having a driver doesn't necessarily mean everything is set up correctly ;-)

---

### Post by litboy21 on 2008-05-19
> **spiderbatdad said:**
> check your network monitior applet for a wireless access point. Left click on the applet in your panel should show you available networks. Try rebooting but first make sure ndiswrapper is listed in /etc/modules: run: ```
gksu gedit /etc/modules
``` add the word ndiswrapper on a line by itself above or below any other modules listed. Save the file and reboot. If you don't have a network monitor applet or no wireless interface up after reboot, please post back with result of ```
iwconfig
```

OK. Now I don't have my network at all.
I have repeated steps from the other posts in here (to the best of my ability). I did follow all steps.
The result of the iwconfig:
lo no wireless extensions
wlan finds my card (lots of info about card--is there something specific I am looking for?)
eth0 no wireless extensions

So, now I have no Internet access on my machine (thankful for backup laptop).

So, now what?

---

### Post by spiderbatdad on 2008-05-19
eth0 is your wired connection. it should not have been affected by installing ndiswrapper and the windows driver. Try running:```
sudo ifdown eth0
sudo ifup eth0
```then run ifconfig to see the status of your connections.

---

### Post by litboy21 on 2008-05-19
> **spiderbatdad said:**
> eth0 is your wired connection. it should not have been affected by installing ndiswrapper and the windows driver. Try running:```
sudo ifdown eth0
sudo ifup eth0
```then run ifconfig to see the status of your connections.

Before I posted, I had installed ndiswrapper and the driver. I was simply unable to enable my wireless card. However, I followed all of the instructions in the posts to the best of my knowledge. I guess I messed something up.

I ran both commands you posted. But I am not able to access anything.
The results of the iconfig are long and complicated (to my eyes). What am I looking for?
It seems that all are up and running, but I have no access.

thanks for the help. I am about ready to reinstall the OS and start over (again).
grrr

---

### Post by spiderbatdad on 2008-05-19
Hopefully you don't get that frustrated. I just wrote a long response, only to have my browser crash when I tried to upload an attachment.

Do you have the network monitor in the upper right corner, in the notification area?

ifconfig should show you tx & rx packets with no errors on eth0 if plugged in.

---

### Post by litboy21 on 2008-05-19
I do have the monitor in the right hand corner.
It did not list any errors (that I can tell).

---

### Post by spiderbatdad on 2008-05-19
so right click on the monitor and make sure eneble networking is checked...also edit network settings...make sure roaming is enabled in the network properties.

---

### Post by litboy21 on 2008-05-19
did that several times. restarted my router. Restarted machine 3x. Prayed to non-denominational and unoffensive gods multiple times. created new and interesting combinations of profane words directed at networking cards more times than I care to admit.
reinstalling OS as I type so that I will at least have hardwire connection again and a tabula rasa from which to work...

---

### Post by spiderbatdad on 2008-05-19
:)

---

### Post by litboy21 on 2008-05-19
OS reinstalled. Windows drivers installed. Still no wireless.

---

### Post by litboy21 on 2008-05-20
iwconfig
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

---

