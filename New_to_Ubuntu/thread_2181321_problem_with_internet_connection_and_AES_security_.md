---
title: "problem with internet connection and AES security system"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by cristina2 on 2013-10-17
Hi everybody! :D
I'm new in this forum and I have a problem with the internet connection that I'm really not able to solve.
I have lived in two places, where they have the same internet security - I need to connect to a hidden network and then connect via PPPoE . In  one place it works perfectly, in the second place I can't connect  with the hidden network, and I know that the only thing that is different is that in the second place there is an AES security system.
Anybody know how should I have to do?

Thank you in advanced for any help ;)


my wireless card:   *-network                       description: Wireless interface        product: AR9285 Wireless Network Adapter (PCI-Express)        vendor: Atheros Communications Inc.

---

### Post by K7AAY on 2013-10-17
PPPoE is for DSL.
You use a DSL type connection, right?

Security systems often block DSL from working, since they are typically wired between the demarc (where the phone line enters the house or flat) and the DSL router. When connected like that, they can reduce the high-frequency radio-band signal on the phone line which carries your DSL. 

If the security system is bypassed, does the DSL then work OK?

---

### Post by cristina2 on 2013-10-24
I'll try to explain my situation a little bit better ;)
The case here is the dorm I live in. The system works as follow: You connect to a wireless and then using &#8220;sudo pppoeconf wlan0&#8221; and after making some changes in /etc/network/interfaces and local IP table you can connect to the internet using &#8220;sudo pon dsl-provider&#8221;. This has worked for me in a twin-dorm with similar system and works here for other people. But now, I cannot finish the 1st step - I cannot connect to the wireless - it keeps disconnecting me.

---

