---
title: "being thick at networking"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by daveoily on 2008-06-01
I have 2 computers, connected via crossover cable, both runnung ubuntu, one of which is ubuntu studio, I'm simply trying to get to use the file system of one on the other (specifically at the moment trying to shift a file from ubuntu to studio, but it'd be nice if i could get transfers going both ways)

ifconfig on studio only gives lo (local loopback?) information as though the crossover isn't there, but the wire is in firmly, and an indicator light is on as if to say the hardware at least has recognised its presence.

ifconfig on the normal release of ubuntu (am I lagging behind on 7.10?) gives recognised eth0 information

well, I haven't got this working before, so it's highly likely I'm doing something incredibly thick.

so does anyone know how I can get this going?

---

### Post by spiderbatdad on 2008-06-01
I'm not sure, but the crossover just acts in place of a switch. I should think you would still need some network sharing enabled...like smbfs. Try right clicking a folder in your home directory and selecting sharing options.
You could share the file system through adminstrative commands, and samba config

---

### Post by The Cog on 2008-06-01
The absence of an eth0 in ifconfig is critical. What kind of network adapter is it? (lspci might tell you)

---

### Post by daveoily on 2008-06-01
as the machine is not connected and I don't have any media to carry it about on to hand, the lspci command gave me some list most of which i guess can be discarded, but the suspect ones i couldn't identify were...

apollo super south
c pipc bus master ide
apollo super acpi

i have no idea what they are, but they may be the ones to look at perhaps?

---

### Post by Monicker on 2008-06-01
We need more details than that.  Either supply the full results of the lspci command, or run the following and show its output.
```

lshw -C network
```

---

### Post by daveoily on 2008-06-01
that last command had to be run using sudo, even then, a lot of info just flashed at me, it didn't look too useful i tried to pipe it to a file but that didn't work :S

lshw -C network > net

was what i wrote, ended up with a blank file...

all I could mske out in the flashes was as follows

PCI (sysfs)
IDE
framebuffer devices

like I said, not exactly useful, looks like I'll have to wait till I can scrounge a memory stick from somewhere, then I'll post the results of lspci ta for the help thus far though :)

---

### Post by daveoily on 2008-06-07
right, i got it together at last, lspci gives...

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:04.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:04.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:09.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0c.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
00:11.0 Mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultra100) (rev 02)


so, does that give anyone any clues?

---

