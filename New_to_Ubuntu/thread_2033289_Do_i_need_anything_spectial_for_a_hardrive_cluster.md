---
title: "Do i need anything spectial for a hardrive cluster?"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by cosmoshell on 2012-07-25
I want to make a hardrive cluster of several hardrives, do I need anything spectial for this? Will a laptop work? Pros cons of anything?

edit. like useing 10 or more hardrives.

---

### Post by anewguy on 2012-07-25
Do you mean like the raid that is the jumbled collection of odd disks?

---

### Post by cosmoshell on 2012-07-25
> **anewguy said:**
> Do you mean like the raid that is the jumbled collection of odd disks?

I think thats it. I need to know if I need special hardware or additional soft?

---

### Post by HeroOfCanton on 2012-07-25
Based on cables: A typical PC will handle up to 4 hard drives. A laptop is typically limited to one.

There are ways though. Off the top of my head:

USB drives (slow)
PCI expansion slots (meh)
SCSI interface card (expensive)

You would also need to ensure that your power supply could support it, and you can fit them all in the case. I have enough trouble getting 4 to fit in most of my systems, including the servers. A laptop... Well, the image of a daisy chain of drives hanging from the bottom of a system doesn't seem appealing.

---

### Post by cosmoshell on 2012-07-26
> **HeroOfCanton said:**
> Based on cables: A typical PC will handle up to 4 hard drives. A laptop is typically limited to one.

There are ways though. Off the top of my head:

USB drives (slow)
PCI expansion slots (meh)
SCSI interface card (expensive)

You would also need to ensure that your power supply could support it, and you can fit them all in the case. I have enough trouble getting 4 to fit in most of my systems, including the servers. A laptop... Well, the image of a daisy chain of drives hanging from the bottom of a system doesn't seem appealing.

I hope im wording this properly. is the pci or scsi method scalable? can I add another lets 10 hardrives If i already have this many, doing this? I was thinking about leaving the hardrives outside of the case so space for hardrives isent an issue.

---

### Post by Cheesemill on 2012-07-26
To start with you need to provide a SATA port for each disk drive. If the drives are going to be external you can get cards which take up on PCI slot in your computer and give you 8 external SATA ports. You can get them for around $200 each (obviously you would need 2 of them for 10 drives). You would then also need an enclosure to hold all of your drives and provide them all with power (probably around another $200 or so for an 8 drive enclosure).

---

