---
title: "Why isn't my LAMP Server working?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-05-21
It works whenever I type local host. but whenever i type in my sites name nothing happens...? does anyone know why? it used to work..

---

### Post by thewho? on 2008-05-21
What is the site, is it local, or are you hosting a site on the internet on that server?  If you are trying to hit it via the net([www.whatever.com](www.whatever.com)) you might be having dns issues, apache(webserver) access issues, or you may have ports blocked on your firewall.  Tell us how you're accessing it and what type of site it is.

---

### Post by spiderbatdad on 2008-05-21
Check ifconfig and verify that your router hasn't reassigned your ip...that is make sure it matches the ip that router forwards requests to.

---

### Post by RadiationHazard on 2008-05-21
i'm using the free "Dynamic DNS" offered by [https://www.dyndns.com/](https://www.dyndns.com/) and as far as ports they may have been reset somehow? it's been so long since i've done this. how do i check? (ps. my ip is the same. I checked that.)

---

### Post by jcwmoore on 2008-05-21
sounds like a DNS or router firewall issue, what is your network setup and internet connection like?

---

### Post by RadiationHazard on 2008-05-21
> **jcwmoore said:**
> sounds like a DNS or router firewall issue, what is your network setup and internet connection like?


um...I use roadrunner with a net gear router. um...like what are you asking?..sorry

---

### Post by jcwmoore on 2008-05-21
> **RadiationHazard said:**
> um...I use roadrunner with a net gear router. um...like what are you asking?..sorry

somewhat... you are behind a router, next your internet connection, is it a static IP address or dynamic IP address, also what did you do to set up your site name?

---

### Post by RadiationHazard on 2008-05-21
> **jcwmoore said:**
> somewhat... you are behind a router, next your internet connection, is it a static IP address or dynamic IP address, also what did you do to set up your site name?

just went to dyndns and setup a account and stuff after I'd already set up my router to forward to port 127.000 or something like that I believe. like I said. it's been awhile. and it's static.

---

### Post by jcwmoore on 2008-05-21
> **RadiationHazard said:**
> just went to dyndns and setup a account and stuff after I'd already set up my router to forward to port 127.000 or something like that I believe. like I said. it's been awhile. and it's static.

on your router, you are forwarding from port 80 to 127?  port 80 is the http port and the port that apache listens on.  It should forward from port 80 to your local machine's port 80.  based on your explanation a port forwarding issue seems the likely reason.

you also say it's been a while, have you been able to access it before?

---

### Post by spiderbatdad on 2008-05-22
```
ifconfig
```
will show the inet address of eth0 (wired connection)
the router should forward port 80 to that address...ie, 168.145.12.102 (for example.
DNS should be registered to actual public ip address, as shown at [www.whatismyip.com](www.whatismyip.com)

Then in /etc/apache2/httpd.conf:

ServerName localhost
ServerName <your_domain>

---

### Post by RadiationHazard on 2008-05-22
> **jcwmoore said:**
> on your router, you are forwarding from port 80 to 127?  port 80 is the http port and the port that apache listens on.  It should forward from port 80 to your local machine's port 80.  based on your explanation a port forwarding issue seems the likely reason.

you also say it's been a while, have you been able to access it before?

yes it used to work. and here is what happened when i put in the code that spiderbatdad gave me

```
eth0      Link encap:Ethernet  HWaddr 00:13:A9:80:D7:62  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:31:A2:43  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:fe31:a243/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33470 errors:3 dropped:2652 overruns:0 frame:0
          TX packets:25680 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47071007 (44.8 MB)  TX bytes:4747522 (4.5 MB)
          Interrupt:18 Base address:0xc000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57763 (56.4 KB)  TX bytes:57763 (56.4 KB)

```

---

### Post by spiderbatdad on 2008-05-22
looks like your wired connection is not established.
Edited previous post a bit.

---

### Post by thewho? on 2008-05-22
You are sure your DynDNS account is still active? Also port 127.000?  This is strange.  If your hosting a web page it should be fowarding to something like 80 or 443.  Might want to check on that...

---

### Post by jcwmoore on 2008-05-22
spiderbatdad is correct, you could use your eth1 (wireless) connection but this is not the most secure...  you will need to forward to the 192.168.X.X address that you see in your output.  establish a wired connection run that command again and forward port 80 to the address associated with eth0

---

### Post by RadiationHazard on 2008-05-22
also if it makes any difference my computer is wireless?

---

### Post by RadiationHazard on 2008-05-22
........

---

