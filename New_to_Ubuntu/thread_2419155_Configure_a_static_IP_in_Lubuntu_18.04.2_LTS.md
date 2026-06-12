---
title: "Configure a static IP in Lubuntu 18.04.2 LTS"
date: 2019-05-17
forum: New to Ubuntu
---

### Post by sed_faster on 2019-05-17
Hello,

I am trying configure the static IP on this flavour of the Linux:
```

$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
$ uname -a
Linux  4.18.0-18-generic #19~18.04.1-Ubuntu SMP Fri Apr 5 10:22:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

I configured the system like this (sudo nano /etc/network/interfaces):
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
        address 192.168.1.70 
        netmask 255.255.255.0
       broadcast 192.168.1.255
        gateway 192.168.1.1
dns-nameservers 10.0.0.1 8.8.8.8

```
But this didn't works. Because the network cards didn't get a IP address. I goggled about this issue on internet and I only found article which advice me to change/setup the file interfaces. Also I use this commands to see more information about my networking:
```

$ ifconfig -a
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.55  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::cb5c:e160:e211:465b  prefixlen 64  scopeid 0x20<link>
        ether 2c:4d:54:4f:4f:9a  txqueuelen 1000  (Ethernet)
        RX packets 4796  bytes 5407544 (5.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3302  bytes 490699 (490.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 376  bytes 37179 (37.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 376  bytes 37179 (37.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 2c:4d:54:4f:4f:9a brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.55/24 brd 192.168.1.255 scope global dynamic noprefixroute enp3s0
       valid_lft 3344sec preferred_lft 3344sec
    inet6 fe80::cb5c:e160:e211:465b/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

What am I doing wrong?
Meanwhile, how can I reset the networking without reboot all system? I tried (sudo /etc/init.d/networking restart) but the feedback it is this message (sudo: /etc/init.d/networking: command not found).
Thanks

---

### Post by ajgreeny on 2019-05-17
See if this helps.
[https://help.ubuntu.com/community/NetworkConfigurationCommandLine](https://help.ubuntu.com/community/NetworkConfigurationCommandLine)

---

### Post by sed_faster on 2019-05-17
Hello,

I tried this sequence of commands:
```

$ ls /sys/class/net
enp3s0  lo

$ cat /etc/network/interfaces 
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto enp3s0
iface enp3s0 inet static
        address 192.168.1.71 
        netmask 255.255.255.0
    broadcast 192.168.1.255
        gateway 192.168.1.1
dns-nameservers 10.0.0.1 8.8.8.8

$ ifconfig
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.55  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::cb5c:e160:e211:465b  prefixlen 64  scopeid 0x20<link>
        ether 2c:4d:54:4f:4f:9a  txqueuelen 1000  (Ethernet)
        RX packets 2721  bytes 1915545 (1.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2581  bytes 379045 (379.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 1010  bytes 93628 (93.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1010  bytes 93628 (93.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

But If I reboot my system I lost my connection ethernet and the output of the command ifconfig it is this:
```

$ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 98  bytes 7816 (7.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 98  bytes 7816 (7.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```
Which value I should I choose to the parameters "broadcast" and "gateway" and "dns-nameservers"?

However I try restart the network card through this way but I can't:
```

$ sudo /etc/init.d/networking restart
sudo: /etc/init.d/networking: command not found

```

What am I doing wrong?
Thanks

---

### Post by sed_faster on 2019-05-17
Therefore I find a article about "how setup static IP on Ubuntu" but I didn't get good results through edit this file "sudo nano /etc/netplan/01-network-manager-all.yaml". Any idea about this issue?

---

### Post by oldfred on 2019-05-17
Most of my old routers let me configure a static IP as long as I did not use the DHCP range it had already allocated.
Most of the newer routers seem to allocate all addresses to DHCP, but then in the router you can set an address to not change for a device.
Check your router  & router manual.

---

### Post by Dennis N on 2019-05-17
In most routers, you can access the router configuration from a connected computer and 'reserve' an IP address on the LAN for each network device, which becomes the static IP address for that device. That's the easiest way. Did you check for that in your router?

---

