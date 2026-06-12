---
title: "Destination Host Unreachable"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by bebox on 2008-05-01
hi....i installed hardy and my lan isnt working anymore...please help me..Destination Host Unreachable

---

### Post by superprash2003 on 2008-05-01
can you post your ifconfig results here..

---

### Post by brigux on 2008-05-01
and the result of "netstat -ra" as well.

---

### Post by bebox on 2008-05-02
> **superprash2003 said:**
> can you post your ifconfig results here..

eth0 Link encap:Ethernet HWaddr 00:13:8f:89:7a:fd
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:27 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:250 Base address:0xe000

eth1 Link encap:Ethernet HWaddr 00:0a:5e:3f:44:d8
inet addr:40.30.5.62 Bcast:40.30.5.255 Mask:255.255.255.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18 Base address:0xc00

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1222 errors:0 dropped:0 overruns:0 frame:0
TX packets:1222 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:65016 (63.4 KB) TX bytes:65016 (63.4 KB)

---

### Post by bebox on 2008-05-02
> **brigux said:**
> and the result of "netstat -ra" as well.

sorry a cant acces my computer right now because i am in germany and i am from croatia...but when i come home i will post...:)

---

### Post by dokdoom on 2008-05-02
Run

dhclient eth0

to grab a dhcp address. If you want to do this automatically everytime you boot up you need to edit your /etc/network/interfaces

Add this into that file.

auto eth0
iface eth0 inet dhcp

After you save this file you can then run

sudo /etc/init.d/networking restart to once again obtain a dhcp address.

***If neither of these methods work that means you need to look at your routing device.***

---

### Post by superprash2003 on 2008-05-02
are you using eth0 or eth1 to connect? cause eth1 seems to be getting an ip 40.x.x.x

---

### Post by bebox on 2008-05-03
> **dokdoom said:**
> Run

dhclient eth0
***

i use static ip address...
my computers ip is 40.30.5.62 and i have a home lan and when i try to ping other computers in my house its not working...i didnt change anything just installed hardy (before i had gutsy and with the same settings it was working..).

i have two lan cards in my computer and i am using only one...and i think it sholud be eth0

---

### Post by bebox on 2008-05-03
> **superprash2003 said:**
> are you using eth0 or eth1 to connect? cause eth1 seems to be getting an ip 40.x.x.x

i use static ip address...
i dont know witch one a am using...i tried both and still it isnt working..

---

