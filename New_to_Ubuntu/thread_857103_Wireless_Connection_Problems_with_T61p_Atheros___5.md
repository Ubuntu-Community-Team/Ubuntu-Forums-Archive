---
title: "Wireless Connection Problems with T61p Atheros   5418"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Horatius Andalus on 2008-07-12
Hey,

I just got my laptop, a T61p, and have used Ubuntu previously on a desktop; when I put Hardy Heron on the T61p, the computer does not show any signs of detecting a wireless device (which should be automatically built into the laptop).

typing the command lshw -C network

tmtill@tmtill-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:d6:aa:07
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 ip=192.168.0.20 latency=0 module=e1000 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: AR5418 802.11abgn Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

any suggestions about how to make the thing work? all help is appreciated, oh, and I'm very new at the more technical aspects of all this, so detailed explanations would be appreciated.  Thanks!

---

### Post by Dutch70 on 2008-07-12
try typing "sudo" before the rest of the command

---

### Post by lisati on 2008-07-12
Does any wifi network show up when you type:```
ifconfig
``` or ```
iwconfig
```????

---

### Post by Horatius Andalus on 2008-07-12
ifconfig shows:

tmtill@tmtill-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:d6:aa:07  
          inet addr:192.168.0.20  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:37ff:fed6:aa07/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:114359 (111.6 KB)  TX bytes:42435 (41.4 KB)
          Base address:0x1840 Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93900 (91.6 KB)  TX bytes:93900 (91.6 KB)



and iwconfig shows:

tmtill@tmtill-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



it looks to me as though the computer just can't figure out that there's a wireless interface too...

also, how do you type in the "code" windows on these forums?

thanks guys for trying to help

---

### Post by Horatius Andalus on 2008-07-12
also, typing sudo in front of the first command I showed does nothing different

---

### Post by TSS on 2008-07-12
This might help you: [http://ubuntuforums.org/showthread.php?t=785040](http://ubuntuforums.org/showthread.php?t=785040)

---

### Post by Horatius Andalus on 2008-07-12
TSS, I had actually tried that before posting this thread, but when I reached step four, (make, make install) the terminal said that there were no such commands, what am I doing wrong?

the only command I put in on those steps where what is stated in the guide, nothing more, nothing less, that is to say, I was essentially copy-pasting the commands into my terminal

---

