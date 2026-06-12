---
title: "start/restart internet key connection"
date: 2010-01-21
forum: Programming Talk
---

### Post by fabien77 on 2010-01-21
Hi,
 
I'm new in ubuntu and in this forum.
 
I have a need: I have a simple bash script that detects if my internet key is connected or not to internet (it is connected to USB port but it can be not connected to internet).
 
Is There a way (by bash script) to try to start internet connection? If yes, can it be detected by Network Manager?
 
I'm using ubuntu 9.04 and at this moment i'm using a huawei e169g internet key (but maybe I have to support some ather keys).
 
I hope this is the right place to post this, if not excuse me in advance
 
bye

---

### Post by fabien77 on 2010-01-22
please, can someone help me? This problem is becoming urgent

---

### Post by Zugzwang on 2010-01-22
I guess the point here is that a "connection to the internet" is some abstract thing. You did not specify how you would manually connect to the internet. Does this just require "turning on the network interface"? Or is there something more involved? How comes that you do not have a connected even if the USB device is plugged in? Did you tell the network manager not to automatically connect?

You might want to try if the following works from the terminal: "sudo ifup wlan0", where you replace "wlan0" by the name of your network device. You can look up the list of network devices using the "ifconfig" command. Does "sudo ifup wlan0" work here?

---

### Post by fabien77 on 2010-01-22
Hi Zugzwang,
 
thanks for reply.
 
in this moment I'm not at home, so I will try your solution ("sudo ifup ppp0" for me) later.
 
Anyway, usually I start connection by using NetworkManager (the icon in the try), and yes, I don't have network manager to automatically connect, this is because I want that connection starts ONLY when some conditions happen (conditions determined by a bash script).
 
I remember that, when I tried "ifconfig", I couldn't retrieve ppp0 entry, so I think that when internet key is disconnected (by using network manager for example) there is not the ppp0 interface.
 
bye
 
p.s. excuse me for my bad english, i'm italian and foreign languages was not my favorite school subject...:(

---

### Post by Axos on 2010-01-22
I'd love to know how to do this too. At least once a day, my notebook loses its wireless connection and is unable to regain it automatically. If I manually click on the Network Manager tray icon and click my wireless connection, Network Manager will disconnect and reconnect and the wireless will work again. I'd really like to automate this process so I don't have to be around to keep the notebook on the network.

If I run sudo ifdown wlan0 (which is the interface name...I've verified it with ifconfig), I get "Ignoring unknown interface wlan0=wlan0."

If there is no other option, I could try writing a Python program to use D-Bus to talk to Network Manager. But surely there is already a command for doing this. I just haven't found it yet.

---

### Post by lisati on 2010-01-22
The best I can come up with at the moment is:
```
sudo /etc/init.d/networking restart
```

---

### Post by Axos on 2010-01-22
Looking in /etc/network/interfaces on my system, the only interface ifup/ifdown knows about is the local (loopback) interface. I think Network Manager is in charge of everything else.

---

### Post by fabien77 on 2010-01-25
sorry for late but I have some problems in these days.
 
axos, linati and Zugzwang: ifup/down or networking command cannot work, this is because ppp0 (or wlan0, or what you want) doesn't exist if it is disconnected from internet (IMHO, "Ignoring unknown interface ppp0=ppp0" was my ifconfig message).
 
It seems that the solution is to install cnetworkmanager that should be a command line "supplement to network manager". 
 
[http://vidner.net/martin/software/cnetworkmanager/](http://vidner.net/martin/software/cnetworkmanager/)
 
I'don't know when I can try this, anyway if someone can tell us how install and use for restart connections (ppp0, wlan0, etc...), it will be great!!! I couldn't spent any time on this but I noted that informations on it are poor,
 
does someone know this program?
 
 
bye

---

