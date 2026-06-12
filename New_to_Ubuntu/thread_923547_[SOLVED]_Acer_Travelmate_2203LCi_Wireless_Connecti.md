---
title: "[SOLVED] Acer Travelmate 2203LCi Wireless Connection"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by getitright on 2008-09-18
Hi,

I have installed Ubuntu 8.04 0n an Acer TravelMate 2203 LCi. The prolem is that that I cannot connect wirelessly. Left clicking on the Wired network connection then selecting Manual connection brings up the Network Settings box, but there is no Wireless Connection option. Can anyone help please?

---

### Post by milky2313 on 2008-09-18
Do you know what kind of wireless card you have? It's all going to depend on that...

---

### Post by getitright on 2008-09-18
Do not know what wireless card is installed.

---

### Post by milky2313 on 2008-09-18
You might be able to figure it out by looking up your machine on the Acer website. If you still have windows installed on your machine, you can look up your wireless driver in the device manager. I'm sure there is a way to do this in ubuntu as well, but I'm not sure how. Maybe someone else can help with that. If your wireless card is a Broadcom, I have some experience with those and I might be able to help. If not, I probably can't do you much good.

---

### Post by getitright on 2008-09-18
Thanks. Do not have Windows, but found this in Ubuntu "Inprocomm IPN 2220 Wireless LAN Adaptor". Could this be the wireless card?

---

### Post by milky2313 on 2008-09-18
Yes, that is the wireless card. Unfortunately, I am completely unfamiliar with this type of card.  Hopefully someone else will pass by that has more experience...

Until then, maybe you can get a little more information about whats going on. Try going to Administration > Network. Does it show a wireless network connection in the list.

Also try this command:
```
iwlist scanning
```
It should give you a list available networks in range. If it gives you some sort of error, you could post it and see if anyone knows what it means.

---

### Post by getitright on 2008-09-19
Thanks.

No network identified.

After further investigation it looks like I need to install the Windows driver, within a ndiswrapper, for the driver. Ndiswrapper is not installed. Have down loaded files for the driver and Ndiswrapper, what is the procedure for installing these?

---

### Post by milky2313 on 2008-09-19
Check out the instructions on this website:
[URL="http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html"]
http://www.ubuntu1501.com/2008/04/ndiswrapper-in-hardy-heron.html[/URL]
The instructions are actually for a broadcom card on a dell machine, but the process for ndiswrapper should be the same for you. If you already have your driver files ready, you can skip step three.

I use ndiswrapper on my machine and it works great. Just make sure you make the wirelessfix.sh script as described in step 1. This is needed for the ndiswrapper module to load correctly.

You should be able to test out your wireless without restarting by running the script:
```
sudo /etc/init.d/wirelessfix.sh
```

At this point your wireless light should come on(if you have one)
then do ```
iwlist scanning
``` to test it out.

hope this helps. let me know if it doesn't work because i do know of one more way to do it...

---

