---
title: "GFX driver install *help please*"
date: 2015-05-08
forum: New to Ubuntu
---

### Post by fade2 on 2015-05-08
Hi guys, I'm trying to get my laptops graphics card to install after discovering that it wasn't installed.

I've managed to get Catalyst installed but without the GFX drivers it won't even open.

I'm using Lubuntu, if that even makes any difference.

The drivers I'm trying to install are in a link at the bottom.

It downloads a ".run" file, however when I double click it, it opens in a text file. I've tried copying the files text into the command window but when it finishes pasting the command window just closes and nothing else happens.

I'm sorry, but I am COMPLETELY new to Linux so if I'm missing the most stupid thing ever. I apologize.


[http://support.amd.com/en-us/download/desktop/legacy?product=Legacy1&os=Linux%20x86](http://support.amd.com/en-us/download/desktop/legacy?product=Legacy1&os=Linux%20x86)

---

### Post by Bashing-om on 2015-05-08
fade2; Hello;

Show us what we are working with:
boot to terminal and post the outputs - Between code tags, please - of terminal commands:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
Maybe what we have here is "hybrid graphics", and the system does not know what to install.
Be aware installing from OEM is generally the last means to employ, There exist system compatible, much easier ways .
(this ain't Windows)

Once we know what is,

[INDENT][INDENT][INDENT]we can do
[/INDENT][/INDENT][/INDENT]

---

### Post by deadflowr on 2015-05-09
I don't think that driver will work anyway.
AMD dropped support for legacy drivers and they are no longer compatible with the current graphics stacks used by Ubuntu.

What version of Ubuntu is this?

---

### Post by fade2 on 2015-05-09
```
fade@Fade:~$ lspci -vnn | grep VGA -A 12
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS482M [Mobility Radeon Xpress 200] [1002:5975] (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:010f]
    Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
    Memory at d4000000 (32-bit, prefetchable) [size=64M]
    I/O ports at 9000 [size=256]
    Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
    Capabilities: <access denied>

08:01.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:010f]
    Flags: bus master, medium devsel, latency 168, IRQ 23
    Memory at d0202000 (32-bit, non-prefetchable) [size=4K]
fade@Fade:~$ sudo lshw -C display


```

```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: RS482M [Mobility Radeon Xpress 200]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8
       resources: memory:d4000000-d7ffffff ioport:9000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
fade@Fade:~$ 


```



It's V15.something

---

### Post by QIII on 2015-05-09
Hello!

deadflowr is quite correct.  The Radeon x200 no longer enjoys driver support from AMD for the current graphics stack (not just Ubuntu, but likely all current popular distributions).  That series of hardware lost AMD driver support some time around 2008, although for a time there were hacks to get around it.  Even the hacks will no longer work.

Although you would be able download and install the file from AMD, what you end up with is a borked and unusable system.

---

### Post by fade2 on 2015-05-09
Damn, good thing I didn't get it to work then O.o

It's a shame though. I would have liked to have OpenGL support on here for video processing :(

Thanks for your help though guys :)

---

### Post by fade2 on 2015-05-09
Quick question, how easy is it to switch out a graphics card on a laptop? I know most people will say it's not worth swapping GFX card on an old laptop. But OpenGL is a killer for me :( I need it for Kodi and other video apps.

---

### Post by alex375 on 2015-05-09
not all notebooks easy to disassemble. Card that ive seen were easy to plug out.
If you have card that's not hard

---

### Post by QIII on 2015-05-09
Some of them actually have the GPU onboard the motherboard and soldered down.  In that case it would not be something you could dol

---

### Post by phillip16 on 2015-05-09
Well, as long as the card is MXM, then in theory you can swap the graphics card out. But even then, the layout of the card can differ from company to company.

Maybe one day, someone will standardize it.

---

