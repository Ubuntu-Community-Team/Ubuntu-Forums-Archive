---
title: "Some internet annoyances..."
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Jeeeep on 2008-07-24
Recently switched user (Xubuntu 8.04.1), bear with me. Most of these should be simple though...

Whenever I load up Firefox, it always starts with "Work Offline" checked. I've tried messing around with all of the configuration options myself, and I don't see anything that could be causing this. It's not really that much of a problem, it's just a little itch I would like to scratch.

Pidgin gets a message at the bottom that says "Waiting for Network..." and none of my IM accounts will connect on startup. Again, it's just an annoyance as I can get them to connect by disabling all of my accounts, then enabling them. I have quite a few, however, so having to do this every time I start up Pidgin gets annoying quickly.

Lastly, I use my Verizon Wireless Broadband Access WWAN connection card (Don't ask what version, I lost all of that information long ago. It's a Pantech USB modem, if that helps.) to connect to the internet (sadly, only source of non-dialup connection out here). I've got wvdial working, but for some reason whenever I load a large file (20MB+), pppd disconnects (The modem has hung up, Exit Code 16). It reconnects pretty quickly so it's not a huge problem, it's just annoying. It also makes it a pain in the **** to watch online videos, which is one of my main uses of this computer so I'd love to have this one fixed. I haven't called Verizon about it yet, I'd figure I would look around online first and try to dodge the hassle of dealing with their customer service first... I would probably get a "Linux is not supported therefore we cannot help you, that'll be $57.98" anyway.

Help?

---

### Post by DGortze380 on 2008-07-24
> **Jeeeep said:**
> Recently switched user (Xubuntu 8.04.1), bear with me. Most of these should be simple though...

Whenever I load up Firefox, it always starts with "Work Offline" checked. I've tried messing around with all of the configuration options myself, and I don't see anything that could be causing this. It's not really that much of a problem, it's just a little itch I would like to scratch.

Pidgin gets a message at the bottom that says "Waiting for Network..." and none of my IM accounts will connect on startup. Again, it's just an annoyance as I can get them to connect by disabling all of my accounts, then enabling them. I have quite a few, however, so having to do this every time I start up Pidgin gets annoying quickly.


Make sure your wifi is up and running before you open firefox or pidgin. Sounds like you're just not connected to the internet yet.  To test your connection you can always ping a website. Open a terminal and type

```

ping http://www.cnn.com/

```

---

### Post by Jeeeep on 2008-07-24
Tried pinging, got "ping: unknown host". Any instructions on how to fix this?

---

### Post by stevoo on 2008-07-24
maybe you are not connected to the internet

try 
ifconfig
post results please

---

### Post by Jeeeep on 2008-07-24
I would have thought that, you know, being able to load up web pages would mean I'm connected, but eh, I'm the newb here.

```
eth0      Link encap:Ethernet  HWaddr 00:08:74:48:39:58  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:400 errors:0 dropped:0 overruns:0 frame:0
          TX packets:400 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20000 (19.5 KB)  TX bytes:20000 (19.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:<IP>  P-t-P:<Another IP>  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:184 errors:6 dropped:0 overruns:0 frame:0
          TX packets:177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:207000 (202.1 KB)  TX bytes:14054 (13.7 KB)
```


On an unrelated note, this is what /var/log/messages gives me during the disconnecting with my third issue...

```
Jul 24 09:48:53 p-laptop pppd[10413]: No response to 4 echo-requests
Jul 24 09:48:53 p-laptop pppd[10413]: Serial link appears to be disconnected.
Jul 24 09:48:53 p-laptop pppd[10413]: Connect time 6.5 minutes.
Jul 24 09:48:53 p-laptop pppd[10413]: Sent 192037 bytes, received 7823168 bytes.
Jul 24 09:48:55 p-laptop pppd[10413]: Modem hangup
Jul 24 09:48:55 p-laptop pppd[10413]: Connection terminated.
Jul 24 09:48:55 p-laptop pppd[10413]: Exit.
```

---

### Post by stevoo on 2008-07-24
My best idea is that you dont get connected. I am not sure how else i can shet some light here.

Maybe some drivers for the USB modem ? 

Perhaps some else can help ....

---

### Post by DGortze380 on 2008-07-24
you're problem isn't firefox or pidgin, you're not connected to the internet. I don't have any experience with your particular card. Hopefully someone else does. In the mean time try to find a model number on your wireless card and start googleing  "<card name> linux" "<card name> ubuntu"  "<model number> linux" "<model number> ubuntu" ... see if you find someone that has that card working under a linux distro.

---

### Post by Jeeeep on 2008-07-24
*sigh* I've tried everything I can come to think of at this point (including [this]("http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=42571.0") guide and many others, the exact same problems no matter what I do). I found out that my card is a UM150, if that helps at all.

I just don't get it. EVERYTHING I look up online either just flat-out doesn't work, or connects, but all the same issues still happen. I even tried installing the Windows access manager under Wine, but that comes to a halt when it needs to "detect my modem" which won't work. I'm out of ideas. D:

---

### Post by DGortze380 on 2008-07-24
> **Jeeeep said:**
> *sigh* I've tried everything I can come to think of at this point (including [this]("http://www.pclinuxos.com/index.php?option=com_smf&Itemid=26&topic=42571.0") guide and many others, the exact same problems no matter what I do). I found out that my card is a UM150, if that helps at all.

I just don't get it. EVERYTHING I look up online either just flat-out doesn't work, or connects, but all the same issues still happen. I even tried installing the Windows access manager under Wine, but that comes to a halt when it needs to "detect my modem" which won't work. I'm out of ideas. D:

There is obviously a widnows driver for the card right? Have you looked into ndiswrapper?

---

