---
title: "USB modem installation"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Caspian_pegasus on 2008-08-08
:guitar: hey dudes, i'm really new to linux and ubuntu in particular. so far its been going well and now I've run into a couple of problems.

I don't know how to access USB devices. I've bought a usb internet dongle. but i can't install it or use it as it does not show up any where. can anyone help?

also, is firefox meant to not have a preferences option on ubuntu? how am i meant to make any modifications to it then?

ah, and also how do i de/activate the firewall (open or close ports) 

thanks,

Caspian

---

### Post by halitech on 2008-08-11
not sure I know what you mean by "usb internet dongle"? do you mean a usb wireless adapter or is it for plugging in a wire to go from your computer to a router/modem?

with the device not plugged in, open a terminal (Applications - Accessories - Terminal) and type in ```
lsusb
``` then plug it in and do the same and see if there is anythign different. post the info here and we'll see what we can do to help.

---

### Post by amoun on 2008-08-11
Preferences is under Edit rather than Tools as in the Win version. :)

---

### Post by london rain on 2009-08-23
Hi there.. I'm also new to Ubuntu and I haven't been able to access internet with my USB Modem.

I'm using Zoom X4. Here is what I came up with "lsusb".

```
root@londonrain-netbook:/home/londonrain# lsusb
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1803:5551  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
root@londonrain-netbook:/home/londonrain# lsusb
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hu
```

---

### Post by marshmallow1304 on 2009-08-23
> **amoun said:**
> Preferences is under Edit rather than Tools as in the Win version. :)

That was my first crisis when I started using Ubuntu. :)


> **Caspian_pegasus said:**
> ah, and also how do i de/activate the firewall (open or close ports)

Use gufw.
```
sudo apt-get install gufw
```

---

### Post by london rain on 2009-08-24
Anybody?

---

### Post by halitech on 2009-08-24
I'm assuming that this
[color="red"]Bus 003 Device 002: ID 1803:5551 [/color]
is the modem but it doesnt look like Ubuntu is getting any info on it.

is this a Dialup USB modem or a highspeed (ADSL) modem?

---

### Post by london rain on 2009-08-24
I have got Zoom X4 (5551)

---

### Post by halitech on 2009-08-24
> **london rain said:**
> I have got Zoom X4 (5551)

again I ask, is this a dialup modem or an ADSL highspeed modem?

---

### Post by london rain on 2009-08-24
ADSL High Speed.

---

### Post by halitech on 2009-08-24
do you have a NIC in your computer? if you do, use that to connect instead of the usb connection

---

### Post by 3rdalbum on 2009-08-24
> **Caspian_pegasus said:**
> :guitar: hey dudes, i'm really new to linux and ubuntu in particular. so far its been going well and now I've run into a couple of problems.

I don't know how to access USB devices. I've bought a usb internet dongle. but i can't install it or use it as it does not show up any where. can anyone help?



Mobile broadband devices do not show up on your desktop, because they are not storage devices.

Try going to the Network Manager applet (towards the right-hand side of your top panel), right-click, go to Edit Connections and set it up there.

> ah, and also how do i de/activate the firewall (open or close ports) 

Unless you've been setting up server software like Apache (you know, software that listens to incoming connections rather than just making outgoing connections) you don't need a firewall. You can set one up in Ubuntu using the gUFW package, but there's nothing in a default Ubuntu install that listens to incoming connections.

---

### Post by hasanthika on 2009-11-06
i think u r talking about usb modems. 
if so you will find the answer here.

[SIZE=2][COLOR=Navy]http://nixcraft.com/ubuntu-debian/12020-usb-modem-ubuntu.html[/COLOR][/SIZE]

---

### Post by killingspree on 2010-08-06
> **hasanthika said:**
> i think u r talking about usb modems. 
if so you will find the answer here.

[SIZE=2][COLOR=Navy]http://nixcraft.com/ubuntu-debian/12020-usb-modem-ubuntu.html[/COLOR][/SIZE]
thanks, i was having this problem too

---

