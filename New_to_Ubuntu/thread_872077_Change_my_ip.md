---
title: "Change my ip"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-27
How can i change my ip without restarting my router and my computer?
I also would like to now my current ip(through terminal)?

---

### Post by maybeway36 on 2008-07-27
I know to find your ip you can use:
```
/sbin/ifconfig
```

---

### Post by stevoo on 2008-07-27
i dont think that is possible. 
If you are talking about the IP that you connect to the internet then that is impossible, depending always from your ISP. 

Usually the only way to do it is to reboot your ISP's modem. 
That is when the ISP will ( perhaps ) release your IP and give you a new one, if you are on a dynamic IP

---

### Post by stevoo on 2008-07-27
> **maybeway36 said:**
> I know to find your ip you can use:
```
/sbin/ifconfig
```

why do you use /sbin ? 
you can just do it with only 
ifconfig

---

### Post by cristo-father on 2008-07-27
i have a dynamic ip. i have a new ip after restarting my router.

---

### Post by billgoldberg on 2008-07-27
Changing your IP might be impossible if it's a static one.

I have a dynamic one, that changes every time I reset my router.

It has to be done manually.

The downpart to dynamic ip adresses is that's it harder to set up a server for to world to access.

If you want to change your ip adress (proxy) for accessing a website, click [here]("https://addons.mozilla.org/en-US/firefox/addon/2464").

---

### Post by crtlbreak on 2008-07-27
It is all managed under the GUI in system>administration>network OR manually in terminal under
sudo ifconfig
OR
/sbin/ifconfig will deliver the results in terminal.
to change your IP address (at least that is what I think you want to do?) - are you possibly talking about your public IP address or your internal addres??
as there is a good chance that you have an internal and an external address which are different (typically 192.168.1.33 for internal and 203.21.224.127 for external)
or your internal can be 10.x.x.x or even 172.x.x.x depending on the type of router - or just to muddy things up a a bit further it can actually look like a public address but also be internal? if it has been manually configured as such.

possibly send/post your ifconfig  - and that of your router - and more importantly tell us which IP address are you wanting to change?
regards

---

### Post by stevoo on 2008-07-27
well there is no way to change the IP with out resetting the router.
IP is dynamically reserved in your ISP servers and it will only be released when resetting the router. 

That is how it works.....

---

### Post by cristo-father on 2008-07-27
```
diastopher@diastopher-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:06:75:cb  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe06:75cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150497234 (143.5 MB)  TX bytes:5100319 (4.8 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:06:5f:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62400 (60.9 KB)  TX bytes:62400 (60.9 KB)

diastopher@diastopher-desktop:~$ 

```

The ip i want to change is the one detected by forums, game servers etc...

---

### Post by stevoo on 2008-07-27
above

---

### Post by lisati on 2008-07-27
> **cristo-father said:**
> ```
diastopher@diastopher-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:06:75:cb  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe06:75cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103084 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:150497234 (143.5 MB)  TX bytes:5100319 (4.8 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:22:15:06:5f:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:62400 (60.9 KB)  TX bytes:62400 (60.9 KB)

diastopher@diastopher-desktop:~$ 

```The ip i want to change is the one detected by forums, game servers etc...
The numbers I recognize as IP addresses here look like your internal ones (i.e. on your own home network), not the ones that the forums will see.

---

### Post by maybeway36 on 2008-07-27
You can go in /etc/network/interfaces and have it say:
```
auto eth0
iface eth0 inet static
address 192.168.1.xxx (replace this with whatever IP you want)
netmask 255.255.255.0
```
Then run:
```
sudo ifdown eth0;sudo ifup eth0
```

---

### Post by halitech on 2008-07-27
to change the IP address of your router (aside from turning it off and on), you can log into the routers web interface and on one of the tabs (depends on your router) there should be a DHCP Release and DHCP renew buttons. Click release then renew and that will renew the WAN IP address.It should also tell you what the IP address is there as well.

For the internal, do as others have suggested and in a terminal do ```
ifconfig
```

---

### Post by crtlbreak on 2008-07-28
if you are happy changing your IP (or specifically want/need to change your IP) then consider using dynamic dns  - someone like 
dyndns.org?
that way you can choose your dns and (irrespective of your IP) keep the routing of traffic as you wish through your custom public dns?
regards

---

### Post by RavUn on 2008-07-28
I'm assuming you were banned by IP?  You can check this site out for some info.  It's for Windows but you could probably translate over to Linux.

[http://whatismyipaddress.com/staticpages/index.php/banned](http://whatismyipaddress.com/staticpages/index.php/banned)

---

### Post by stoneybroke on 2008-07-28
If you go here [http://whatismyipaddress.com/](http://whatismyipaddress.com/) it will show you you outside address if your IP is dynamic this address might change every time you turn on your modem.

This site also has a lot of very useful information on IP addresses.

Hope that helps.

---

### Post by sharks on 2008-07-28
> **stoneybroke said:**
> If you go here [http://whatismyipaddress.com/](http://whatismyipaddress.com/) it will show you you outside address if your IP is dynamic this address might change every time you turn on your modem.

This site also has a lot of very useful information on IP addresses.

Hope that helps.

+1

If u have a dynamic ip it will change once your modem is switch off and on .

---

### Post by lisati on 2008-07-28
> **stoneybroke said:**
> If you go here [http://whatismyipaddress.com/](http://whatismyipaddress.com/) it will show you you outside address if your IP is dynamic this address might change every time you turn on your modem.

This site also has a lot of very useful information on IP addresses.

Hope that helps.
It even correctly identified my general geographic location.... I'm impressed

---

