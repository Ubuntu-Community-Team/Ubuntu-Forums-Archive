---
title: "can't connect to net via ethernet + modem (Ubuntu 8.04)"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by peterballard on 2014-01-01
Hi all, yet another "can't connect to the net" thread...

I've got a D-link modem, and one Linux PC (also running Ubuntu 8.04) connects via ethernet to the modem (and on to the internet), no problem. I am trying to get a 2nd Linux PC to connect via a 2nd ethernet port on the modem. I know the connectivity is right because it's a dual boot with Windows and it connects fine in Windows.

I'm using Ubuntu 8.04 which I installed a few years ago and then stopped using. Yes I know 8.04 is old. My intention is to upgrade once I can connect.

My 2nd PC cannot see the modem, i.e. "ping 192.168.1.1" gets no response.

Try #1: I ran "sudo pppoeconf" and got the following response (the "1 interface" is eth0):
```

Sorry, I scanned 1 interface, but the Access
Concentrator of your provider did not respond. Please
check your network and modem cables. Another reason
for the scan failure may also be another running pppoe
process which controls the modem.

```

Try #2, I tried Enabling "Onboard LAN Boot ROM" in the BIOS as in this thread (post #22): [http://ubuntuforums.org/showthread.php?t=901051&page=3](http://ubuntuforums.org/showthread.php?t=901051&page=3) No help so I changed it back to the BIOS default (Disabled).

Below are the outputs of a few commands I often see suggested:
```

pb@sirboris:~$ ping google.com

pb@sirboris:~$ ping 192.168.1.1
connect: Network is unreachable

pb@sirboris:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0

pb@sirboris:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:83:28:16  
          inet addr:192.168.0.156  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe83:2816/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:4759 (4.6 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1891 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94736 (92.5 KB)  TX bytes:94736 (92.5 KB)

pb@sirboris:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
02:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem

pb@sirboris:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:83:28:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.2.0 firmware=1.1-2 ip=192.168.0.156 latency=0 module=e1000e multicast=yes

```

Over to you folks. Any suggestions? Thanks in advance.

---

### Post by peterballard on 2014-01-01
OK it looks like I've solved it. The problem is it was set up for a Static IP Address. Here's how I fixed it:

In the graphical interface, at the very top of the screen, are the 3 words "Applications Places System".
I clicked System -> Administration -> Network
Clicked "Unlock"
Typed in my password (didn't need to be root) and clicked "Authenticate"
Selected "Connections" tab.
Selected "Wired connection" (i.e. the ethernet interface "eth0")
Clicked "Properties"
Under "Configuration" line, I changed the selection from "Static IP Address" to "Automatic configuration (DHCP)"
clicked "OK"

And now it connects to the net!

I've no idea why it was set up for Static IP Address. Anyway, if anyone else has the same problem as me, check for that :)

---

### Post by holycow131415 on 2014-01-02
Not sure why you need to connect to the internet first to upgrade. I dont think you can directly upgrade from 8.04 anymore to the current ubuntu without doing a clean install from a dvd disk.

---

