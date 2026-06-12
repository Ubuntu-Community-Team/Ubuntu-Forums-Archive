---
title: "internet and screen help"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by super61 on 2008-06-02
alright well i have a laptop with 2 problems. 
1) the ethernet does not work for some reason. It work for everything else ( like windows ) but not ubuntu. some help would work. 
2) My screen is at a 800x600 resolution. i want it at 1024x756 but the xorg server changed alot in this and i dont know to change it i can use some help with that. 

thank you and if you need any PC info tell me 

~*super61*~

---

### Post by james_vanb on 2008-06-02
To change screen resolution go to System > Preferences > Screen Resolution.

How are you trying to connect to the internet - Wireless or Wired.  It may help to post output of:

```
ifconfig
```

---

### Post by super61 on 2008-06-03
Alright, i know but that option is not in the resolution. So i was going to fix it via x-org server but that changed a lot in it. 

Now the internet, My set up is 2 computer a and b. A has the main internet and the wireless device is in internet sharing. B has ubuntu installed and here the ifconfig out put 

> eth0      Link encap:Ethernet  HWaddr 08:00:46:48:04:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0:avahi Link encap:Ethernet  HWaddr 08:00:46:48:04:c1  
          inet addr:169.254.5.58  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:167492 (163.5 KB)  TX bytes:167492 (163.5 KB)


I know this works becuase it works with internet from a cable and it intrenet is set up right because i used it with my ps3 on ubunru to get it to work. so any help will be helpful.

---

### Post by james_vanb on 2008-06-03
Have you tried to edit /etc/X11/xorg.conf file. Had similar problem a while ago. As I remember, edited file as follows:


Code:
sudo gedit /etc/X11/xorg.conf

You should see a section that looks like this:

Section "Screen"

There should be a subsection called "Virtual". If it is not set to the correct resolution, edit. Or you may have a section called "Mode" that lists available resolutions. As I recall, the first resolution listed will be used. Edit appropriately.

---

### Post by superprash2003 on 2008-06-03
go to system->administration->network and click on eth0 properties and change from roaming mode to DHCP mode (restart if required) and then type ifconfig and post output

---

### Post by super61 on 2008-06-03
Im useing 8.04 and this well not work with it. The ifconfig output is the same because thats what i did, and the x-org thing has changed so you cant do it that way any more. so anything else well up, I would have to install it from 7.04 to 8.04 manually to get everything to worl and i dont want to. so anything else well help alot. thanks

---

### Post by james_vanb on 2008-06-03
I'm not sure, but it sounds like you are trying to set up internet sharing from one main computer (A) to another (B).  Only thing I could find on the issue is the following:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
[http://ubuntuforums.org/showthread.php?t=59186](http://ubuntuforums.org/showthread.php?t=59186)

Can't offer much more on the topic.  Maybe someone else can.

As for screen resolution.  What has changed in x-org - how was it changed - What made you change it?  Maybe attach a screen shot of x-org file.  Don't understand why the file can not be edited.

---

### Post by superprash2003 on 2008-06-03
what is your modem's ip address? have you tried static ip instead of DHCP?

---

### Post by super61 on 2008-06-03
> **james_vanb said:**
> I'm not sure, but it sounds like you are trying to set up internet sharing from one main computer (A) to another (B).  Only thing I could find on the issue is the following:

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)
[http://ubuntuforums.org/showthread.php?t=59186](http://ubuntuforums.org/showthread.php?t=59186)

Can't offer much more on the topic.  Maybe someone else can.

As for screen resolution.  What has changed in x-org - how was it changed - What made you change it?  Maybe attach a screen shot of x-org file.  Don't understand why the file can not be edited.

Ok, the dev have changed it not me, everyone had the problem. well thanks and ill tinker with it

> **james_vanb said:**
> Have you tried to edit /etc/X11/xorg.conf file. Had similar problem a while ago. As I remember, edited file as follows:


Code:
sudo gedit /etc/X11/xorg.conf

You should see a section that looks like this:

Section "Screen"

There should be a subsection called "Virtual". If it is not set to the correct resolution, edit. Or you may have a section called "Mode" that lists available resolutions. As I recall, the first resolution listed will be used. Edit appropriately.

---

