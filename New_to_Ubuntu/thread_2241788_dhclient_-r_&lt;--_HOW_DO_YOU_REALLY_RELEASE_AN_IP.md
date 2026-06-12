---
title: "dhclient -r &lt;-- HOW DO YOU REALLY RELEASE AN IP ADDRESS?"
date: 2014-08-28
forum: New to Ubuntu
---

### Post by cwmoser on 2014-08-28
How do you really release an IP address?
I was putting together some basic command line networking tools
similar to what I use with Windows and could not find a *workable*
command that would release a dynamic IP address.

These do not work:
sudo dhclient -r 
sudo ifdown eth0

After I issue those commands, I can still ping.
I am using dynamic IP addressing on my PC.

Thanks for any insights in this.

---

### Post by cwmoser on 2014-08-28
When I issue **sudo dhclient -r **or **sudo ifdown eth0**, I can still ping other hosts, browse the Internet, etc.

---

### Post by The Cog on 2014-08-28
Can you post the output of the command **ifconfig** both before and after the **sudo dhclient -r** and **sudo ifdown eth0** commands.

---

### Post by cwmoser on 2014-08-28
Here is the output:
```

carl@klaatu-2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:ad:c8:6d  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fead:c86d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:620328 errors:0 dropped:25 overruns:0 frame:0
          TX packets:373128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:693990892 (693.9 MB)  TX bytes:47516259 (47.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:41445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4398682 (4.3 MB)  TX bytes:4398682 (4.3 MB)


carl@klaatu-2:~$ 

carl@klaatu-2:~$ sudo dhclient -r

carl@klaatu-2:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:ad:c8:6d  
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fead:c86d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:620498 errors:0 dropped:25 overruns:0 frame:0
          TX packets:373249 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:694069320 (694.0 MB)  TX bytes:47525433 (47.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:41455 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4399562 (4.3 MB)  TX bytes:4399562 (4.3 MB)


carl@klaatu-2:~$
```

---

### Post by The Cog on 2014-08-28
OK, mabe just releasing the IP address doesn't remove the address from the interface - I don't know about that. But I would expect that sudo ifdown eth0 would knock the interface down and lose your connectivity (unless the background Network Manager restarts it again). It would be interesting to do **sudo ifdown eth0** and immediately **ifconfig**, then **ifconfig** again a few seconds later. See if the interface is knocked down and later reinstated by network manager.

---

