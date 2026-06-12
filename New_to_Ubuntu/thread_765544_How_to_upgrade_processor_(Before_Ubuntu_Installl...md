---
title: "How to upgrade processor (Before Ubuntu Installl...)"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by SweetBearCub on 2008-04-24
Greetings.

I've downloaded Xubuntu 8.04 LTS (x86-32) and burned it to a CDR, but before I install it, I'd like to complete the last upgrade to my machine - Replacing the P3 1.13Ghz (256KB L2) with a P3 1.40Ghz (512KB L2).

Unfortunately, I haven't the slighest idea of how to do it. (The RAM, video card, HD, & DVD Burner were much easier..)

On my Dell Optiplex GX150, the processor is mounted under a large heatsink which has a small fan mounted on the side. The heatsink appears to be held in place by two small metal clips which grab onto the processor mount on two sides. **Unfortunately, there doesn't seem to be any obvious way to remove the heatsink from the processor mount**, and I'm afraid that if I experiment with it, I may do some serious damage. (I've never upgraded a processor before..)

Once I have the heatsink & fan off, as far as I know, all I have to do is release the ZIF lever and pull the heatsink off. If the CPU thermal grease has frozen the CPU to the bottom of the heatsink, the whole thing *should* come out, at least in theory.

Then I just gently free the old CPU from the heatsink, clean the old grease off both surfaces, re-apply the new thermal grease to the new CPU (I know I'm not supposed to use much, but how much is too much?), insert it into the processor mount, lock the ZIF lever, and reinstall the heatsink and fan. (Can't forget the fan power connector either!)

Then, cross my fingers and power the system up.

If anyone can talk me through this or provide some illustrations or tips, it would be appreciated.

Thanks...

---

### Post by Paqman on 2008-04-24
Sounds like you have a pretty good grasp on the process.

The clips on heatsinks/fans can be seriously stubborn, at a time when you'd prefer to be gentle. See if the manufacturer has any guides available about disassembly. Is it the stock heatsink that came with the processor? Do you still have the guides that came with it?

As for thermal grease, you really only want enough to provide a sooth surface of contact. The grease is there to stop any imperfections in the mating surfaces from creating air gaps that won't conduct heat across the joint. So the short answer is: thinner than you'd think. Make sure you set up a clean area to work, with a nice stiff plastic spreader to give you an even coat. Don't touch the mating surfaces with your fingers, it'll leave oils in the join. Again, the manufacturer should have detailed pictorial instructions for you.

---

### Post by SweetBearCub on 2008-04-24
Paqman, thanks for the fast reply.

No, I do not have the guides that came with the system. It is quite old, and has likely been through several owners. The heatsink appears to be the stock Dell type, although I have nothing to base that on. It doesn't look to be anything special - It's the same size as the processor mount, made of a shiny silver metal (aluminium maybe?) and is composed of vertical 'fins'. There is a metal link running through the fins at the lower part of the heatsink which attaches it to the processor mount.

I checked Dell's support site, but found nothing helpful. If you have any ideas, I'd be happy to hear them. If it helps, the system's Service Tag is "86QYD11".

Thanks again...

---

### Post by Paqman on 2008-04-24
Without knowing exactly what you're looking at it's difficult to guess the right way to disassemble it. I'd just say take the mobo out, put it on a flat surface and take a really good look at how it's secured. You might be able to figure out how to unclip it just by eyeballing it.

Of course, taking the board out would involve plugging everything back in properly later, which might not be an option if you don't have manuals.

Btw, don't touch any conducting parts inside the case with your bare hands. The static electrical charge on your body can cause invisible damage to the components. Handle printed circuits or the processor by the substrate. Definitely don't touch any pins or connectors.

---

### Post by Zralou on 2008-04-24
It sounds like a slot 370 mount.  If so, where the clips connect either side of the processor, it should be just a small plastic 'ear' that the metal strip clips to.  The easiest way is to gently push down on one side of the metal strip, at the same time push outward where is 'loops' onto the 'ear'.
Once you get one side loose, the other side will just unclip easily, as the metal strip will slide across to the other side.

Hope you can make head nor tail of those instructions.
Sara Lou

---

### Post by SweetBearCub on 2008-04-24
Ok - I think I've got it!

The BIOS recognizes the CPU, listing the correct processor name, speed, and L2 cache. Windows XP booted, and so far seems to be running with no problems. Perhaps its a placebo, but it seems to be a few percent faster. The new processor may only bring an extra 267 Mhz in speed, but hopefully, increasing the L2 cache from 256KB to 512KB helps out more.

Thanks for your help!

---

