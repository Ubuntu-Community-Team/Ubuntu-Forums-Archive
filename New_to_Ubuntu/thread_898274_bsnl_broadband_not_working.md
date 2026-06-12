---
title: "bsnl broadband not working"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-08-23
hi, can you help me?
i live in india
i have got windows and ubuntu in dual boot in my pc(i installed it through wubi). recently i got a bsnl broadband connection. in windows i am able to work in internet where as in ubuntu i cant. i tried sudo pppoeconf command but it is showing some error. what can i do.
I use UT300R2U router given by BSNL. Those 4 lights(power,dsl,internet,ethernet) in the modem are glowing when i am working in windows and ubuntu. internet is working when i work in windows. but when i go to ubuntu and typed sudo pppoeconf, it is detecting but it says some error like 'not able to configure etho concentrator...or something like that...' what shall i do

---

### Post by livestockPimp on 2008-08-23
well first of all, pppoeconf is used for if the modem is in bridge mode in this case the internet light will not be lit ever on the router.

try using "sudo dhclient eth0" providing your router has dhcp setup this should work.

---

### Post by lisati on 2008-08-23
What output do you get when you do ```
ifconfig
```

---

### Post by luckydeveloper on 2008-08-23
whats the difference between bridge mode and the mode i have.

---

### Post by aloshbennett on 2008-08-23
From windows, how do you connect to bsnl? Do you use a pppoe dialer?
And whats the error you are getting when you try to run pppoeconf?

---

### Post by livestockPimp on 2008-08-23
The difference between bridge and pppoe mode on the modem is one of them the modem connects to the internet, the other method the modem is purely a modem and does not connect to the net, instead it allows the PC to send the username and password through it. if you configured the modem through a web browser and entered your username and password here then you do not want to use pppoeconf here. If you have an internet connection that you "dial" in windows to connect the connection then you use pppoeconf.

I am assuming you do not need pppoeconf since I have never seen a modem hold the internet light on in bridge mode since the PC is holding the connection.

To get the internet to work all you should need to do is setup the network card and your "resolve.conf" where the DNS servers are.

---

### Post by luckydeveloper on 2008-08-23
it worked.. thanks. what did that command do...  sudo dhclient eth0         please explain

---

### Post by livestockPimp on 2008-08-23
dhclient simply requests a DHCP lease from a DHCP server.

basically it says:

I need to be configured with an ip address, netmask, default gateway, DNS servers, ect.

the modem responds and sends the configuration data to you.

---

### Post by ashwinhgtx on 2009-11-12
I'm using a dialer in Windows to get my bsnl connection. So I'm assuming that my modem is in bridge mode.
I configured using pppoeconf and I do get a connection.

But the connection drops out randomly after 2 or 3 min.

I have to restart the connection to use it. How do I fix this?

The internet light on my modem glows even though it is in bridge mode. Is something wrong?

---

### Post by GIRI MURALI on 2010-07-03
Ubuntu can detect broadband itself if your modem in bridge state.If you want to connect it in pppoe mode please follow this tutorial 
[http://www.beubuntu.co.cc/2010/06/how-to-connect-bsnl-broadband-in-linux_27.html](http://www.beubuntu.co.cc/2010/06/how-to-connect-bsnl-broadband-in-linux_27.html)

---

