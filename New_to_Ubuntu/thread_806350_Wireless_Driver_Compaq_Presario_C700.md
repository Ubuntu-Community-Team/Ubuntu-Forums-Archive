---
title: "Wireless Driver Compaq Presario C700"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by xxsethxxallen on 2008-05-24
Hey, I just got Ubuntu a couple of days ago, and I've been poking around on the Internet searching for a Wireless Driver for may Compaq C700, but I have yet to find any information of good use. Can someone lend me a hand please?

---

### Post by cardinals_fan on 2008-05-25
What kind of wireless card does it have?

---

### Post by xxsethxxallen on 2008-05-27
I think like Atheros or something. How do I check?

---

### Post by cardinals_fan on 2008-05-27
> **xxsethxxallen said:**
> I think like Atheros or something. How do I check?
What brand/model card is it (check the box)?

---

### Post by kwacka on 2008-05-27
open terminal, and type in: ```
lspci
```

find the one that looks like a wireless card, then just search here using the card's make/model - there's plenty of information regarding the different cards.

---

### Post by xxsethxxallen on 2008-05-28
My computer says it a 

" Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)"

I got that from the Terminal, now what?

---

### Post by kwacka on 2008-05-28
When I entered 'Atheros AR242' into the search box at the top of the page it showed me several threads, including this one:
[http://ubuntuforums.org/showthread.php?t=662877](http://ubuntuforums.org/showthread.php?t=662877)

---

### Post by duncan_bayne on 2008-11-27
These instructions worked for [me]("http://www.fluidscape.co.nz/?q=node/128") (Compaq C700, Ubuntu 8.10 Intrepid Ibex):

[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

### Post by lkraemer on 2008-11-28
Try these:

http://ubuntuforums.org/showthread.php?t=792158

http://ubuntuforums.org/showthread.php?t=988691

lkraemer

---

