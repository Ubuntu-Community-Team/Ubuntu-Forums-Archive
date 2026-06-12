---
title: "Network problem??"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by lightblue on 2008-05-23
I bought a new PC yesterday and install Ubuntu (Hardy)

my motherbaord is ECS G31-M 

i use onboard Vga, Sound and NIC (realtek 8111b)

during the live session i had network and internet but i did not use it.

after installation i configure network card to take static IP. The icon of the network was ok (indicating that the network connection was working fine) but the internet was unstable. I maen that there are time i have normal internet speed, other times very slow and some times NO internet. in the same session of surfing the web.

looking to find out if there is any compatibility problem with my NIC i read somewhere to upgrade network manager 0.6 that i have to 0.7 from

```

# deb http://ppa.launchpad.net/asac/ubuntu hardy main
# deb-src http://ppa.launchpad.net/asac/ubuntu hardy main

``` 


after that(the update) the icon is show with a ! and when i put cursor on it it say's that there is no network connection BUT i have internet normally (as the network connection have no problem at all)


anyone have any idea why this is happening and any suggestion what to do?

i know that since i have network there is no major problem but i do not like to have an icon saying "no network connection"

---

### Post by hyper_ch on 2008-05-23
plz post the output of:
```

ifconfig

```
```

iwconfig

```
```

cat /etc/network/interfaces

```
```

cat /etc/resolv.conf

```
```

ping ROUTERIP

```
of course replace "ROUTERIP" with the actual ip of your router.

---

### Post by lightblue on 2008-05-23
```

nikos@statheros:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:90:76:30:32  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fe76:3032/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2227954 (2.1 MB)  TX bytes:420218 (410.3 KB)
          Interrupt:222 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1702 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86780 (84.7 KB)  TX bytes:86780 (84.7 KB)


```

```

nikos@statheros:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

```

nikos@statheros:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback





iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0


```

```

nikos@statheros:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4959
#
### END INFO



nameserver 192.168.1.1




```

```

nikos@statheros:~$ ping -c 5 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=56.0 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=2.65 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=17.2 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=14.0 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=254 time=1.96 ms

--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4001ms
rtt min/avg/max/mdev = 1.964/18.381/56.013/19.764 ms


```

---

### Post by Bodsda on 2008-05-23
Strangely enough there is nothing wrong with any of that code. are you using KDE or Gnome? i had a similar issue with kubuntu, never found a solution (alhough i didnt try very hard)

---

### Post by hyper_ch on 2008-05-23
The network settings look all fine to me...

If it's just "random" delay you might want to turn of IPv6 (search the forums here, there's howtos for that)

---

### Post by lightblue on 2008-05-23
i run gnome

i will try to turn of ipv6 

thanks all for help-information

---

