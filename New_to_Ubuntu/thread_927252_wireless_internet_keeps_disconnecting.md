---
title: "wireless internet keeps disconnecting"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by duquer on 2008-09-22
my wireless keeps connecting and disconnecting.in didnt do this before if anyone can help me it would be appreciated?

---

### Post by willca on 2008-09-23
Hi

When you get disconnected, does it get connected right away and it works ( i mean you can browse and all?).

Is this wifi network at home? Perhaps you have other neighbors running wifi too nearby and you are overlapping on the channel they use?

I would check who else is in the vicinity. 

sudo iwlist wlan0 scan
wlan0 if thats what is your Ubuntu using or eth1 maybe.
check if anybody else uses the same channel as you are.

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
tail /etc/var/messages
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

### Post by computx on 2008-09-23
> You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:


```
sudo ifdown wlan0
sudo ifup wlan0
```

You may diagnose the network adapter status with commands:
Code:

```
ifconfig
iwconfig
dmesg
tail /etc/var/messages
```



I think you meant to say /var/log/messages.
also the wlan0 may be another name such as wifi0 or ath0 depending on the adapter you use. run iwconfig by itself to discover the port used for wireless.

---

### Post by duquer on 2008-09-23
when my computer loses signal, all the computers in the house still have signal. i can still play my xbox online with no interuptions or disconnection. when it happens it doesnt show a disconnection right away i will go to the browser first try to go to a different web site or try to download something off of frostwire and then it will disconnect and after 10 or 15 seconds it will reconnect. we just had comcast come to my house and to a signal boost so i doubt is a problem with the modem..

---

