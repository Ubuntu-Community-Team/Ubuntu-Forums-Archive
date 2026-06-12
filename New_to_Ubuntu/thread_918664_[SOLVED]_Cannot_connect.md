---
title: "[SOLVED] Cannot connect"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by tradet on 2008-09-13
Hey

I've got a pretty big problem now, I can't connect with either my wireless or through ethernet. The wireless I found in another [thread]("http://ubuntuforums.org/showthread.php?t=879134&highlight=wifi+5100&page=7") but I can't connect whatever I do.

Please help, I don't even know what to post here :(

At the top it says "wired network connection" but I can't browse the internet. If I press "connect to 802.1X Protected Wired Network" a box prompting for my pw appears. But you should be able to just connect to my router and it should reach the internet without any password.

Now I've tried with my wireless pw and even my admin/pw to make changes in the router but still nothing, just that it needs a passphrase or encryption key to access.

My router is a "netgear WGR614" and my network card is a "Realtek RTL8168C(P)/8111C(P) Family PCI-E Gigabit Ethernet NIC (NDIS 6.0)". At least according to vista and it works fine there.

Uhm.. well that's it I guess :)

Oh and I'm very new, don't know nothing. Thx in advance

---

### Post by cdtech on 2008-09-13
Let's see what you get with the output:
**ifconfig**

---

### Post by tradet on 2008-09-13
```
PC:~$ ifconfig
eth0     
Link encap:Ethernet  
HWaddr 00:1e:68:c1:57:60            
inet addr:192.168.1.5  
Bcast:192.168.1.255  
Mask:255.255.255.0          
inet6 addr: fe80::21e:68ff:fec1:5760/64 Scope:Link          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1          
RX packets:62 errors:0 dropped:1083625953 overruns:0 frame:0          
TX packets:63 errors:0 dropped:0 overruns:0 carrier:0          
collisions:0 txqueuelen:1000           
RX bytes:5276 (5.1 KB)  
TX bytes:7780 (7.5 KB)         
Interrupt:216 Base address:0x2000 lo        
Link encap:Local Loopback            
inet addr:127.0.0.1  Mask:255.0.0.0          
inet6 addr: ::1/128 Scope:Host        
UP LOOPBACK RUNNING  MTU:16436  Metric:1        
RX packets:1978 errors:0 dropped:0 overruns:0 frame:0          
TX packets:1978 errors:0 dropped:0 overruns:0 carrier:0         
collisions:0 txqueuelen:0          
RX bytes:98900 (96.5 KB)  
TX bytes:98900 (96.5 KB)
```

Edit: The format got a bit screwed, linebreaks and so on..

---

### Post by tradet on 2008-09-15
Anyone? :(

---

### Post by cdtech on 2008-09-15
I just got back (out of town). Your Ethernet is up. Did you ever have a wired connection before Ubuntu?

---

### Post by tradet on 2008-09-15
Yes, I have the portable connected to my router which is connected with my stationary where I'm writing this. All are wired.

---

### Post by Idefix82 on 2008-09-15
I have the same ethernet card and I also have big problems with it. Sometimes Ubuntu doesn't recognise the card, sometimes it does. I also dual boot, in my case Win XP and Ubuntu 8.04.
Next time your network doesn't work, can you type in
```
lshw -C network
```
and copy the output here?

---

### Post by tradet on 2008-09-15
```
treeman@treeman-PC:~$ sudo lshw -C network
[sudo] password for treeman: 
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-generic
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: ff
       serial: 00:1e:68:c1:57:60
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=twisted pair speed=1GB/s

```

---

### Post by Idefix82 on 2008-09-15
Yep, exactly the same problem as on my machine. For some reason the driver didn't recognise the ethernet card (it shouldn't be saying Illegal Vendor ID).
Two things that you could try, neother of them is a satisfactory long term solution:
1. Shut down the laptop, unplug all cables (this is important) wait for about 30 seconds or a minute, start it up again and boot Ubuntu. Try the same command as before (lshw -C network). If instead of illegal Vendor ID you can now see Realtek... then you are up and running. If not then go to step 2:
2. I find this kind of spooky and am yet to see an explanation, but this often works for me: restart the computer again and this time boot Windows. Login, but don't do anything, just restart it again and boot Ubuntu. Check, whether you are connected.

Let us know, if this works. If anybody has a more sane solution, I would be extremely grateful!

---

### Post by tradet on 2008-09-15
Whoa it worked! :)

---

### Post by Idefix82 on 2008-09-15
Glad, I could help! Please, please let me know if you find a proper solution!

One more question: which one of the two things helped? If it is the former, then there is hope for you. Next time you boot Windows, go to the hardware manager, find the ethernet card and in the advanced settings set Wake-On-Lan to Enabled. In the power saving tab forbid Windows to switch off the card to save energy. This might solve the problem for good. It didn't for me but others have reported that it did for them.

---

### Post by tradet on 2008-09-15
Yes it was the first one. I'll try it and come back.

Thx again :)

---

### Post by snakra on 2008-09-15
Hello,

Idefix82

Your point as follows:

2. I find this kind of spooky and am yet to see an explanation, but this often works for me: restart the computer again and this time boot Windows. Login, but don't do anything, just restart it again and boot Ubuntu. Check, whether you are connected.

I've also got a dual boot Ubuntu 8.04 and Windows XP Tablet Edition and using an Ecolife HG520s router.  Everything had been working fine till one bright morning the router was not recognised. after a bit of trial and error I decided to see if XP would recognise the router - it did. Went back to Ubuntu and guess what - it too recognised the router and all has been well since. 

Would love to know:

1 why Ubuntu stopped recognising the router and

2 why and how did it correct itself after the XP boot.

Thanks

SN

---

### Post by Idefix82 on 2008-09-15
> **snakra said:**
> 
1 why Ubuntu stopped recognising the router and

2 why and how did it correct itself after the XP boot.

Thanks

SN

I wish, I knew! As a matter of fact this procedure only solves the problem for me for one session. Next time I boot Ubuntu it usually doesn't recognise the card again. I can only guess that Ubuntu somehow manages to put the ethernet card to sleep in such a way that it can't wake it up again. Windows wakes it up again and after that it works under Ubuntu too. But this is just a random guess and I find this theory very weird, it's just that I don't have a better one. I am not a Linux expert by any account and don't know much about ethernet cards and drivers either so I have been hoping for some help from the gurus on these forums, but so far I didn't get any.

---

### Post by Idefix82 on 2008-09-18
Update for everybody:
the problem is actually a bug in the driver that Ubuntu uses by default.
If you follow the instructions on this website:
[http://www.jamesonwilliams.com/hardy-r8168.html]("http://www.jamesonwilliams.com/hardy-r8168.html")
or simply download and execute the script from there, then this should fix the problem forever. It did for me. If this behaviour doesn't occur for you anymore then don't bother, since it will be fixed in the next version 8.10 and also in 8.04.2 which is due to come out in February 2009.

---

