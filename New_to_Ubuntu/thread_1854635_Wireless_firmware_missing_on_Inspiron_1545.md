---
title: "Wireless firmware missing on Inspiron 1545"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by shayne_helms on 2011-10-04
Ok guys, I'm new with Ubuntu. I have viewed other posts about this issue and none seem to help me. A friend fully booted Ubuntu 11.04 onto my computer and I need it for it's wireless capabilities, which are now not working. It has a dell 1397 wlan mini-card. I can't hardwire it to my router or take it to a friends. I'm on a dial-up connection at the moment but can download files to a flash drive and transfer them over to the laptop as needed. If anyone can help, it would be much appreciated. Thank you.

---

### Post by wolfen69 on 2011-10-04
Post the output of:
```
lspci
```

---

### Post by shayne_helms on 2011-10-05
I can't copy the whole thing, as I am on a different pc. What I am assuming you need is Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by wildmanne39 on 2011-10-05
Hi, I believe the easiest thing to do is to download this zip file onto a flash drive then drag it to your ubuntu desktop, unplug your modem or wired connection,then Right-click it and select Extract Here. 

Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
one line at a time and if you have not installed any other drivers it should come on.
Thank you

---

### Post by shayne_helms on 2011-10-11
Sorry I haven't said anything about the results. It worked though. Thank you so much for your help!

---

### Post by wildmanne39 on 2011-10-11
Hi, that is great, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

