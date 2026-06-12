---
title: "Yamaha ymf724e"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by sakid on 2008-09-30
Hi All,

I'm having trouble getting my sound card to work. It is a yamaha ymf724e-v which is a pci card.
As far as I can tell the OS isn't even detecting it.

Any help would be greatly appreciated.

Cheers

---

### Post by markbuntu on 2008-09-30
Type aplay -l in a terminal and post the results here.

---

### Post by sakid on 2008-09-30
> mythtv@mythsvr:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I'm 99% sure that is the onboard sound - but could be wrong

---

### Post by markbuntu on 2008-09-30
Yes, that is the onboard sound. No sign of the Yamaha card.

Did you just put this card in?

Is the card recognized and enabled in the bios?

It is supported so it should show up. Have you tried it in another slot? Post the results of:

lspci

---

### Post by sakid on 2008-09-30
Would appear the problems more involved than the sound card. I've tried different pci slots and different pci cards and nothing seems to work.
Any ideas?

---

### Post by markbuntu on 2008-10-01
Did you look in the bios when you boot up. Sometimes, with some machines, you need to enable a new pci card in the bios.

---

