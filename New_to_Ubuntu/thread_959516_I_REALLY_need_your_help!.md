---
title: "I REALLY need your help!"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-10-26
I have had my own site set up before on my Sony Vaio laptop using L.A.M.P. on Ubuntu 7.10. I have L.A.M.P. installed everything is working great as far as that goes. When I go to [http://localhost/](http://localhost/) everything pulls up as it should. Now where my problem is that when I put in my ip it doesn't do anything. I know that I need to do port forwarding or something but I don't know how. I have a NETGEAR WGR614 click [[COLOR="Blue"]**here**[/COLOR]]("http://www.google.com/products/catalog?hl=en&q=netgear+wgr614&cid=10256100175040107864#ps-sellers") for a little more info. I know how to login to the router and get to the portforwarding but after that I don't know what ports to forward too or anything. I am using the wireless built into my laptop with the router and like I stated earlier I know that it can be done, I've had it set up before and it worked like a charm. Thank you so much in advance to anyone who can help me get this set up again! I have been trying to get this working again for months.

---

### Post by scorchgeek on 2008-10-26
I'm pretty sure webservers use port 80, but I'm not sure I quite get what you're trying to do. Are you trying to run a webserver on your computer?

---

### Post by RadiationHazard on 2008-10-26
> **scorchgeek said:**
> I'm pretty sure webservers use port 80, but I'm not sure I quite get what you're trying to do. Are you trying to run a webserver on your computer?

yes, sorry I tried to give as much detail as I could and probably confused most people. but yes, I have the actual web server set up on my computer using LAMP. Now I am just trying to get my router to forward to the sever when people go to my ip address so I can share my site with others.

---

### Post by ciscosurfer on 2008-10-26
> **RadiationHazard said:**
> I have had my own site set up before on my Sony Vaio laptop using L.A.M.P. on Ubuntu 7.10. I have L.A.M.P. installed everything is working great as far as that goes. When I go to [http://localhost/](http://localhost/) everything pulls up as it should. Now where my problem is that when I put in my ip it doesn't do anything. I know that I need to do port forwarding or something but I don't know how. I have a NETGEAR WGR614 click [[COLOR=Blue]**here**[/COLOR]]("http://www.google.com/products/catalog?hl=en&q=netgear+wgr614&cid=10256100175040107864#ps-sellers") for a little more info. I know how to login to the router and get to the portforwarding but after that I don't know what ports to forward too or anything. I am using the wireless built into my laptop with the router and like I stated earlier I know that it can be done, I've had it set up before and it worked like a charm. Thank you so much in advance to anyone who can help me get this set up again! I have been trying to get this working again for months.There's always a few ways of doing things, but this thread might prove useful: [http://ph.ubuntuforums.com/showthread.php?t=870433](http://ph.ubuntuforums.com/showthread.php?t=870433) (post 3 has some good tips, but read the whole thread).

---

### Post by RadiationHazard on 2008-10-26
> **ciscosurfer said:**
> There's always a few ways of doing things, but this thread might prove useful: [http://ph.ubuntuforums.com/showthread.php?t=870433](http://ph.ubuntuforums.com/showthread.php?t=870433) (post 3 has some good tips, but read the whole thread).

I will, thank you and I'll let you know how it goes for me. :)

---

### Post by Xiong Chiamiov on 2008-10-26
You need to muddle around in your router settings until you find the port forwarding section.  Then you'll want to forward port 80 to the IP of your computer.

---

### Post by RadiationHazard on 2008-10-26
to be honest guys that thread really isn't working for me. :( or maybe I am just stupid and not doing it right.

here is what happens when I type ifconfig in my terminal
```
eth0      Link encap:Ethernet  HWaddr 00:13:A9:80:D7:62  
          inet addr:192.168.1.150  Bcast:192.168.1.255  Mask:255.255.255.0
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
          RX packets:12266 errors:22 dropped:4136 overruns:0 frame:0
          TX packets:10740 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89397779 (85.2 MB)  TX bytes:5893124 (5.6 MB)
          Interrupt:18 Base address:0x2000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1333 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1500005 (1.4 MB)  TX bytes:1500005 (1.4 MB)

```

and here is a screenshot of the page where I do my port forwarding...

[http://i36.tinypic.com/2uxzq55.jpg](http://i36.tinypic.com/2uxzq55.jpg)

---

### Post by Xiong Chiamiov on 2008-10-26
You need to change the server IP to either 192.168.1.150 or 192.168.1.3, whichever is the connection you're actually using.  My guess would be the latter.

---

### Post by RadiationHazard on 2008-10-26
> **Xiong Chiamiov said:**
> You need to change the server IP to either 192.168.1.150 or 192.168.1.3, whichever is the connection you're actually using.  My guess would be the latter.

alright, awesome!
atleast now when I put in my ip it pops up for me to login to my router.
now how do I make it go to my site instead of my ip.

ps. thank you for all your help!

---

### Post by Xiong Chiamiov on 2008-10-28
Port 80 will by default be used for the web interface, so I'd suggest changing the admin interface's port to 8080 (the alternate), after which everything should work fine.  Alternatively, you could use port 8080 to connect, but that would require you specifying a port in your browser every time, which I don't think you want.

---

