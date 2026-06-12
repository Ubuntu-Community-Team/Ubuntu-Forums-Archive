---
title: "Problem with reinstall"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Drejcek on 2008-09-06
Hi,
I'm using ubuntu about 7 months now. Few days ago my friend ask me to get new OS on his laptop (no metter witch one). So I decide to install Ubuntu. Well it was quite strange when laptop didn't want to reset by itself. When I run it again Ubuntu started normally but it didn't want to connect to network. First I tried Wireless it didn't work, then I tried wired connection, nothing happend. I disconnected my PC and try cable from it. Nothing happend again. 

Then I tried "ifconfig" in terminal and got this: 
```
eth0 Link encap:Ethernet HWaddr 00:0f:b0:c3:3f:9a
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:1060 errors:0 dropped:0 overruns:0 frame:0
TX packets:1060 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:53000 (51.7 KB) TX bytes:53000 (51.7 KB)

```
I didn't understand this (I'm not expert in Ubuntu yet) so I tried to reinstall Ubuntu. I got ubuntu CD in, restart laptop, start installation and this error made: 
```
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
Buffer I/0 error on device hdc, logical block 34513
SQUASHFS error: sb_bread failed reading block 0x1053c
SQUASHFS error: Unable to read page, block 4145e4f, size 945d
SQUASHFS error: sb_bread failed reading block 0x1053c
SQUASHFS error: Unable to read page, block 4145e4f, size 945d
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
Buffer I/0 error on device hdc, logical block 34513
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
SQUASHFS error: sb_bread failed reading block 0x1053c
SQUASHFS error: Unable to read page, block 4145e4f, size 945d
SQUASHFS error: sb_bread failed reading block 0x1053c
SQUASHFS error: Unable to read page, block 4145e4f, size 945d
```
... over and over again
There were some numbers in front of each line (somekind of timestamps) and i couldn't copy them. I got my laptop next to friend's and write everything on screen. Well I took CD out and restart laptop. It started normally, came to Ubuntu but still couldn't connect to network through wireless. My ISP set my modem to find computers, so my laptop connect by itself without my help, and PC is same, I just turn them on. But this friend's laptop just don't work. I hope you can help me, I really don't know what to do.

---

### Post by Drejcek on 2008-09-06
Nobody knows what's wrong?

---

### Post by mikewhatever on 2008-09-06
There seems to be a problem with the device Ubuntu named hdc. Try figuring out what it is and disconnect it. Try disconnecting any peripherals such as external HDDs, printers, etc.

---

### Post by sanemanmad on 2008-09-06
> **Drejcek said:**
> 
```
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
Buffer I/0 error on device hdc, logical block 34513
SQUASHFS error: sb_bread failed reading block 0x1053c
SQUASHFS error: Unable to read page, block 4145e4f, size 945d
SQUASHFS error: sb_bread failed reading block 0x1053c
SQUASHFS error: Unable to read page, block 4145e4f, size 945d
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
Buffer I/0 error on device hdc, logical block 34513
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
hdc: error code: 0x70 sense_key: 0x03 asc: 0x11 ascq:0x00
SQUASHFS error: sb_bread failed reading block 0x1053c
SQUASHFS error: Unable to read page, block 4145e4f, size 945d
SQUASHFS error: sb_bread failed reading block 0x1053c
SQUASHFS error: Unable to read page, block 4145e4f, size 945d
```


Hi Drejcek ~ 

The errors you are receiving indicate the 'medium' you are using may be corrupt. This has happened to me before when installing ubuntu 8.04 LTS. I would recommend using a new copy of ubuntu.

---

### Post by Drejcek on 2008-09-06
I created new copy of Ubuntu and it works for now. I didn't finish yet, but I hope this time everything will works.

---

### Post by Drejcek on 2008-09-06
Well this worked. But now to my next problem. I can't connect to internet. Friend's laptop is now in LAN with my laptop, is there any way to connect through laptop to internet. I have Ubuntu, and friend got it too now ;)

EDIT: I get it work. THX for help everyone

---

### Post by Drejcek on 2008-09-06
Well I have new problem. So I won't open new topic. I upgraded Ubuntu and when i wanted to install samba or anything else from terminal I got this:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

What should I do?

---

### Post by pbotros1234 on 2008-09-06
> **Drejcek said:**
> Well I have new problem. So I won't open new topic. I upgraded Ubuntu and when i wanted to install samba or anything else from terminal I got this:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

What should I do?
That happens when you have one package manager already working, and then you try to install something else with another. Like if you have synaptic open, and then you try to apt-get install something, then you get this message. Just close one or the other :)

---

