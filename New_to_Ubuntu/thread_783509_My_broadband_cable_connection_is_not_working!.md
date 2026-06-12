---
title: "My broadband cable connection is not working!"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Fixman on 2008-05-05
I have Ubuntu Hardy, and I used internet perfectly. However, I changed my computer (and conserved the hard drive), and now, after fighting a little with my Ubuntu (lucky for me, my Windows partition doesn't even work), I can't connect ti the internet. I tried using roaming mode (what I used before), static IP address, and DHCP, but it still doesn't work. I know that I am connected to the internet because I have 2 computers connected to a router, and the second one works. Here is my ifconfig:

Code:

eth1    Link encap:Ethernet HWaddr 00:1e:8c:14:0b:7d
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:10 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 frame:0
        collisions:0 txquelen:1000
        RX bytes:1638 (1.5KB) TX bytes:0 (0.0 B)
        Interrupt: 80 Base address:0xdead

lo      (loopback interface goes here, Im too lazy to copy it)

Note that I copied this from another screen, so there can be an error. Does anyone know what this can be?

BTW, I have an ethernet broadband cable connection.
EDIT: Internet doesn't even work from the Live CD!

---

### Post by gilda on 2008-05-05
can you ping the router at all ?

---

### Post by hariprs on 2008-05-05
It seems there is no IP for your card.
What IP you assigned to your LAN card?
Do you know how your second computer gets IP(Static or DHCP)?

---

### Post by lemming465 on 2008-05-05
Have you tried power-cycling your router?  Sometimes they get confused about the clients.  Also, if you are still having trouble, post ```
cat /etc/network/interfaces
```

---

### Post by aonegodman on 2008-06-05
I have the same problem, no broadband detection via Ubuntu. Now I have to use my laptop with Windows XP to access internet. Without internet connection Ubuntu Linux has had to take a back seat to my Windows based laptop. So . . . my question is this, is there not a Ubuntu based trouble-shooting program that will check out my desktop and tell me why or what I need to do to fix this?

I've tried changing all the settings mentioned in original post, I've even tried installing a second 10/100 net PCI Ethernet Card incase my onboard was blown out. Not that. Ubuntu sees both Ethernet ports, but it can't sense or see my cable broadband connection. Yes, I changed out cables, used the same cable going to my laptop that works fine.

Now I have HS cable from Charter, my connection is simply direct from cable modem to my Ethernet port, no router, hard wired.

I'm running Ubuntu 7.10 with updates up to, but not, Heron.

How about some of you cable guys giving a hint?

Please don't suggest calling Charter, they only support Windows and Mac computers in the support department and have no clue when you tell them your running Ubuntu Linux. Besides that, they have a strong dialect and are very hard to communicate with verbally.

:(

---

### Post by stchman on 2008-06-05
> **aonegodman said:**
> I have the same problem, no broadband detection via Ubuntu. Now I have to use my laptop with Windows XP to access internet. Without internet connection Ubuntu Linux has had to take a back seat to my Windows based laptop. So . . . my question is this, is there not a Ubuntu based trouble-shooting program that will check out my desktop and tell me why or what I need to do to fix this?

I've tried changing all the settings mentioned in original post, I've even tried installing a second 10/100 net PCI Ethernet Card incase my onboard was blown out. Not that. Ubuntu sees both Ethernet ports, but it can't sense or see my cable broadband connection. Yes, I changed out cables, used the same cable going to my laptop that works fine.

Now I have HS cable from Charter, my connection is simply direct from cable modem to my Ethernet port, no router, hard wired.

I'm running Ubuntu 7.10 with updates up to, but not, Heron.

How about some of you cable guys giving a hint?

Please don't suggest calling Charter, they only support Windows and Mac computers in the support department and have no clue when you tell them your running Ubuntu Linux. Besides that, they have a strong dialect and are very hard to communicate with verbally.

:(

I have Charter high speed as well and it works perfectly with Ubuntu.

You can connect the output of the modem directly to the network card.

What kind of wired ethernet card do you have in your PC?

---

### Post by tedrogers on 2008-06-05
My advice:

1. Turn off your router and modem, wait 1 minute. Turn the modem on first, wait 1 minute, then turn on the router last.

2. Try using a wired connection directly to the router.

3. If this fails, try using a wired connection directly to the modem. You may need to turn your modem on and off again.

4. Try getting access to your router by typing [http://192.168.1.1](http://192.168.1.1) into the address bar of your internet browser (in Ubuntu). This will prove communication with router.

5. Try getting access to your modem by typing [http://192.168.100.1](http://192.168.100.1) into the address bar of your internet browser (in Ubuntu). This will prove communication with modem.

6. Backup your partition using wieman01's excellent guide at [http://ubuntuforums.org/showthread.php?t=287522](http://ubuntuforums.org/showthread.php?t=287522) and then wipe everything and try a fresh install.

Google is your friend as well...you can find a lot of help if you look hard enough...but it does require effort on your part.

Good luck.

---

