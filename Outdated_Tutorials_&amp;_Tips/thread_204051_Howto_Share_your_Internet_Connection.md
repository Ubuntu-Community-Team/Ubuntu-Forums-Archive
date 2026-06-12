---
title: "Howto: Share your Internet Connection"
date: 2006-06-26
forum: Outdated Tutorials &amp; Tips
---

### Post by anarhistu on 2006-06-26
Ok, this is how I did it, the most simple way:

I used tinyproxy as a simple to use, lightweight and small proxy solution
```
apt-get install tinyproxy
```

It's in the Universe package list, so it should be easy

Then:

Assuming you have got an internet connection available and you want to share with a network thet connects through one of the network cards on your computer.

First, do an ifconfig and see the IP on which you want to put your proxy to listen to.
In my case it's 192.168.147.1 , set on a second card in my computer.

Edit your /etc/tinyproxy.tinyproxy.conf:

```
sudo nano /etc/tinyproxy/tinyproxy.conf
```

Do this:
Choose a port to listen on
```
#
# Port to listen on.
#
Port 2000
```

Bind to a certain interface in your computer
```
#
# If you have multiple interfaces this allows you to bind to only one. If
# this is commented out, tinyproxy will bind to all interfaces present.
#
Listen 192.168.147.1
```

Allow certain network computers to connect: ad their IP-s one by one:

```
# Also the order of the controls are important. The incoming connections
# are tested against the controls based on order.
#
Allow 127.0.0.1
Allow 192.168.1.0/25
Allow 192.168.147.2
```

Add yahoo messenger connection possibility:
```

# This is a list of ports allowed by tinyproxy when the CONNECT method
# is used.  To disable the CONNECT method altogether, set the value to 0.
# If no ConnectPort line is found, all ports are allowed (which is not
# very secure.)

ConnectPort 5050
```

Then restart (or start) tinyproxy
```
$sudo /etc/init.d/tinyproxy restart
```

---

### Post by DaveNF2G on 2006-07-06
I didn't have to do anything to get Ubuntu to share the connection.

I installed in dual-boot mode to a Windows 98SE box that was connected to a cable modem via cable router.  Ubuntu recognized whatever it needed to see for the RoadRunner connection and the computer shares it with the other computers in my apartment in exactly the same way as it does under Windows.

---

