---
title: "[SOLVED] OpenDNS"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-29
I set this up the other day, but I'm having a problem where the IPs I entered in System > Admin > Network under the DNS tab keep changing back to the default ones.

Any ideas?

---

### Post by eightmillion on 2008-07-29
To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:
```
$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0
```

---

### Post by adobrakic on 2008-07-29
Yeah, I tried this, but when i try to do

```
sudo ifdown eth0 && sudo ifup eth0
```

I get some error

---

### Post by eightmillion on 2008-07-29
What's the error? It's possible that your network interface is named something else. Could you post the output of 'ifconfig'?

---

### Post by adobrakic on 2008-07-29
The error:
```

[sudo] password for ado: 
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
ado@ado-desktop:~$ 

```

ifconfig:
```

ado@ado-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:ca:35:db:df  
          inet addr:75.132.26.30  Bcast:255.255.255.255  Mask:255.255.192.0
          inet6 addr: fe80::240:caff:fe35:dbdf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4188441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:369242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1025545625 (978.0 MB)  TX bytes:36554258 (34.8 MB)
          Interrupt:16 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:957714 (935.2 KB)  TX bytes:957714 (935.2 KB)

ado@ado-desktop:~$ 

```

---

### Post by dentaku65 on 2008-07-30
My :) sticky for OpenDNS here:
[http://ubuntuforums.org/showthread.php?t=872500](http://ubuntuforums.org/showthread.php?t=872500)

---

