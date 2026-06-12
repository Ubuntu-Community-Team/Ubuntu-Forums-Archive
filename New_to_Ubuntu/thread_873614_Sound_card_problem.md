---
title: "Sound card problem"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Benbow on 2008-07-29
I have two sound cards in my system, one on board intel and a separate pci card, they came with the pc and I have no idea of the history. My problem is that each time I turn on the pc one of three things can happen 1) the on board intel card works 2) the pci sound card works (I know this because I constantly have to change the speaker plug from one to the other) or 3) I have no sound at all!
When I dive into System/Preferences/Sound, I can usually sort out what is working but there is no constant factor here either.
I suppose that the obvious answer would be to remove the pci card and use the onboard sound but I would prefer not to do this.

Thanks for any help.

---

### Post by Bradtek on 2008-07-29
Disable the onboard one in the Bios.
When the computer is starting Press the Del key
If Del key doesn't work there are a few others
to try depending on what brand your motherboard / bios is

---

### Post by northern lights on 2008-07-29
> **Benbow said:**
> I suppose that the obvious answer would be to remove the pci card and use the onboard sound but I would prefer not to do this.
You pretty much nailed the easiest solution. Yet, if you'd rather use the PCI card, I'm certain you can disable the onboard sound chip in the BIOS (most likely: hit 'DEL' at bootup and look for 'Integrated Peripherals' section)

---

### Post by Bradtek on 2008-07-29
Do you know what the brand / model of the PCI sound card is ?
It maybe no better than the onboard.

---

### Post by Benbow on 2008-07-29
Thanks for your help, guys. I have to go out for a few hours but will try your suggestions when I return.

---

### Post by Benbow on 2008-07-30
This is a "used" pc so I am not familiar with its wrinkles. What I can see is that the sound system is very unstable and changes at each boot up. You mentioned the bios but I can't get further into the bios on this pc than altering the boot start up sequence (cd,floppy etc) which is a little limiting!
I will try removing the pci sound card to see what effect this has. Wish me luck!

---

### Post by northern lights on 2008-07-30
> **Bradtek said:**
> Do you know what the brand / model of the PCI sound card is ?

> **Benbow said:**
> This is a "used" pc so I am not familiar with its wrinkles

Run```
cat /proc/asound/cards
``` or ```
sudo lshw -C multimedia
```to get an idea of what device/chipset you're using.

---

