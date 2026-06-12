---
title: "Can not See Wireless PCM350"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by bcc21k on 2008-05-24
I can not see my wireless router. I have a IBM T22 laptop with an Aironet PCM352 card.  I downloaded the linux driver (linux-acu-driver-v21.tar.gz).  How do I install it?

---

### Post by bcc21k on 2008-05-24
I installed 8.04 with allthe patches.  Hereare somediagnostics:
sudo lshw -C network
[sudo] password for rcardone: 
  *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 0c
       serial: 00:03:47:93:70:5f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s


 ping -c4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.091 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.077 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.077 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.077 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.077/0.080/0.091/0.010 ms

 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:93:70:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4923 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5507676 (5.2 MB)  TX bytes:686011 (669.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2292 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2292 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:114872 (112.1 KB)  TX bytes:114872 (112.1 KB)

---

### Post by bcc21k on 2008-05-24
I found this thread that looks like a promising fix:
 Re: Wireless PCMCIA card won't work as eth1, but works MANUALLY as eth2
I have to confess that I went through similar frustrations installing my NetGear PCMCIA card on my (much older) ThinkPad. With > 10 years Debian behind me, I just KNEW that it had to be difficult, no? But it turned out that trying to do it yourself via iwconfig, etc, interferes with the foolproof Ubuntu/Gnome way of getting this done.

So, here's my advice:

1. Clean out /etc/network/interfaces by removing all lines for the eth1 and eth2 interfaces, also the map eth1 option for hotplug. Do you have the "network-manager" package installed (the one running nm-applet)? Then remove it as well.

2. Insert your card, then start System/Administration/Networking -- it should list an interface for your card under some name (may be eth1 or wlan0,...) and it should say not configured. I assume such an interface is present, otherwise you need a suitable kernel module...

3. Highlight that interface, select Properties, and then check the box to enable it. You can now configure the interface (you need to do this only once): select the essid ("retuelle"); type in the WEP key; select DHCP. Then OK, and activate the interface.

4. After it has activated, you can check that the necessary lines have been added to /etc/network/interfaces, no need to do this yourself.

5. If you shut down with the interface active, then it will automatically come up next time you boot with the card inserted. Should you elect to deactivate the interface before shutting down, then you'll have to activate it yourself after a reboot -- use System/Administration/Networking for that -- don't mess with ifup, iwconfig,...

Try it.

MY etc/network/interfaces contains the following:
auto lo
iface lo inet loopback

I do not know how to edit this file.

---

### Post by styphon on 2008-05-24
> **bcc21k said:**
> I found this thread that looks like a promising fix:
 Re: Wireless PCMCIA card won't work as eth1, but works MANUALLY as eth2
I have to confess that I went through similar frustrations installing my NetGear PCMCIA card on my (much older) ThinkPad. With > 10 years Debian behind me, I just KNEW that it had to be difficult, no? But it turned out that trying to do it yourself via iwconfig, etc, interferes with the foolproof Ubuntu/Gnome way of getting this done.

So, here's my advice:

1. Clean out /etc/network/interfaces by removing all lines for the eth1 and eth2 interfaces, also the map eth1 option for hotplug. Do you have the "network-manager" package installed (the one running nm-applet)? Then remove it as well.

2. Insert your card, then start System/Administration/Networking -- it should list an interface for your card under some name (may be eth1 or wlan0,...) and it should say not configured. I assume such an interface is present, otherwise you need a suitable kernel module...

3. Highlight that interface, select Properties, and then check the box to enable it. You can now configure the interface (you need to do this only once): select the essid ("retuelle"); type in the WEP key; select DHCP. Then OK, and activate the interface.

4. After it has activated, you can check that the necessary lines have been added to /etc/network/interfaces, no need to do this yourself.

5. If you shut down with the interface active, then it will automatically come up next time you boot with the card inserted. Should you elect to deactivate the interface before shutting down, then you'll have to activate it yourself after a reboot -- use System/Administration/Networking for that -- don't mess with ifup, iwconfig,...

Try it.

MY etc/network/interfaces contains the following:
auto lo
iface lo inet loopback

I do not know how to edit this file.

If you mean you cant save them because you need root permission use:
```
sudo gedit
```
Then open your file from within the editor and this will allow you to save the files back

---

