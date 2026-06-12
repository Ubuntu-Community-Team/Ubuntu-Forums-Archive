---
title: "General WiFi Networking Questions"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by lesterbolen on 2008-10-02
X

---

### Post by superprash2003 on 2008-10-02
1)in your terminal type ifconfig and you should get an output.. see which interface has an ip of the form 192.168.1.x or 192.168.0.x , that would be the one connected to your cable modem..
2)Probably because you have two wifi adapters.. or you have a virtual interface..
3)These are mostly interfaces and unless you have shared the internet connection to those interfaces and setup a adhoc network, you shouldnt worry..
4)Well theres no harm in setting up a firewall.Additional security..

---

### Post by lesterbolen on 2008-10-02
x

---

### Post by superprash2003 on 2008-10-03
1)yes ath1
2)Please post output of lshw -C network and iwconfig to know more about your setup
3)Its not shared by default, so if you havent done it, then you dont have to worry..

---

