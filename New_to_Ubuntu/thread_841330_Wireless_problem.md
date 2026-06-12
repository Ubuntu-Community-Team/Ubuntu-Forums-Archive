---
title: "Wireless problem"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by rawtin on 2008-06-26
Hi there.  I'm fairly new to Ubuntu.  I have a HP laptop with a broadcom BCM94311 wlan card.  I have the driver file installed, and was able to extract the firmware from the driver.  Now, the connection is found and the strength is displayed yet when I open Firefox it cannot connect.  Any ideas?

---

### Post by cmnorton on 2008-06-26
1) Open up an X-term (command line), and type ifconfig.

Part of the output should look similar to this:

eth1      Link encap:Ethernet  HWaddr 00:50:B6:01:7C:C8
          inet addr:192.168.1.4  Bcast:10.100.255.255  Mask:255.255.0.0
          inet6 addr: fe80::250:b6ff:fe01:7cc8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12826637 errors:18 dropped:0 overruns:0 frame:18
          TX packets:20530899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:270798394 (258.2 MB)  TX bytes:3232462793 (3.0 GB)

Don't worry this is showing eth1. I have a different configuration for my laptop. It could easily be eth0 or something else.

2) If your inet addr: is 192.168.1.4, your router is probably 192.168.1.1. Try pinging that.

3) Then, try to ping a known address outside your router. Your ISP service provider would be a good start.

---

### Post by dca on 2008-06-26
..also make sure there are no settings under 'System -> Administration -> Network' relative to your ethernet card, like the DNS settings and such.

---

### Post by rawtin on 2008-06-26
The settings are correct.  I can connect sometimes.  Then it will just lose connection I will have to restart the system.

---

### Post by flytripper on 2008-06-26
haha welcome to my world. dropping wireless :(

go cable whenever possible

---

### Post by dca on 2008-06-26
The only time I've seen that happen is when you have two styles of driver for the same component.  IE:  you have an Atheros chipset-based WiFi NIC that you're using ndiswrapper & the windows driver PLUS the 'madwifi' & kernel packages with...

---

### Post by rawtin on 2008-06-26
I ran iwconfig for eth0.  It came up no wireless connectios.  I then ran iwconfig for wlan0 and it came up with settings.  is this a problem?

Sorry about the double post.

---

