---
title: "usb tethering weird issue"
date: 2019-06-16
forum: New to Ubuntu
---

### Post by ubulepetitroi on 2019-06-16
Hi,
To start off, I must say I am... mostly lost in Ubuntu. So I'm sorry in advance if I forgot to give some obvious infos that are supposed to help solve my issue.

I have now been trying for two months to solve an USB tethering issue from my phone to my computer. I'm running ubuntu 19.04 and my phone is a galaxy S10e.
The fact is that the tethering connection seems to be working, in a way... for example, I still can surf on this website. but the rest of the internet, as well as all my apps, keep loading forever.
I really don't get it.
So I tried a bunch of threads, hoping that would help... none could do.

here are the infos I think that might help you:

first I checked **lsusb:**
```
Bus 002 Device 004: ID 0a5c:21d7 Broadcom Corp. BCM43142 Bluetooth 4.0
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:648b Microdia Integrated Webcam
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 015: ID 04e8:6863 Samsung Electronics Co., Ltd Galaxy series, misc. (tethering mode)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

then I looked into **ifconfig -a,** to find my device:
```
enp0s20u3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.42.220  netmask 255.255.255.0  broadcast 192.168.42.255
        inet6 fe80::8e7c:6f25:b5b9:bf3  prefixlen 64  scopeid 0x20<link>
        ether 4e:49:db:c6:ed:6b  txqueuelen 1000  (Ethernet)
        RX packets 1879  bytes 617606 (617.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1981  bytes 423463 (423.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp2s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 5c:f9:dd:60:80:09  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 262975  bytes 16634880 (16.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 262975  bytes 16634880 (16.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp1s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 9c:2a:70:cc:a0:4b  txqueuelen 1000  (Ethernet)
        RX packets 978685  bytes 444227592 (444.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 76460
        TX packets 349420  bytes 62111526 (62.1 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  
```

I believe my device is called enp0s20u3 then.

I tried also to use **macchanger**, as I saw that solved the issue for people that couldn't make it work:

```
sudo macchanger -b -a enp0s20u3
[WARNING] Ignoring --bia option that can only be used with --random
Current MAC:   4e:49:db:c6:ed:6b (unknown)
Permanent MAC: 00:00:00:00:00:00 (XEROX CORPORATION)
[ERROR] Could not change MAC: interface up or insufficient permissions: Device or resource busy
```

At this point I tried this:
```

 service network-manager stop; sleep 5 
ifconfig enp0s20u3 down
SIOCSIFFLAGS: Operation not permitted
ifconfig enp0s20u3 up; sleep 5
SIOCSIFFLAGS: Operation not permitted
service network-manager start
```

As you can see it didn't work as intended.

Finally I tried a command I saw In a thread about this error message "SIOCSIFFLAGS: Operation not permitted":

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Wireless interface
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: 9c:2a:70:cc:a0:4b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:d0500000-d0507fff
  *-network
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 10
       serial: 5c:f9:dd:60:80:09
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:d0400000-d043ffff ioport:2000(size=128)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp0s20u3
       serial: 4e:49:db:c6:ed:6b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.220 link=yes multicast=yes
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```


and then... stuck. I don't get the information that the last command is supposed to give me. To be fair, I don't get most of the things I did anyway :>

Any help would be welcome at this point. If you need any other infos, I'd be glad to answer.

Thank you for reading!
ubu

---

### Post by CatKiller on 2019-06-17
I've never tried tethering a phone using anything but WiFi, so I can't help you with that part.

However, Linux is designed to be multiuser; the permissions system defines which user can access which files, and which user can run which applications.

Things like starting and stopping services, and interrogating hardware directly, are not things that a user can do, generally. Your output calls that out specifically

```
WARNING: you should run this program as super-user.
```

and obliquely

```
Operation not permitted
```

You can, however, if your user is authorised to do so, run commands as if you were a different user. Most usefully, that allows you to temporarily acquire the permissions that the *root* user has. That's what the **sudo** (switch user, do) command does, that you *have* used earlier.

Sudo with a user name runs the following command as that user. Sudo without a user name runs the following command as root.

You should use it with caution. It is much easier to break your system with root permissions than without, and there are some pitfalls over ownership with anything that makes changes to your Home folder.

---

### Post by ubulepetitroi on 2019-06-18
I'll keep that in mind, thanks a lot :) I'll try with sudo though: there's no point for me to have a working system on this computer if I can't connect to internet

---

