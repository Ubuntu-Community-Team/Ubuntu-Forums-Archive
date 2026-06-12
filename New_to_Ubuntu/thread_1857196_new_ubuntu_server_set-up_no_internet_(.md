---
title: "new ubuntu server set-up no internet :("
date: 2011-10-09
forum: New to Ubuntu
---

### Post by cris@smp.com.ph on 2011-10-09
Hello Ubuntu™,
newbie here

I setup an ubuntu™ server and configure the eth0 with the ip, subnet and gateway but
still i have no internet connection when i tried to ping an outside ip or host and try to update the server. Please help :( but the windows workstation that i have have no problem in the internet all in same wired network...

---

### Post by papibe on 2011-10-09
Hi cris. Welcome to the forums!

Could you post the result of these commands in both computers? 
```
$ ifconfig
```
Regards.

---

### Post by cris@smp.com.ph on 2011-10-09
My Ubuntu Server
-------------------------------------------------------------
root@mis-ubuntu:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:29:f2:b6:f4
          inet addr:192.168.0.212  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fef2:b6f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:699966 errors:0 dropped:61 overruns:0 frame:0
          TX packets:9987 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:55002105 (55.0 MB)  TX bytes:1333739 (1.3 MB)
          Interrupt:19 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8288 (8.2 KB)  TX bytes:8288 (8.2 KB)

root@mis-ubuntu:~#
----------------------------------------------------------
my windows configuration
C:\Users\Cris>ipconfig

Windows IP Configuration

Ethernet adapter Local Area connection:
            
             Connection-specific DNS Suffix:
             Link-Local IPv6 Address          : fe80:1d7b:cddd:4594%10
             IPv4 Address                         : 192.168.0.7
             Subnet Mask                         :  255.255.255.0
             Default gateway                   :192.168.0.3
-----------------------------------------------------------------

---

### Post by papibe on 2011-10-09
Thanks. It looks like your LAN IP and your netmask as OK:
```
inet addr:192.168.0.212 Bcast:192.168.0.255 Mask:255.255.255.0
```
Could you post the content of these command on the server?
```
$ sudo lshw -C network

$ lspci -nn | grep -i eth

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Please paste the results using # tags (available when you reply).

Regards.

---

### Post by cris@smp.com.ph on 2011-10-10
```
root@mis-ubuntu:/etc# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.3
```

---

### Post by cris@smp.com.ph on 2011-10-10
thank you for the reply papibe :)
but I solved the problem
the problem was the DNS
i just edit the [FONT=&quot]
/etc/network/interfaces
/etc/resolv.conf
```

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.212
        netmask 255.255.255.0
        gateway 192.168.0.3
        # dns-* options are implemented by the resolvconf package, if installed
        dns-namservers 192.168.0.2
        dns-search smp.local

```

```

search smp.local
nameserver 192.168.0.2

```



[/FONT][FONT=&quot] [/FONT]

---

### Post by papibe on 2011-10-10
Just a question:

You have your default route pointing to 192.168.0.3 (which I presume is your router), but your DNS server is 192.168.0.2 (is that a Home Server?).

Not that there's anything wrong with that, just a little unusual. Just double checking.

Regards.

---

### Post by cris@smp.com.ph on 2011-10-10
@papibe 
its in testing phase here in the company with i an isolated network, that's why its in ip zero series.

thanks for the reply..

regards

---

