---
title: "Suitable Graphics card?"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-17
Hi,

Google earth runs very slowly on my machine. I suppose I need an adequate graphics card. Has anyone any suggestions Please? (UK).

---

### Post by muteXe on 2008-11-17
[http://earth.google.com/support/bin/topic.py?topic=13341](http://earth.google.com/support/bin/topic.py?topic=13341)

---

### Post by davidsrsb on 2008-11-17
I just installed a MSI 8600GT and it runs Compiz effects and OpenGL stuff very well.
It is a fanless design with a large heatpipe cooler so it is silent too.

Price was equivalent to USD70

---

### Post by handydan918 on 2008-11-17
> **muteXe said:**
> [http://earth.google.com/support/bin/topic.py?topic=13341](http://earth.google.com/support/bin/topic.py?topic=13341)

Great link! According to that, the OP needs Windows!:)

---

### Post by Stalker72 on 2008-11-17
> **davidsrsb said:**
> I just installed a MSI 8600GT and it runs Compiz effects and OpenGL stuff very well.
It is a fanless design with a large heatpipe cooler so it is silent too.

Price was equivalent to USD70
Works fine with [9800 GX2]("http://www.nvidia.com/object/geforce_9800gx2.html") too.
Price (when I bought it) was $500-600. It's cheaper now.

Stalker72

---

### Post by starcannon on 2008-11-17
@nnjond

What are you currently running?
If your unsure whats in your machine please post the output of:
```
sudo lshw -C display
```

P.S. you won't need an expensive card, a $30 to $50 card (USD) will run it fine.

---

### Post by Tom--d on 2008-11-17
Any Nvidia Graphics Card will do.

---

### Post by nnjond on 2008-11-17
Thanks for your interest.

 *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 cap_list
       configuration: latency=0
nick@nick-desktop:~$

---

### Post by starcannon on 2008-11-17
> **nnjond said:**
> 
       vendor: Silicon Integrated Systems [SiS]
       
SiS... curses... my advice is go get an nvidia 5500 or better video card. I have never seen an SiS card pull off any 3d applications in Linux.

Again 5500 or newer, any thing older than the 5500 requires use of the legacy drivers, and additional headaches.

A 7xxx or 8xxx series nvidia card is probably the easiest to lay your hands on, though newegg.com and other web shoppes carry everything.

To be completely clear, an Nvidia 5200 is a legacy card. An Nvidia 5500 is a "new" card.

GL and happy hunting.

---

### Post by LowSky on 2008-11-17
My advice is buy an 8600 or a 9600 from Nvidia. Very decent cards that should playt most games and google earth just fine

---

