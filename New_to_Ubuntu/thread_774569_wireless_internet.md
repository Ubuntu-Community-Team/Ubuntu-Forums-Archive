---
title: "wireless internet"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-29
i am trying to install ubuntu onto my mom's computer, but she does not have an ethernet port. She has had a wireless internet usb drive, but that has done nothing on my ubuntu. It is a MyEssentials 802.11g-54mbps drive. Any help?

---

### Post by EnergySamus on 2008-04-29
The easiest thing to do is to go to your nearest PC store and by a Ethernet Card. Wireless is not good for desktops (just my opinion).


EnergySamus

---

### Post by shearn89 on 2008-04-29
> **Zopiac said:**
> i am trying to install ubuntu onto my mom's computer, but she does not have an ethernet port. She has had a wireless internet usb drive, but that has done nothing on my ubuntu. It is a MyEssentials 802.11g-54mbps drive. Any help?

First you need to hit alt-f2, type xterm, and then in that terminal do
```

lspci | grep Network

```
Its case-sensitive. Paste that output here, which will give us the chip set of your card, and we can help you find the right drivers for it. it may take a bit of putting stuff onto usb sticks and moving it back and forth from a connected computer, but you can get there in the end.

---

### Post by Zopiac on 2008-04-29
uhm nothing happened.

wait, i forgot to put in xterm, but now when i press alt+f2, nothing happens.


edit: ok i went to the normal terminal and did it there, opened up a box and i typed in lspci | grep Network. it did nothing after that

---

### Post by shearn89 on 2008-04-29
can you go application -> accessories -> (some form of terminal like gnome-terminal or xterm)?

---

### Post by Zopiac on 2008-04-29
> **shearn89 said:**
> can you go application -> accessories -> (some form of terminal like gnome-terminal or xterm)?

done and failed ^

---

### Post by shearn89 on 2008-04-29
try logging out and back in.

---

### Post by Zopiac on 2008-04-29
> **shearn89 said:**
> try logging out and back in.

it only opens a window for a brief moment then closes it; i dont know.

---

### Post by shearn89 on 2008-04-30
Do you mean the terminal? It just pops up and then closes? if so, hit ctrl-alt-f1, and log in as usual. Then try lspci.

---

