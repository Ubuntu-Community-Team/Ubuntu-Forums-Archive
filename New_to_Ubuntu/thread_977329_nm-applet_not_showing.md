---
title: "nm-applet not showing"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by whitethorn on 2008-11-10
I can't find the nm-applet at the top right of the screen.  I've checked in my session and NetworkManager is checked.  When I try to run nm-applet in the terminal I get

> $nm-applet 

** (nm-applet:6578): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6578): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


I also have a wired connection to my network.  I've tried restarting the NetworkManager, and the networking services.  Didn't help.  Notification area is active at the top right of my screen.  

A couple days ago I set up VirtualBox with host interface networking. I'm not sure is this what messed it up. Here's my ifconfig (oh sudo dhclient br0 works)

> ~|$ifconfig
br0       Link encap:Ethernet  HWaddr 00:0f:1f:26:60:8e  
          inet addr:192.168.178.31  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe26:608e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1153190 (1.1 MB)  TX bytes:254615 (254.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:0f:1f:26:60:8e  
          inet6 addr: fe80::20f:1fff:fe26:608e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5002945 (5.0 MB)  TX bytes:704907 (704.9 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9060 (9.0 KB)  TX bytes:9060 (9.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:0b:04:84  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0B-7D-0B-04-84-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Oh here's my /etc/network/interfaces

> auto lo
iface lo inet loopback

auto br0

iface br0 inet dhcp

bridge_ports eth0

up chmod 0666 /dev/net/tun

auto eth0

iface eth0 inet manual


---

### Post by frankleeee on 2008-11-10
After upgrading to intrepid my nm-applet was there after multiple restarts but disappeared a couple of days ago there are several threads on this very problem. I installed wicd that worked as far as being able to have a applet to switch wireless when I go to school.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by whitethorn on 2008-11-16
Is there a way to connect to the vpn tunnel I set up in Administration -> Network Configuration.   I used to just click on the applet for that, but since it's not there anymore I can't.  I need it to connect to the network at my work.

---

### Post by whitethorn on 2008-11-17
bump

---

### Post by whitethorn on 2008-11-18
Don't really like bumping my thread, but I can't find anything on google about this. Help pls.

---

### Post by Farhadi on 2008-12-03
I have the same problem. I installed VirtualBox with Host Interface too. and after that nm-applet tray icon was disappeared.

I have read somewhere in VirtualBox forums that nm-applet can't handle a bridge properly.

It seems nm-applet is running but it's not visible because when you try to run it again you got that error, but when you kill it by using "killall nm-applet" and run it again you don't get any error.

---

### Post by Melvin1981 on 2008-12-04
You can look this thread. Solution helped me to get back nm-applet to notification area.
The idea is to clear your /etc/network/interfaces file (except lines with lo interface) and reboot. After reboot nm-applet is on its place. :D

[http://ubuntuforums.org/showthread.php?t=153481](http://ubuntuforums.org/showthread.php?t=153481)

---

