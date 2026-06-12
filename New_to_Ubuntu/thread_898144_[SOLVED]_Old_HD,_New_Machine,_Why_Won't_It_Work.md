---
title: "[SOLVED] Old HD, New Machine, Why Won't It Work?"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by E.T.Smith on 2008-08-22
My old desktop was done in by a couple of lightning strikes last week. The shop I took it to pointed out a fried motherboard, called it hopeless and advised I get a new machine, which I did. On the plus side, the original hard-drive is likely intact. I assumed I'd be able to swap out the blank new one for the old and pick up where I left off, but both the shop and the person I bought the new machine from said this would be a bad thing, that the HD trying to run on the specs of the old machine would crash in an instant  and instead I'd have to make do with "slaving" the old drive and swapping out the data.

First, is the techs' warnings relevent to a linux system, or is this bit of hardware touchiness only a problem with more mass-market OSes? Ubuntu has been pretty tolerant with general hardware changes before, and I don't see a switch from one i386 machine to another being so dire.

Second, if it comes to it, how do I "slave" the old drive? Wires and sockets were pointed out to me, but I'm sure there's more detail to know.

---

### Post by Shazaam on 2008-08-23
There is a good probability that the electronics on the hard drive's pc board might have gotten fried along with the motherboard. BUT, you never know until you try. Set the jumper on the old drive to SLAVE and see if it works. If you don't have a port (on your motherboard) for it you can by a USB drive enclosure pretty cheap these days.
I rescued a drive that was submerged in the midwest flooding this year and it works great. OpenSuSe and Mandriva are on it now. :)

---

### Post by Iowan on 2008-08-23
If it's (E)IDE drive, there are probably jumpers for Master, Slave, and Cable Select.  On some drives, there's a different setting for "only".  I'm rapidly losing track of the "new stuff", but my (somewhat worthless) opinion is that a new machine should be smart enough to deal with an old drive. "Safe" bet would be to follow suggestions, copy old drive onto new... 
Then (if curious and/or courageous enough), try booting from old drive alone.  If it crashes, re-install new drive with backed-up data.

---

### Post by E.T.Smith on 2008-08-23
> **Shazaam said:**
> Set the jumper on the old drive to SLAVE and see if it works.
> **Iowan said:**
> If it's (E)IDE drive, there are probably jumpers for Master, Slave, and Cable Select.  On some drives, there's a different setting for "only".

What is the jumper, and where do I find it/them? 

The three sockets pointed out to me on the HD were a ribbon-strip input (data-flow, I assume), a four-prong power outlet and a-not-clearly-identified smaller secondary outlet with a small white cap in it that I've been told to remove. The old drive will essentially be read as media, I guess.

EDIT: yes it is an Enhanced IDE drive, structurally identical to the new one.

---

### Post by eightmillion on 2008-08-23
Here's a picture of a hard drive jumper:
[IMG]http://www.zdnetasia.com/i/techguide/harddrive-C.jpg[/IMG]
Your drive should have a diagram on it like this to instruct you where to place the jumper:
[IMG]http://www.easeus.com/resource/images/install-ide-hard-drive-jumper.gif[/IMG]

---

### Post by wgrant on 2008-08-23
> **E.T.Smith said:**
> My old desktop was done in by a couple of lightning strikes last week. The shop I took it to pointed out a fried motherboard, called it hopeless and advised I get a new machine, which I did. On the plus side, the original hard-drive is likely intact. I assumed I'd be able to swap out the blank new one for the old and pick up where I left off, but both the shop and the person I bought the new machine from said this would be a bad thing, that the HD trying to run on the specs of the old machine would crash in an instant  and instead I'd have to make do with "slaving" the old drive and swapping out the data.

First, is the techs' warnings relevent to a linux system, or is this bit of hardware touchiness only a problem with more mass-market OSes? Ubuntu has been pretty tolerant with general hardware changes before, and I don't see a switch from one i386 machine to another being so dire.

In most cases it should work fine. The only likely issues are if you have installed strange drivers manually, or a different proprietary graphics card driver is required. Both are fairly easily to fix - in neither case is a reinstall required. Windows, on the other hand...

---

### Post by alienexplorers on 2008-08-23
Most drives even older ones have a label or etching on the drive showing the pin placement fo master or slave.

---

### Post by Gone fishing on 2008-08-23
If its a new mother board is your now drive an IDE drive? I would guess not it will probably be a SATA drive so you can just plug in the old IDE drive, leave it as master if you wish, and go into the BIOS and make sure the first boot device is the SATA drive. The IDE drive will then behave like a slave drive.

---

### Post by E.T.Smith on 2008-08-23
> **eightmillion said:**
> Here's a picture of a hard drive jumper ...
Your drive should have a diagram on it like this to instruct you where to place the jumper ...

Thank you that helps immensely, since the old drive has no such diagram. Interestingly, according to that image the white shunt on the old drive has always been in the "limit drive" position rather than "master". Is that significant?

---

### Post by eightmillion on 2008-08-23
You should not go by that diagram. Most hard drives are different. If you can, you should look at the manufacturers website.

---

### Post by gmjs on 2008-08-23
By the sound of it, the advisor at the shop said they didn't advise it because they didn't know!  An IDE hard disk drive will run fine in a newer machine (regardless of OS), **provided that the new motherboard/PSU supports the IDE data and power connections. **

Unfortunately, I suspect that your new machine will not have the appropriate connectivity for the IDE drive and will only support a SATA drive (it's pretty safe to assume that most PCs bought in the last two/three years will primarily support SATA).

Therefore, **it is most likely that the old drive will not be able to connect to the new motherboard, physically.**

A good option may be to buy an IDE drive casing with USB interface.  Then you could put your old drive in the device and connect it via USB to your new PC and copy any data you need across.

Hope this helps,

Graham

---

### Post by E.T.Smith on 2008-08-23
> **fujitsu said:**
> In most cases it should work fine. The only likely issues are if you have installed strange drivers manually, or a different proprietary graphics card driver is required. Both are fairly easily to fix - in neither case is a reinstall required. Windows, on the other hand...

Based on this encouragement, I shrugged, swapped the drives, powered up and hoped for the best. And everything's been working without so much as a hiccup, so it seems there was no need to worry. As far as I can tell, ubuntu adjusted to the change in hardware as a matter of course; it recognized the difference in media drives without prompting, for instance.

> **gmjs said:**
> By the sound of it, the advisor at the shop said they didn't advise it because they didn't know!  An IDE hard disk drive will run fine in a newer machine (regardless of OS), provided that the new motherboard/PSU supports the IDE data and power connections.

Unfortunately, I suspect that your new machine will not have the appropriate connectivity for the IDE drive and will only support a SATA drive (it's pretty safe to assume that most PCs bought in the last two/three years will primarily support SATA).

Huh. I wasn't aware of this shift in HD design. Fortunately I'm cheap; when I say I bought a "new" machine, I really mean a used Gateway E4000 of nearly identical vintage and design as my old Dell 2400; so much alike that I've been able to salvage parts from the Dell and plug them into the Gateway.

Now I've got a new puzzle: two functioning hard drives, one running Ubuntu and one running Windows. Wonder if I can manage a dual boot.

---

### Post by Ptero-4 on 2008-08-24
I suggest you to just clean out the trash from the drive not running ubuntu.

---

### Post by E.T.Smith on 2008-08-24
> **Ptero-4 said:**
> I suggest you to just clean out the trash from the drive not running ubuntu.
Tempting, but I have use for Win on the secondary for exactly two reasons: dealing with my ISP, whose periodic service changes cut me off from the internet unless verified by Win, and running the Win-games I've never been able to get going in Wine.

---

