---
title: "internet connectivity problem"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by Happycamper374 on 2008-08-01
Hi,

I installed Hardy on my Lenovo Thinkpad R61 laptop at the beginning of summer and it's been working fine. I've been hopping from campus to campus using the internet with no problems. I'm now moved in to a new apartment and can't connect to the internet via my ethernet port and cable. I have connected via hard wire in the past. The internet does work in the apartment as I'm typing this out on my desktop that runs xp. 

I read in another forum that it could be an issue with the router and not my comp. How do I check this? I've only been using linux for the summer and mostly for word processing but I'm not afraid to get dirty in the terminal if someone tells me how.

Thanks

---

### Post by phidia on 2008-08-01
With the ethernet plugged in open a terminal and enter "ifconfig" without the quote marks. Post the results of that here please.

---

### Post by Happycamper374 on 2008-08-01
paul@paul-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:91:54:dc  
          inet6 addr: fe80::21c:25ff:fe91:54dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27574 (26.9 KB)  TX bytes:6424 (6.2 KB)
          Interrupt:22 

eth0:avahi Link encap:Ethernet  HWaddr 00:1c:25:91:54:dc  
          inet addr:169.254.7.182  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:121552 (118.7 KB)  TX bytes:121552 (118.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:28:0c:6d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1675 errors:0 dropped:0 overruns:0 frame:0
          TX packets:833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:461077 (450.2 KB)  TX bytes:171785 (167.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-28-0C-6D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Thanks for your help.

---

### Post by Happycamper374 on 2008-08-02
Bump.

---

### Post by coffeecat on 2008-08-02
> **Happycamper374 said:**
> net addr:169.254.7.182  Bcast:169.254.255.255  Mask:255.255.0.0

There's the problem. If you get an IP address of 169.154.x.x in any operating system, this means that your computer is unable to contact the DHCP server, the router you are connected to.

The address range for the network you are trying to connect to will be either 10.0.x.x or 192.168.x.x. It might be useful seeing which it is. In your Windows XP computer, open a command prompt window and type 'ipconfig' and then return. Yes, that's right, ipconfig.

Windows - ipconfig
Linux - ifconfig

You will get four lines: DNS suffix (we don't need this), IP address, subnet mask and default gateway. What do you get? The default gateway is the IP address of the router.

Post the output and someone might be able to help. In the meantime, try two things. Double-check the cable you are using to connect the Linux machine to the network. Is it the same as the one you use for the Windows machine? The other is that the person administering the network might be willing to give you a fixed IP address. You'll have to use System > Administration > Network to set that up, and you use the gateway address and subnet mask you got from the Windows command prompt. That might work where DHCP is failing for whatever reason.

**Edit:** I assumed from your use of the words 'campus' and 'apartment' that you are connecting to a campus network - which is why I referred to a network administrator. If that is a domestic-type router connected to a private broadband account, then perhaps some details of the router might be useful.

---

### Post by Happycamper374 on 2008-08-03
Ok I got 

IP addy............69.134.2.11
subnet mask........255.255.248.0
default gateway....69.134.0.1

The ethernet cable is the same one hooked up to the xp machine. I'm just unplugging it from the desktop and plugging into the laptop.

I'm now in a residential area with no sys admin. We just had the Time Warner cable guy drop off a router and set us up.

The model number of the router is U10C018.80 which makes it an Ambit Broadband.

Thanks again for the help.

---

### Post by coffeecat on 2008-08-03
I think I have an answer for you. When you referred to a 'router' I assumed you were on a private network (whether domestic, university or enterprise) which is why I mentioned the 192.168.x.x and 10.0.x.x address ranges. Those 69.134..... addresses are a giveaway and tell a different story which means that I don't think what you are calling a router is a router - probably a cable modem, but let's not argue over semantics. That's not important now.

You're with Time Warner - that's cable, not adsl, yes? Try doing a reverse whois on your IP address and the gateway address [here](http://tools.whois.net/whoisbyip/). The results are slightly surprising.

But whatever, if I'm right, you are being allocated the IP address of 69.134.2.11 by Time Warner's (or their subcontractor's) router 69.134.0.1. I don't have any personal experience of cable (I use adsl over an old-style copper phone line) but from what I've read, the cable modem will only connect a NIC with a MAC address it knows about. I think you would have had the same problem if you had tried to connect another Windows machine. The MAC address of the ethernet NIC in your Linux machine is in the output of ifconfig, under HWAddr. I believe you either have to contact the support line of Time Warner or there may be some web-based facility to do this. Try not to mention Linux if you need to contact them. You'll probably get some support-drone telling you they don't support Linux when the issue has nothing to do with the OS.

---

### Post by coffeecat on 2008-08-03
Adding another post, rather than editing the previous one:

I don't know whether this is any help, but [here is a middle page]("http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=7005&postdays=0&postorder=asc&start=30") from a thread on another forum about setting up on Virgin cable here in the UK. As far as I can make out, the OP chose to buy an ethernet router to connect to her cable modem so that she could connect her Linux, Windows and MacOS machines. She's certainly uses an eclectic range of OSs :?. And she had to use a setup CD (if I read this correctly) to register the MAC address of the router.

I don't know whether Virgin cable uses the same sort of system as Time Warner, but having a router, so long as its MAC is registered to your account, should obviate the problem. The Time Warner router will never 'see' the MAC addresses of any computers connected to the router. All it knows is the router.

Oh, by the way, I did a quick google on U10C018.80, and it seems that is a modem, not a router - I'm glad to say, otherwise I'd still be scratching my head. :)

And another by the way - if you wish, try reading the whole thread. There's quite a relaxed atmosphere on it, with the posters wandering happily on and off topic. I don't think it would be allowed here. :wink:

---

### Post by Happycamper374 on 2008-08-03
Thanks a lot for the help. I'll post to let you know how it turns out.

As far as the misuse of words, I would have called it a cable modem as well, but since I'm the clueless guy who is posting on the tech forum I tried to adopt the words that were used in the post and went with router. People often use them interchangeably anyway. But yes, it's a cable modem :)

Thanks again!

---

### Post by ellgor on 2008-08-03
Hi,

If all else fails, switch the router off for a couple of minutes and then restart, after months of trying this and that thats all it took for me, in a nutshell, the router needs to forget the old settings and take on the new, hope this helps.

Regards, Ellgor.

---

### Post by coffeecat on 2008-08-03
> **ellgor said:**
> If all else fails, switch the router off for a couple of minutes and then restart

I think the OP might find that a tad difficult. The only router in this case is owned by Time Warner and is probably located a couple of states away. :wink:

---

### Post by texasjim on 2008-08-03
I had this same problem with Time Warner.  The quick solution is to power off the cable modem when switching computers, as TWC doesn't allow changing MAC addresses without a reset. 

Better fix, get a wired router (Not a hub) or a wireless router and connect to your TWC cable modem.

FYI, I got a wired router for 5 bucks at my local goodwill.

Hope this helps
  Jim

---

### Post by Happycamper374 on 2008-08-03
Well, I went for the quick and easy fix of just turning off the cable modem and computer and that seems to work fine. I for some reason had to turn off the computer to get it to work as well. I'm not sure why and I don't think I've tried every iteration of actions possible so I'm not worried. 

So, my plan is to get a wireless router. If I'm understanding everything correctly, I'll be able to run multiple computers through that and not have any problems. That's my ticket. 

Thanks for all the help everyone. I've been lurking for a while and finally had to post to solve a problem. I appreciate all the good, friendly, and timely help.

---

