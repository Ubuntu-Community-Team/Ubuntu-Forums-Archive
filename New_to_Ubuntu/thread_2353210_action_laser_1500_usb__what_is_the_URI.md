---
title: "action laser 1500 usb:  what is the URI?"
date: 2017-02-19
forum: New to Ubuntu
---

### Post by ankvigil on 2017-02-19
I used Ubuntu 3 years ago on an old dell computer and was pleased that it 'saw' our old actionlaser 1500.  overall too slow, etc.  Now got another free device from in-laws and would love to use this hp laptop to find and use the actionlaser 1500.  Since the laptop is newer i had to get pin converter to usb, but ubuntu doesn't see the usb.  looked for hours for solutions;  last was the command dmesg  which showed:   um,  can't post it cause can't figure out to select, copy and paste...i saw lots of 'serial number:  000:00:1a.0
in any case, i didn't see an obvious number string that cups uri might like.  any advice appreciated.

---

### Post by oldrocker99 on 2017-02-19
Is there a "Network" readout for the printer? You're likely to find the URI there, or at least that's where I found it on my Brother laser printer.

---

### Post by ankvigil on 2017-02-20
I did an lpinfo  -v and got lots of networks.  I think I am more interested in the "direct" ports? As my printer cable goes to usb.  Two direct hits were  hp and hpfax.  I tried both with ipp:/hp and hpfax got nothing.   I did try a network upi and that found my new printer nicely, but I had already found that long before.   Perhaps I am using wrong ipp /upi forthe "direct" ports?

---

