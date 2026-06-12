---
title: "Can't connect to internet &amp; large login font"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Dan Buckley on 2008-05-31
Hi I have just installed Ubuntu 8 as dual boot (windows XP) onto my Toshiba Notebook and have two problems.
1. When the Notebook is in Windows it connects to the internet seamlessly (network cable to Nwtcom 5NB adsl router - router is connected via USB to another PC.)  BUT when in Ubuntu it doesn't connect.  I have tried the various network actions but is doesn't seem to want to configure eth0.  I have tried the pings as suggesed in help  the ping to 82.211.81.158 gest no results from 5, but the pings to ubuntu.com comes through as 5 from 5.  I have done the suggested checking in Aplications>termonal ifconfig eth0  and it comes through with results for various adresses includin IP 192.168.30.2 (same address as under Windows) and Hwaddr 00:a0:45:c5:25  etc

I am at a loss on this (as a beginner) - could it be a firewall issue?

2.  The Ubuntu login dialog box has very large text - how can this be fixed.

---

### Post by iaculallad on 2008-05-31
> **Dan Buckley said:**
> Hi I have just installed Ubuntu 8 as dual boot (windows XP) onto my Toshiba Notebook and have two problems.
1. When the Notebook is in Windows it connects to the internet seamlessly (network cable to Nwtcom 5NB adsl router - router is connected via USB to another PC.)  BUT when in Ubuntu it doesn't connect.  I have tried the various network actions but is doesn't seem to want to configure eth0.  I have tried the pings as suggesed in help  the ping to 82.211.81.158 gest no results from 5, but the pings to ubuntu.com comes through as 5 from 5.  I have done the suggested checking in Aplications>termonal ifconfig eth0  and it comes through with results for various adresses includin IP 192.168.30.2 (same address as under Windows) and Hwaddr 00:a0:45:c5:25  etc
I am at a loss on this (as a beginner) - could it be a firewall issue?
.

Try Roaming Mode if it works for you.

Navigate through System->Administration->Network. On the "Connection" tab, 
select/click "Wired Connection" and click on "Properties". Click/Enable the checkbox for "Enable Roaming Mode" and click on OK. Restart network

On the terminal:

```
 sudo /etc/init.d/networking restart
```

---

### Post by Dan Buckley on 2008-05-31
Hi

thanks for the reply.  I set roaming mode and restarted metowrk as suggested.  No Luck and no change to pinging.  Any more suggestions?

---

### Post by ugm6hr on 2008-05-31
I'm confused as to what you are trying to do.

This is what I've understood:
1. Laptop
2. Ethernet cable connecting laptop to ADSL broadband modem-router
3. Works in Windows, not in Ubuntu 8.04

If this is not correct - please tell us.

I need more info - output from:
```
lspci
lshw -C network
ifconfig
route -n
```

Also - read this: [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425) (point 8)

---

### Post by Dan Buckley on 2008-05-31
Hi Thx  
I appreciate your help
text from Terminal (Ipconfig command did not work)

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) 
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02) 
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller 
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) 
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller 

 lshw -C network 
*-network                
       description: Ethernet interface 
       product: 82573L Gigabit Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 00 
       serial: 00:a0:d1:45:c5:25 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-5 ip=192.168.30.2 latency=0 module=e1000 multicast=yes 
  *-network 
       description: Network controller 
       product: PRO/Wireless 3945ABG Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       version: 02 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: driver=iwl3945 latency=0 module=iwl3945 

dan@dan-laptop:~$ ipconfig 
bash: ipconfig: command not found 


dan@dan-laptop:~$ route -n 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.30.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         192.168.30.1    0.0.0.0         UG    0      0        0 eth0 
dan@dan-laptop:~$

---

### Post by unutbu on 2008-05-31
Please post

```
ifconfig
cat /etc/network/interfaces
```

To change the actual size you perceive of as a 10pt font throughout your X session you can [change your DPI using these instructions]("http://ubuntuforums.org/showpost.php?p=3826654&postcount=14"). This  will alter the size of your fonts everywhere, not just the GDM login window. To just change the font sizes of the gdm login window itself, you can do the following (mind you, there might be a better way that I just don't know about -- this is a hack!)

```
gksu gedit /usr/share/gdm/themes/Human/Human.xml
```

Search for the word 'font' and change the font sizes to your liking.

---

### Post by james_vanb on 2008-05-31
To change the resolution of your login screen, you may have to edit /etc/X11/xorg.conf file.  Had similar problem a while ago.  As I remember, edited file as follows:

```
sudo gedit /etc/X11/xorg.conf
```

You should see a section that looks like this:

Section "Screen"

There should be a subsection called "Virtual".  If it is not set to the correct resolution, edit.  Or you may have a section called "Mode" that lists available resolutions.  As I recall, the first resolution listed will be used.  Edit appropriately.

---

### Post by Dan Buckley on 2008-05-31
TExt from Ifconfig request

dan@dan-laptop:~$ ifconfig cat /etc/network/interfaces 
Usage: 
  ifconfig [-a] [-v] [-s] <interface> [[<AF>] <address>] 
  [add <address>[/<prefixlen>]] 
  [del <address>[/<prefixlen>]] 
  [[-]broadcast [<address>]]  [[-]pointopoint [<address>]] 
  [netmask <address>]  [dstaddr <address>]  [tunnel <address>] 
  [outfill <NN>] [keepalive <NN>] 
  [hw <HW> <address>]  [metric <NN>]  [mtu <NN>] 
  [[-]trailers]  [[-]arp]  [[-]allmulti] 
  [multicast]  [[-]promisc] 
  [mem_start <NN>]  [io_addr <NN>]  [irq <NN>]  [media <type>] 
  [txqueuelen <NN>] 
  [[-]dynamic] 
  [up|down] ... 
 
  <HW>=Hardware Type. 
  List of possible hardware types: 
    loop (Local Loopback) slip (Serial Line IP) cslip (VJ Serial Line IP)  
    slip6 (6-bit Serial Line IP) cslip6 (VJ 6-bit Serial Line IP) adaptive (Adaptive Serial Line IP)  
    strip (Metricom Starmode IP) ash (Ash) ether (Ethernet)  
    tr (16/4 Mbps Token Ring) tr (16/4 Mbps Token Ring (New)) ax25 (AMPR AX.25)  
    netrom (AMPR NET/ROM) rose (AMPR ROSE) tunnel (IPIP Tunnel)  
    ppp (Point-to-Point Protocol) hdlc ((Cisco)-HDLC) lapb (LAPB)  
    arcnet (ARCnet) dlci (Frame Relay DLCI) frad (Frame Relay Access Device)  
    sit (IPv6-in-IPv4) fddi (Fiber Distributed Data Interface) hippi (HIPPI)  
    irda (IrLAP) ec (Econet) x25 (generic X.25)  
    eui64 (Generic EUI-64)  
  <AF>=Address family. Default: inet 
  List of possible address families: 
    unix (UNIX Domain) inet (DARPA Internet) inet6 (IPv6)  
    ax25 (AMPR AX.25) netrom (AMPR NET/ROM) rose (AMPR ROSE)  
    ipx (Novell IPX) ddp (Appletalk DDP) ec (Econet)  
    ash (Ash) x25 (CCITT X.25)

---

### Post by unutbu on 2008-05-31
Type 

```
ifconfig
```

and 

```
cat /etc/network/interfaces
``` 
as separate commands.

---

### Post by Dan Buckley on 2008-05-31
dan@dan-laptop:~$ ifconfig cat /etc/network/interfaces 
Usage: 
  ifconfig [-a] [-v] [-s] <interface> [[<AF>] <address>] 
  [add <address>[/<prefixlen>]] 
  [del <address>[/<prefixlen>]] 
  [[-]broadcast [<address>]]  [[-]pointopoint [<address>]] 
  [netmask <address>]  [dstaddr <address>]  [tunnel <address>] 
  [outfill <NN>] [keepalive <NN>] 
  [hw <HW> <address>]  [metric <NN>]  [mtu <NN>] 
  [[-]trailers]  [[-]arp]  [[-]allmulti] 
  [multicast]  [[-]promisc] 
  [mem_start <NN>]  [io_addr <NN>]  [irq <NN>]  [media <type>] 
  [txqueuelen <NN>] 
  [[-]dynamic] 
  [up|down] ... 
 
  <HW>=Hardware Type. 
  List of possible hardware types: 
    loop (Local Loopback) slip (Serial Line IP) cslip (VJ Serial Line IP)  
    slip6 (6-bit Serial Line IP) cslip6 (VJ 6-bit Serial Line IP) adaptive (Adaptive Serial Line IP)  
    strip (Metricom Starmode IP) ash (Ash) ether (Ethernet)  
    tr (16/4 Mbps Token Ring) tr (16/4 Mbps Token Ring (New)) ax25 (AMPR AX.25)  
    netrom (AMPR NET/ROM) rose (AMPR ROSE) tunnel (IPIP Tunnel)  
    ppp (Point-to-Point Protocol) hdlc ((Cisco)-HDLC) lapb (LAPB)  
    arcnet (ARCnet) dlci (Frame Relay DLCI) frad (Frame Relay Access Device)  
    sit (IPv6-in-IPv4) fddi (Fiber Distributed Data Interface) hippi (HIPPI)  
    irda (IrLAP) ec (Econet) x25 (generic X.25)  
    eui64 (Generic EUI-64)  
  <AF>=Address family. Default: inet 
  List of possible address families: 
    unix (UNIX Domain) inet (DARPA Internet) inet6 (IPv6)  
    ax25 (AMPR AX.25) netrom (AMPR NET/ROM) rose (AMPR ROSE)  
    ipx (Novell IPX) ddp (Appletalk DDP) ec (Econet)  
    ash (Ash) x25 (CCITT X.25)

---

### Post by Dan Buckley on 2008-05-31
Sorry pasted old Terminal text  correct one is:

dan@dan-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:45:c5:25   
          inet addr:192.168.30.2  Bcast:192.168.30.255  Mask:255.255.255.0 
          inet6 addr: fe80::2a0:d1ff:fe45:c525/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:100  
          RX bytes:38097 (37.2 KB)  TX bytes:172374 (168.3 KB) 
          Base address:0x2000 Memory:d6000000-d6020000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1485 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1485 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:74776 (73.0 KB)  TX bytes:74776 (73.0 KB) 
 
dan@dan-laptop:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback

---

### Post by unutbu on 2008-06-01
Sorry Dan, I'm not seeing anything wrong with your setup. Could you post the pings you tried and the output you're getting? It's getting late over here, but I'll take a look tomorrow.

---

### Post by ugm6hr on 2008-06-01
> **ugm6hr said:**
> Also - read this: [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425) (point 8 )

Did you read and check this - Windows power saving setting?  I am fairly sure this isn't the problem though - because of this:

```
dan@dan-laptop:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.30.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
0.0.0.0 192.168.30.1 0.0.0.0 UG 0 0 0 eth0 
```

This tells me your router (192.168.30.1) is connected, you have an IP (from ifconfig 192.168.30.2).

So - this must be a DNS resolution issue.

Post output from (3 separate commands):
```
ping 192.168.30.1
ping www.google.com
ping 64.233.183.104

```

---

### Post by Dan Buckley on 2008-06-01
Results of Pings - all seemed OK - I am beginning to think that it may be a Firefox setup issue of Firewall - any ideas?  I note that ping to 82.211.181.158 still gives zero results.

Bytes	Source	Seq	Time	Units 
64	192.168.30.1	1	7.74	ms 
64	192.168.30.1	2	0.816	ms 
64	192.168.30.1	3	1.17	ms 
64	192.168.30.1	4	1.64	ms 
64	192.168.30.1	5	0.907	ms 
Time minimum:	0.82 ms 
Time average:	3.34 ms 
Time maximum:	7.74 ms 
Packets transmitted:	5 
Packets received:	5 
Successful packets:	100% 


Bytes	Source	Seq	Time	Units 
64	64.233.167.99	1	247	ms 
64	64.233.167.99	2	266	ms 
64	64.233.167.99	3	268	ms 
64	64.233.167.99	4	270	ms 
64	64.233.167.99	5	271	ms 
Time minimum:	247.00 ms 
Time average:	261.50 ms 
Time maximum:	271.00 ms 
Packets transmitted:	5 
Packets received:	5 
Successful packets:	100% 

Bytes	Source	Seq	Time	Units 
64	64.233.183.104	1	341	ms 
64	64.233.183.104	2	344	ms 
64	64.233.183.104	3	344	ms 
64	64.233.183.104	4	345	ms 
64	64.233.183.104	5	343	ms 
Time minimum:	341.00 ms 
Time average:	343.00 ms 
Time maximum:	345.00 ms 
Packets transmitted:	5 
Packets received:	5 
Successful packets:	100%

---

### Post by Dan Buckley on 2008-06-01
Tried browsing for a few things  - can connect OK to mozilla.org but all others - get a "connection to server reset" message.

Does this give any clues?

---

### Post by Dan Buckley on 2008-06-01
I also tried Evolution email and could send out an email but not receive.

---

### Post by unutbu on 2008-06-01
I can't ping 82.211.181.158 either, and I have a working connection.
Some computers refuse to respond to pings, so don't worry about 82.211.181.158. What guide were you using that told you to ping that address?

Regarding firewalls: Ubuntu comes with iptables which implement firewall rules. By default, Ubuntu simply lets everything through. To check that your iptables is normal, run

```
sudo iptables -L
```

the result should be
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```
If your output from iptables is the same, you can rule out firewall as the problem.

I'm tempted to ask if your router might be implementing its own firewall, but then you'll probably say that everything works under Windows with the same router, so we have to rule out the router as the problem, huh?

I'm stumped...

---

### Post by Dan Buckley on 2008-06-02
Output from iptable - L is exactly as you suggested.

I have also tried the turning of of the power control box for the network controller.

If it is not firewall then I am also at a loss.

I can try a dual boot on another PC (w2000) which works fine and see if unbubtu works OK on that - or should I try Kunbutu or Xunbutu?

What do you think?

---

### Post by unutbu on 2008-06-02
It's a forum policy that you are not allowed to give up until we give up.

Okay, I give up. :)

Seriously now, I'm sorry I couldn't help you. I'm mystified why you can ping but can't surf. If you ever find out the reason, please post back.

It wouldn't hurt to try Kubuntu or Xubuntu. 
Kubuntu is a little heavier on the eye-candy (bloat?), but it uses Konquerer, so at least you could try a different web browser and see if it clears up your problem. Xubuntu I think uses Firefox by default, but you could always remove Firefox and install something else like Epiphany.

In fact, you could try installing Epiphany (or even Konquerer -- be prepared for a lot of dependencies) on your current ubuntu machine before sacking it...

```
% sudo apt-get install konqueror
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  kcontrol kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a kdesktop kfind
  kicker libarts1c2a libavahi-qt3-1 libdbus-qt-1-1c2 libkonq4 liblua50 liblualib50
Suggested packages:
  khelpcenter mtools fam kicker-applets menu konq-plugins ksvg gij-4.1 libgcj7-awt libjessie-java
Recommended packages:
  pmount kamera kdemultimedia-kio-plugins perl-suid libxine1-ffmpeg libarts1-mpeglib libarts1-akode
The following NEW packages will be installed:
  kcontrol kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data kdelibs4c2a kdesktop kfind
  kicker konqueror libarts1c2a libavahi-qt3-1 libdbus-qt-1-1c2 libkonq4 liblua50 liblualib50
0 upgraded, 16 newly installed, 0 to remove and 34 not upgraded.
Need to get **39.1MB of archives**.
After unpacking **112MB of additional disk space** will be used.
Do you want to continue [Y/n]? n
Abort.
% sudo apt-get  install epiphany
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  epiphany-data hermes1 libclan2c2a-sound libclanlib2c2a
The following NEW packages will be installed:
  epiphany epiphany-data hermes1 libclan2c2a-sound libclanlib2c2a
0 upgraded, 5 newly installed, 0 to remove and 34 not upgraded.
Need to get **1016kB** of archives.
After unpacking **3666kB of additional disk space** will be used.
Do you want to continue [Y/n]? n
Abort.



```

---

### Post by Dan Buckley on 2008-06-03
Before I start installing other browsers.

I have noticed that there a number of screen messages on shutdown of Ubuntu - there are a few ending in OK the the last is:
Running Local Boot Script

and then there a number of lines with about Network manager  the don't stay on screen long enough to read but the first one  says:
Network manager shutting down normally caught signal 15

there are about another 3 lines I think the last one is indicating a problem of some sort but cannot be sure.

Also 
When trying to configure Eth0 in the connection properties inside network manager a dialog box pops up and says:
"The interface does not exist"

I also tried the connect to network via terminal  the following resulted:

dan@dan-laptop:~$ sudo ifdown eth0 
[sudo] password for dan:  
There is already a pid file /var/run/dhclient.eth0.pid with pid 4472 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:a0:d1:45:c5:25 
Sending on   LPF/eth0/00:a0:d1:45:c5:25 
Sending on   Socket/fallback 
DHCPRELEASE on eth0 to 192.168.30.1 port 67 
dan@dan-laptop:~$ sudo ifup eth0 
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:a0:d1:45:c5:25 
Sending on   LPF/eth0/00:a0:d1:45:c5:25 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 
DHCPOFFER of 192.168.30.2 from 192.168.30.1 
DHCPREQUEST of 192.168.30.2 on eth0 to 255.255.255.255 port 67 
DHCPACK of 192.168.30.2 from 192.168.30.1 
bound to 192.168.30.2 -- renewal in 245674 seconds. 
dan@dan-laptop:~$ 


Does this help?

---

### Post by unutbu on 2008-06-03
> **Dan Buckley said:**
> 
Network manager shutting down normally caught signal 15


Yes, I get a similar message on my screen when I shutdown. Including an annoying spelling error -- "Terminiation". 

I don't recall seeing an error, but I'm not sure. Next time I shutdown I'll try to watch more carefully... 

> 
Also When trying to configure Eth0 in the connection properties inside network manager a dialog box pops up and says:
"The interface does not exist"

Immediately after receiving that pop up, run ifconfig. You should see eth0. If that's the case Network Manager is just not working properly.

> 
dan@dan-laptop:~$ sudo ifup eth0 
...
**bound to 192.168.30.2 -- renewal in 245674 seconds**. 
dan@dan-laptop:~$ 


This is proof that you have established a connection with your router. The bold line shows the router has DHCP running and has assigned you the ip address 192.168.30.2.

So there is no problem between you and the router. There is no firewall issue on your machine -- we've checked iptables. The only thing left, it seems to me, is to double check the router settings. 

Its hard to guide you here because each router is different, but I suggest you point your browser at  
192.168.30.1 and look at any firewall, port forwarding, or "custom services" configuration the router has. Note anything having to do with port 80 -- the port through which http traffic is received.

If that comes up empty, then short of your ISP doing something weird I am again stumped.

---

### Post by Dan Buckley on 2008-06-03
Hi

I tried to configure the eth0 interface and the same does not exist message popped up.  Then I did ifconfig and all seemed to be ok with eth0.  Hence from your suggestion the Network Manager is not working?

If so can that be reinstalled or do I have to uninstall and reinstall ubuntu?

---

### Post by unutbu on 2008-06-03
Network Manager is just a GUI to help users establish a network connection. It is not necessary that you use Network Manager. There is a [great guide on how to connect manually without Network Manager]("http://ubuntuforums.org/showthread.php?t=684495"), for instance. 

You already have a network connection -- that's demonstrated by your ability to ping. So you could just as easily forget about Network Manager. I don't know if re-installing it will fix its behavior -- it might just have a bug in its code. But if you want to try reinstalling, this is the command:
```

sudo apt-get install network-manager --reinstall
```

---

### Post by Dan Buckley on 2008-06-03
It is also very odd that appear to be able to browse the Mozilla.org web site (except for the store and cannot seem to download from mozilla).

Could there be some setting in Mozilla that is restricting access to all other sites?

---

### Post by Dan Buckley on 2008-06-03
When i Tried to traceroute to Mozilla.org it traced from 192.168.30.2 to 192.168.30.1 then has a string of no replies

---

### Post by unutbu on 2008-06-03
I get 
```
% traceroute Mozilla.org
traceroute to Mozilla.org (63.245.209.11), 30 hops max, 40 byte packets
 1  routerip (192.168.1.1)  3.805 ms  7.580 ms  9.785 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  moz.org01.nslb.sj.mozilla.com (63.245.209.11)  203.820 ms  210.891 ms  100.252 ms
```

So you are not alone. This might just be normal behavior. Like ping, some machines refuse to respond to the packets (pings?) traceroute sends.

You are not typically relying on Mozilla.org  when you visit another website. Mozilla.org is incapable of blocking your ability to view other sites. Your ISP on the other hand, could block sites, but if almost all sites are being blocked, there is more likely something else that is wrong.

Is there another computer available that can connect to your router to see if it has the same trouble surfing?

Oh -- when you said "is there a setting in Mozilla that is restricting access to all other sites" you meant Firefox, not Mozilla.org, didn't you? That's a good question. Go to Edit->Preferences. Click on the Advanced Tab, then the Network subtab, then the Connection Settings button. Does it say Direct connection to the internet? If not, try that.

---

### Post by Dan Buckley on 2008-06-03
Hi I took a photo of the text at close down:

after the text about caught termination signal the following shows:

NetworkManager <debug> [1212549965.864626] nm_print_open_socks () open sockets list:

NetworkManager <debug> [1212549965.864626] nm_print_open_socks () open sockets list:Done.

NetworkManager <info> deactivating device eth0

NetworkManager <WARN> nm_hal_deinit(): libhal shutdown failed connection is closed

NetworkManager <WARN> nm_dbus_init(): could not get the system bus. Make sure the message bus daemon is running.

NetworkManager:nm_dbus_signal_device_status_change: assertion 'dbdata->data->dbus_connection' failed 
NetworkManager:nm_dbus_signal_device_status_change: assertion 'dbdata->data->dbus_connection' failed 
NetworkManager:nm_dbus_signal_device_status_change: assertion 'dbdata->data->dbus_connection' failed 


 Can you make any sense of this?  Is it saying that the newtork manager could not shut down becasue the connection was already closed?

---

### Post by Dan Buckley on 2008-06-04
I used another PC linked to the same router/modem and setup up LIve CD version of Ubutu - guess what" same issues - can't browse.  So I think that narrows it down to an issue between Ubuntu and my network / router?  but what? and how to detect and fix I don't know.

---

### Post by Dan Buckley on 2008-06-04
reading some other threads - I saw that others with similar problems had success plugging in the USB connection to the router - guess what - it works.  AT the moment that is convenient  - but not for the future - so I still need to resolve the ethernet problem.  Which I now assume is associated between Ubunut  / eth0 and the Netcomm NB5 Router / adsl modem.  Does anyone know of any previous threads with resolutions to this issue?

---

