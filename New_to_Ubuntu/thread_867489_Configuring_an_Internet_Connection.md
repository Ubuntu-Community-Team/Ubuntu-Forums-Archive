---
title: "Configuring an Internet Connection"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by caleb.gross on 2008-07-22
So recently Windows crashed on my HP notebook and Im using a CD that I previously installed Ubuntu on. Im in the demo mode, so I havent actually created a partition on the hard drive and installed the OS on it. Im trying to connect to the wireless network we have running but the card (Broadcom B43) doesnt work with Ubuntu. The [solution]("http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/") Ive found requires me to access the internet, which Im assuming is through a wired connection. I have the laptop directly wired to the internet but I dont know how to configure it. Anybody have any clue how to get me where I want to go with this

---

### Post by bukwirm on 2008-07-22
Open a terminal, type ifconfig. That should give you a list of network interfaces. Figure out which one is your wired connection, then type sudo ifup *interface_name*.

If that doesn't work, tell us the output.

Note that the wireless solution you linked to will probably require you to actually install Ubuntu first.

---

### Post by dhughes on 2008-07-22
If eth0 is the designation of your card, and say your router is 192.168.1.1 giving your PC an IP address of 192.168.1.2 then try:

```
sudo ifconfig eth0 192.168.1.2 netmask 255.255.255.0 up
```

 then maybe, restart the network

```
sudo /etc/init.d/networking restart
```

 The Networking and Wireless forum has a nice howto stickied on manually setting up a network.

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

