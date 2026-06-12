---
title: "Can't get any sound, not sure where to start."
date: 2008-08-02
forum: New to Ubuntu
---

### Post by InTheShires on 2008-08-02
Latest version of Ubuntu installed, and I've managed to get most things working by reading things here.Which I'm quite pleased with.

However, I can't get any sound working. I've tried a few things that I've found on here, but it's still not working.

This is the last thing I need to get sorted, other than this my system is sorted and running well. 

It's a Realtek sound chip, on an Acer Aspire 3050.

Thanks in advance for any help.

ITS

---

### Post by northern lights on 2008-08-02
Can you post the outputs of ```
cat /proc/asound/cards
``` and ```
sudo lshw -C multimedia
```

Thank you.

---

### Post by InTheShires on 2008-08-03
Thanks for replying...

```

 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xb0000000 irq 18
 
```

and 

```
 *-multimedia            
       description: Audio device
       product: IXP SB4x0 High Definition Audio Controller
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64 module=snd_hda_intel

```

---

### Post by northern lights on 2008-08-03
Intel's HDA chipset is not fully compatible yet.

You might want to read [this HowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Launchpad bug reports on this device are marked as 'Won't Fix' as they do not meet the criteria for a stable release update.

I dunno if it'll be fixed in Intrepid.

---

### Post by InTheShires on 2008-08-03
> **northern lights said:**
> Intel's HDA chipset is not fully compatible yet.

You might want to read [this HowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

Thank you. I've followed the instructions, things have gone ok so far. 

However, when I follow this bit from the "HowTo".

```
Open /etc/modprobe.d/alsa-base with the following command: 

sudo nano /etc/modprobe.d/alsa-base

Then paste the following line at the end of the file (change MODEL with the type of sound card's model, in our example it should be "acer" (without quotation marks)): 

options snd-hda-intel model=MODEL
Reboot
```

I paste and edit the details as I need to. But I don't think it's saving the line I've added. When I reboot, I still have no sound, but the line of code I added, is no longer there.

Is that right?

If not, how do I make it save the line I add? (Seems a dumb question, but I can't see how to make it save it)

---

### Post by northern lights on 2008-08-03
In nano, "Ctrl+O" saves and "Ctrl+X" exits...

---

### Post by InTheShires on 2008-08-03
> **northern lights said:**
> In nano, "Ctrl+O" saves and "Ctrl+X" exits...

Ah, ok. Thanks again!

---

### Post by InTheShires on 2008-08-03
Thanks so much northern lights, got it sorted now. Really grateful for the help/support.

The HowTo worked a treat. (And knowing how to save in Nano!)

/doffs_cap

---

