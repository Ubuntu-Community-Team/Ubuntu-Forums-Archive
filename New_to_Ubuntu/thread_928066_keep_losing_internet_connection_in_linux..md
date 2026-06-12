---
title: "keep losing internet connection in linux."
date: 2008-09-23
forum: New to Ubuntu
---

### Post by misswham on 2008-09-23
I started losing internet connection yesterday but have been having a few problems with the connection running slow anyway. I looked up and saw the connection icon that looks like 2 tvs and it was searching for internet address.  it would circle and stop and start searching again.  So today it did it over again.  I have rebooted and it seems to be ok now.  What does this sound like could be happening?  I havent changed anything on my pc.

---

### Post by Korijn on 2008-09-23
Can you give us some details? Like, do you have a router in your home network? Is your internet wireless or wired? If it's wireless, is your computer far away from your router?

Regardless, please open up a terminal window and type the following:
```

sudo ifconfig

```
and then copy & paste the result here.

Hopefully I'll be able to help you out a bit better with that info. :)

---

### Post by Crafty Kisses on 2008-09-23
You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```
sudo ifdown wlan0
sudo ifup wlan0
```
You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
/var/log/messages
```
I also want to see the results of this command:
```
lshw -C network
```

I'm thinking it could also be packet loss, it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

---

### Post by twitch2197 on 2008-09-23
my computer does that sometimes too. it's trying to assign an ip address to your computer from the router. a reboot, or even a logoff/login, usually fixes it for me.

---

### Post by misswham on 2008-09-23
this is the result from sudo ipconfig

eth0      Link encap:Ethernet  HWaddr 00:19:21:02:c1:9c  
          inet addr:192.168.15.100  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::219:21ff:fe02:c19c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7501 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6049269 (5.7 MB)  TX bytes:1720513 (1.6 MB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:297 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14844 (14.4 KB)  TX bytes:14844 (14.4 KB)


i am using a linux router but i am on a wired connection from comcast.  my pc is a gateway.  this just started happening 2 days ago.

---

### Post by misswham on 2008-09-23
sorry not linux router and linksys router with a cable modem but not using wireless when it happens.

---

### Post by Korijn on 2008-09-24
Right now I'm thinking it might be the fact that you don't have a static IP. If you could provide me with a little more data I can help you out. Please copy & paste the contents of the file /etc/network/interfaces by typing the following command in the terminal:

```
gksudo gedit /etc/network/interfaces
```

It says in the result of your ifconfig that there have been no errors or packets dropped. So interference probably isn't an issue, especially since you are on a wired connection.

You could also run all the commands Codename suggested. They all provide incredibly useful feedback.

---

### Post by misswham on 2008-09-25
i put that last command in and it asked for my password and then it took me to another page and it only had a few words at the top and when i went to close it it asked me if i wanted to save the past 2 minutes so i sure didnt know what that was.

---

