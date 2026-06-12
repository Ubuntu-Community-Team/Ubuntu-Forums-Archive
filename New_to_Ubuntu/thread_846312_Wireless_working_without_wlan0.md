---
title: "Wireless working without wlan0"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2008-07-01
Hi all

I'm currently connected to the net with my wireless adapter. But when I issue ifconfig, it looks like i'm using eth0 instead of wlan0.

For now I'm happy with my connection, but does this feel right? shouldn't wireless adapter be wlan0 instead of eth0? And i haven't tried wired connection yet. Do you guys think this will cause me troubles if I decided to work wired?

these are some outputs that I think will be helpful for you to help me

Thanks in advance

```

yousef@YousefLaptop:~$ lspci | grep -i network
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
yousef@YousefLaptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 00
       serial: 00:16:41:e7:85:d5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.5-1 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:d2:b2:36:30
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.103 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g
yousef@YousefLaptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:D2:B2:36:30  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:feb2:3630/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2858 errors:1 dropped:711 overruns:0 frame:0
          TX packets:2002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3013616 (2.8 MB)  TX bytes:294067 (287.1 KB)
          Interrupt:21 Base address:0xc000 Memory:edf00000-edf00fff 

eth1      Link encap:Ethernet  HWaddr 00:16:41:E7:85:D5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x2000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

yousef@YousefLaptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

irda0     no wireless extensions.

eth0      IEEE 802.11g  ESSID:"DardeerHome"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:39:AB:EE:8C   
          Bit Rate:54 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=79/100  Signal level=-55 dBm  Noise level=-56 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:710   Missed beacon:0

yousef@YousefLaptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

yousef@YousefLaptop:~$ 



```

---

### Post by sdennie on 2008-07-01
I don't think this is an issue.  It's not normal for an intel wireless card to be labeled eth0 and the wired connection to be eth1 but, it shouldn't be a problem either.  I suspect it's probably because you are using the older ipw3945 driver and not the newer iwl3945 driver.  Another thing you could check is the udev rules for your network cards.  Have a look in /etc/udev/rules.d/70-persistent-net.rules.  You can probably rename your devices from there but, you will likely have to reboot before you see the changes reflected.

---

### Post by Abu_Dayya on 2008-07-01
Well, as long as its working.... I don't realy mind the naming of the card. I was just curious. Thanks

---

