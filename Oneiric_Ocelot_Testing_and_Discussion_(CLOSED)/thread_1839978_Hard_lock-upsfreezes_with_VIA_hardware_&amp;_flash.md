---
title: "Hard lock-ups/freezes with VIA hardware &amp; flash drive"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-09-06
With this hardware I get hard lockups/freezes when I plug in a FAT USB data flash drive:

> VIA PC2500 Mainboard
VIA Esther C7 CPU 1500MHz
System Memory 2GB DIMM
VT8233/A/8235/8237 AC97 Audio Controller
CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] Graphics

I've cross-tested with both Ubuntu/Nautilus and Lubuntu/pcmanfm so I know this isn't a file manager problem.

Since no key combos will reboot I suspect a kernel problem but I guess it could be an X problem.

Any ideas?

---

### Post by kansasnoob on 2011-09-06
BTW I figured out it was hardware related because I can't reproduce it with my Intel hardware:

> JetWay JATOM-GM1-230-LF Motherboard
Intel Atom 230 CPU @ 1.60GHz
System Memory 2GB DIMM
Intel 82945G/GZ Integrated Graphics
Intel N10/ICH 7 Family High Def Audio Controller


Since the only way to reboot is a hard reset, and I can't open a terminal while frozen, I suspect I'll need to learn how to SSH the frozen box from my other one to collect info ................ something I'm clueless about :(

Also Natty works fine with the old VIA hardware so it's some kind of regression.

---

### Post by kansasnoob on 2011-09-06
My first plan of action is trying the mainline kernel but this may take some time because I have non-computer things that I must take care of.

---

### Post by kansasnoob on 2011-09-07
Well, installing the mainline kernel didn't appear to change anything ............... but, this is a big but, somehow I found it very fiddly to boot the mainline kernel with a Maverick grub-pc. No idea why :confused:

So I tried booting both the effected Ubuntu Oneiric and the Lubuntu Oneiric with their own grub-pc and this USB/freeze problem went away. Being a glutton for punishment I then handed boot off to that Maverick grub-pc again and the problem returned.

And a bit of closer looking tells me what was actually happening. I'm using both USB keyboard and mouse, and I also have a USB powered set of speakers plugged in to that box, that has a power light on the front of one speaker.

When I plug in that data drive the speaker light goes out indicating that the USB ports actually go dead, I've never seen such a thing before. And it only happens if I've booted into Oneiric with that Maverick grub-pc.

If I use a PS2 mouse and keyboard I can reboot OK which brings back the USB power, but just restarting X does not bring back the USB power.

Regardless using either a Oneiric or Natty grub to boot prevents this from happening altogether. This is an odd one for me, but I guess the general rule of thumb should now be always use the newest OS's grub to boot in a multi-boot scenario.

Odd thing indeed but thought it was worth sharing ;)

---

