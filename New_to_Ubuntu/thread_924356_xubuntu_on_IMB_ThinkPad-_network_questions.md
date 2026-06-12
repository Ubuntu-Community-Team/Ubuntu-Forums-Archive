---
title: "xubuntu on IMB ThinkPad- network questions"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by pstrbrc on 2008-09-19
Computer: 
IBM ThinkPad, 500mHz, 320mb RAM, no network port, has USB port, has two pci ports (will allow me to plug in my Broadcom wireless network card from a diseased Dell Inspiron) 
Original OS: Win98 
Have downloaded Xubuntu with another computer (the now defunct Dell) and burned a cd, which I used to load Xubuntu into ThinkPad. Did a full reformat and _only _have xubuntu in this computer. But I need internet access to get internet access! 
Two possibilities:
I have a usb-to-network cable. Can I make this work? How do I do this?
I have the broadband pci card. BCM94306CBSG (an aside. Does anybody know if the first digit "9" just mean that this was a card made for Dell? When I Google Broadcom card numbers, they almost always are a 4 digit 43xx number.) I have downloaded both the driver for the card and the ndis wrapper tar.gz file. But I'm not sure that Xubuntu can "see" the pci card. How do I find out?
:confused:

---

### Post by Whiffle on 2008-09-19
If you run "lspci" in the terminal and look through the list it gives you you should be able to tell if Linux sees it.

---

### Post by pstrbrc on 2008-09-19
AHA!!!!! Thanks! 
(ps. How long does it usually take to quit thinking MS and start thinking Linux?????:confused: )

---

### Post by LowSky on 2008-09-19
> **pstrbrc said:**
> How long does it usually take to quit thinking MS and start thinking Linux?????:confused: )

Decades...LOL..wait whats the question?:popcorn:

---

### Post by panhandle on 2008-09-19
To check network card recognition:

Open terminal
```
lshw -C network
```

your wireless card will appear if recognized.

---

### Post by pstrbrc on 2008-09-22
Thank you both! My BCM94306 shows up as a Broadcom BCM4306.

---

