---
title: "Wireless"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by marlan on 2008-08-04
I have a Netgear Wireless-G PCI Adapter WG311 that I want to install on my Linux computer running Xubuntu. The set-up CD only comes with Windows set-up, how do I get the necessary set-up either disc or program to install this adapter to use in my Linux system?:confused:

---

### Post by muted1987 on 2008-08-04
could you post the outup of lspci | grep Ethernet

---

### Post by marlan on 2008-08-04
could you post the outup of lspci | grep Ethernet

Where do I find that?

---

### Post by c2olen on 2008-08-04
> **marlan said:**
> could you post the outup of lspci | grep Ethernet

Where do I find that?

Start a terminal session en type the command:

```
lspci | grep Ethernet
```

Then cut and paste the output in a reply in this thread?

---

### Post by marlan on 2008-08-04
This is the result I got from the code you asked me to run.

01:08.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

---

