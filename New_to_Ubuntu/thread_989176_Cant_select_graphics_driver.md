---
title: "Cant select graphics driver"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by lightnin on 2008-11-21
my card is detected - its a PCI Trident 9750

detected as
```
 *-display               
       description: VGA compatible controller
       product: 3DImage 9750
       vendor: Trident Microsystems
       physical id: 9
       bus info: pci@0000:00:09.0
       version: f3
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master
       configuration: latency=32

```

When I boot, before login I get the "Ubuntu is running in low graphics mode" warning

if I select the Trident driver, and log in , the driver isn't selcted.  it set itself as a VESA-Generic driver, even tho it is telling me which card it has detected above !

if I select the trident driver and click OK it doesn't change it.

I am a newb to linux so easy answers please.

My system is a P4 running 7.10 Gutsy

Thanks

---

### Post by phidia on 2008-11-21
How are you selecting the trident driver?  You can open a terminal or from command line enter this: > sudo dpkg-reconfigure -phigh xserver-xorg
See if that works.

---

### Post by lightnin on 2008-11-21
I have to go out - I'll be back in an hour (didnt want to seem rude by not replying 

Thanks

---

### Post by lightnin on 2008-11-21
:):):):):):)


Thanks :)  that seems to have done the trick :)

so ... what made it go wrong in the 1st place ?  or is it common ?

---

### Post by phidia on 2008-11-21
> **lightnin said:**
> :):):):):):)


Thanks :)  that seems to have done the trick :)

so ... what made it go wrong in the 1st place ?  or is it common ?

Some cards are not auto configured and I guess the trident is one of those.
You are using an old release too-but I can't say whether you'd have any better luck with the latest release. IMO if it works stay with it.

---

### Post by lightnin on 2008-11-23
Hello again all .

Today I switched on and I was back to low graphics mode.

The above, let me set the graphics back up again, but I dont realy want to be doing this every morning !

any ideas whet might be wrong ?

Now its working, I'll try shutting down and booting back up to see if it happens again.

back in a min !

---

### Post by lightnin on 2008-11-23
still ok after a shut down :confused:

so its either something I am doing whilst powered up.

or could it be a hardware fault with my graphics card - over heating or something ?

:confused:

---

