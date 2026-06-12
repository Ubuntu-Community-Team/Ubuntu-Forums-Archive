---
title: "Intel® PRO/Wireless LAN 3945ABG"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by mike4life on 2008-08-28
Hi,
 
Before i install or anything, i was just wondering if it is possible to go wireless with ubuntu using my Intel® PRO/Wireless LAN 3945ABG wireless card ? :S
Ive never used terminal before or got much experience with ubuntu tbh either! lol
 
 
 
Mike. [x]

---

### Post by oilchangeguy on 2008-08-28
> **mike4life said:**
> Hi,
 
Before i install or anything, i was just wondering if it is possible to go wireless with ubuntu using my Intel® PRO/Wireless LAN 3945ABG wireless card ? :S
Ive never used terminal before or got much experience with ubuntu tbh either! lol
 
 
 
Mike. [x]

run the computer from the live cd, to see if it works.

---

### Post by mike4life on 2008-08-28
> **oilchangeguy said:**
> run the computer from the live cd, to see if it works.
Hi,
 
Is is still possible to install drivers for hardware whilst running the Live CD, 
And also how ywould i go about connecting to a network wirelessly?
(I have the 8.04 Live Disc)
 
 
Mike. [x]

---

### Post by anotherdisciple on 2008-08-28
I have that exact card... It works very well... never had a problem with it. Hope that helps.

---

### Post by laurence91 on 2008-08-28
I have this exact card, the card is already installed on the latest release 8.04 that i have.

you can set up the connection automatically using the preinstalled apps, or if you prefer, there is a way to check the drivers are installed at least through the terminal

if you type....
$ lshw

the output will list the card details among other things,

$ lwlist
should scan for routers, although its much easier to just use the GUI to set up your network with modern connections (such as work connections etc) its called Knetwork manager on kubuntu if that helps.

Cheers
Laurence

---

### Post by mike4life on 2008-08-28
> **anotherdisciple said:**
> I have that exact card... It works very well... never had a problem with it. Hope that helps.
How did you get it to install? or was it simply boot the OS and away you go?
and how also would you go about connecting to the Wireless Router? :S
 
I must sound like a rite noob! lol
 
 
 
Mike [x]

---

### Post by mike4life on 2008-08-28
> **laurence91 said:**
> I have this exact card, the card is already installed on the latest release 8.04 that i have.

you can set up the connection automatically using the preinstalled apps, or if you prefer, there is a way to check the drivers are installed at least through the terminal

if you type....
$ lshw

the output will list the card details among other things,

$ lwlist
should scan for routers, although its much easier to just use the GUI to set up your network with modern connections (such as work connections etc) its called Knetwork manager on kubuntu if that helps.

Cheers
Laurence
I really dont understand how to use command prompt in ubuntu, or how do i connect to the network? :S
 
Click on the network icon yeah? or is that simply for wired connections? :S

---

### Post by oilchangeguy on 2008-08-28
> **mike4life said:**
> I really dont understand how to use command prompt in ubuntu, or how do i connect to the network? :S
 
Click on the network icon yeah? or is that simply for wired connections? :S

you're making life to hard. simply run the live cd. you'll see the network icon in the top panel. click on it and select your connection type. then connect to your network.

---

### Post by mlentink on 2008-08-28
The  Intel® PRO/Wireless LAN 3945ABG is buitl in to my HP Compaq nx7400. It worked out of the box, no need to install drivers etc.

---

### Post by Nepherte on 2008-08-28
> **mike4life said:**
> Hi,
 
Before i install or anything, i was just wondering if it is possible to go wireless with ubuntu using my Intel® PRO/Wireless LAN 3945ABG wireless card ? :S
Ive never used terminal before or got much experience with ubuntu tbh either! lol
 
 
 
Mike. [x]
The open source driver iwl3945 for your wireless card is included in Ubuntu. Your wireless card should be recognized both while running the live cd and after installing Ubuntu. I have the same wireless card on a sony (see signature) and it worked right away.

---

### Post by mewithafez on 2008-08-28
Works for me! Using Gateway CX210X and the wireless has always worked in ubuntu, whatever version I was using.

---

### Post by laurence91 on 2008-08-28
Yes, sorry to confuse, oilchangeguy is right in that dont worry about setting up the network card. In 8.04 its already done if not in other releases too.

It should work on the live cd, mine did.

Should you wish to learn a little more about networks in ubuntu try this link out.

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

If there's one think iv learnt about linux its read twice and reinstall once......
Laurence

---

