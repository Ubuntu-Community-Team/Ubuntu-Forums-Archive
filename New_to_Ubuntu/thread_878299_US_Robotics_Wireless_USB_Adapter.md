---
title: "US Robotics Wireless USB Adapter"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by cool_penguin on 2008-08-02
Hi everybody,

I am trying out an US Robotic Wireless USB Adapter. Model number: 5423.

It works out of the box in Ubuntu Hardy. The network manager shows it as Unknown USB device, but still shows the list of available wireless networks and signal strength bars. However, I am able to log on to unsecure wireless networks without any problem. But when I log on to WPA secure network, I am unsuccessful. 

I am very happy to see this USB Wifi adapter work out of the box, but it wouldn't let me log on to WPA secure networks. This card is listed to work out of the box right from the 7.10 (Gutsy) versions and also on Hardy. 

Please help me guys. 

Thanks a million.

Cheers,
Harry

---

### Post by cool_penguin on 2008-08-02
Somebody, Anybody?

---

### Post by spiderbatdad on 2008-08-02
wpa supplicant from synaptic package manager?

---

### Post by cool_penguin on 2008-08-03
I checked. It is installed. In fact, i am able to connect to WPA network using my inbuilt Wireless *Atheros". I just wanted to get rid of using the native Windows driver that I am use with NDISWrapper. 

This USB US Robotics wifi adapter works out of the box without Windows driver but then I am unable to log on to WPA secured networks.

---

### Post by cool_penguin on 2008-08-08
No body yet. 

I need help. Please somebody help.

---

### Post by andrewjoy on 2008-08-08
I had a U.S Robotics PMCIA card for my laptop a while ago before i got the macbook and replaced the 2nd laptops card with a Netgear.

The only way i got it to work was using the wrapper and the windows driver there was just no other way to do it because of U.S robotics woeful linux support.

For now i would say keep using the wrapper and buy a replacement card as soon as possible and check its linux support first, and never buy anything form U.S Robotics again.

---

### Post by waspbr on 2008-08-08
k, some one pls correct me if I say something outrageous, but as far as I can understand here, your problem is not the adapter or the drivers but logging in to a WPA protected network using Network-manager. 

though I haven't had that problem yet, I have heard quite a few people that have, the first thing I would try would be to left click in the network manager (NM) applet (usually in your system tray) and click on "connect to other wireles networlk" (something like that).

then if personal WPA doesn't work, I would try the enterprise type, WPA1 or WPA2... not sure what is the difference really but moving on, that would be the most basic way. 

if all fails, I would recommend you give wicd a shot, google it and download the .deb file, the unstable (testing) version should be stable enough. A lot of people seem to find wicd more easy-going then NM.

my 23 cents... yes you heard me right not two...

---

### Post by cool_penguin on 2008-08-08
Hi Guys, 

I solved the problem. I installed the following drivers from:

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

I compiled it, installed it and followed the instructions and now my USB wifi adapter is up and running. I am successfully able to log on to WPA secured networks. 

However, the only turn down is that the network manager does not show my device as US Robotics, instead shows me Wireless Networks (Unknown USB vendor specific interface). But I can live with that for the moment. 

Long Live Ubuntu and FOSS.

Cheers,
Harry

---

