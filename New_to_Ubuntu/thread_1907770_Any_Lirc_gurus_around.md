---
title: "Any Lirc gurus around?"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by hopelessone on 2012-01-12
Hi Guys,

Trying to map ALL of my buttons for Asus P7131 Hybrid TV Remote

Lirc buttons don't all work...

I did this so far:

```
lsinput
/dev/input/event6
bustype : BUS_PCI
vendor : 0x1043
product : 0x4876
version : 1
name : "saa7134 IR (ASUSTeK P7131 Hybri"
phys : "pci-0000:05:00.0/ir0"
bits ev : EV_SYN EV_KEY EV_REP
```

```
input-events -g -t5 6

```shows all buttons working

```
input-kbd 6 > keyMapIR.txt

```
My question is how can i use the data from keyMapIR.txt to make a new mycinema.conf lirc file?

I tried direct change from:
1 0x0002 <-old file
to
1 0x0816 <- new keyMapIR.txt

started lircd then irw and nothing...

I've attached both files for your review...

Would absolutely love to get this working 100%

So close need a hand from anyone out there..

---

### Post by hopelessone on 2012-01-12
Or just map it as a keyboard?

Anyone got any ideas?

---

