---
title: "firestarter"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by hellomoto on 2008-07-16
hello,
      Im trying to share my internet between 2 PC's one running ubuntu the other xubnutu.

Here is how I would like them conneted:

Wlan0 (internet)> Ubuntu PC routes connection to> eth0> eth0 Xubuntu

I have tryed using firestarter but am getting errors: please see the screen shots: 
1 of ubuntu PC
1 of xubuntu PC

any ideas how to solve this problem?

Thank you.

---

### Post by Archmage on 2008-07-16
As far as I see this, you don't have a fixed IP-Adresse for eth0. Change this in the network configuration.

---

### Post by hellomoto on 2008-07-16
would i assign that on the ubuntu machine (the one routing the connection)?

Am i correct in thinking i could assign a fixed IP for eth0 in network settings? 

One last Q: What IP should I assign to eth0?

---

### Post by phantomjoker on 2008-07-16
assign your IP from Wlan0 to Etho.. 
Assign a static IP address on both machines and set it up with your internet by typing your IP into the address bar on your web browser and then going into virtual servers.

does this help a little?

---

### Post by hellomoto on 2008-07-16
I have assigned Ip address to both computers eth0 connections and they can ping each other but thats it.

I tried putting into my browser the IP my router has asigned for my wlan0 connection but that didn't seam to help.

Please see the enclosed screen shot from trying to start firestarter now.

---

