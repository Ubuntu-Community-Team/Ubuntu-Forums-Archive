---
title: "Need help reflashing BIOS"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by BSG75 on 2008-07-19
I need to disable PnP, and in another forum another user had the same problem as I. He was told to reflash the BIOS. Can someone help me with this?

---

### Post by sdowney717 on 2008-07-19
run the bios setup at PC boot
There should be an option to disable plug and play

---

### Post by jerome1232 on 2008-07-19
What you actually are wanting to do is flash CMOS I think. That's the little utility that you use to edit BIOS settings. There should be a jumper somewhere on you motherboard that is labled CMOS, if not consult your manufactures manual. 

All you have to do is turn everything off, move the little jumper over (somemotherboards you have to just put a jumper on the 2 pins there) wait 20 seconds, remove/move jumper back, Boot up machine and your BIOS should be back to factory settings.

I would consult your motherboards manual for exact instructions though.

---

### Post by Sef on 2008-07-19
Before flashing your BIOS:

1) **Back up** your data

2) Have a Live CD or an alternate cd handy.

Flashing your BIOS can necessitate a reinstallation of your OS.

---

### Post by benerivo on 2008-07-19
If you want to disable pnp, then just enter the BIOS settings (like sdowney717 said) when the machine is first powered on. The only reason you would want to flash the CMOS is if the BIOS settings were password protected, and so you were unable to change them (in which case removing the battery inside the machine for 1 minute should remove the password protection).

---

### Post by BSG75 on 2008-07-19
I have already checked  the BIOS and I can't disable PnP from there. I have a PhoenixBIOS by the way

---

### Post by cariboo on 2008-07-19
If you don't know what you are doing, do not flash your bios. I have a friend that has bricked his computer 3 times trying to flash the bios. The first two times I managed to get a replacement bios chip. The last time he had to buy a new motherboard. That being said if your motherboard manufacturer allows flashing the bios from windows do it that way.

What problem do you have that you need to turn off plug n' play?

Jim

---

### Post by benerivo on 2008-07-19
Why do you need to disable pnp?

---

### Post by BSG75 on 2008-07-19
When I start my computer I get the message pnpbios caused fatal error, reboot with pnpbios=off option to operate stably. Sound and video do not work properly.
I thought that if a disabled pnp it would fix the problems

---

### Post by oilchangeguy on 2008-07-19
> **BSG75 said:**
> When I start my computer I get the message pnpbios caused fatal error, reboot with pnpbios=off option to operate stably. Sound and video do not work properly.
I thought that if a disabled pnp it would fix the problems

please give your computers specs, and the version of ubuntu you're using. as already stated you should be able to disable pnp from within the bios. or as already stated some newer computers have the ability to flash the bios from windows (winphlash, or winflash, see start, all programs). usually the only reason to flash the bios is for updates (not needed by most users) or to enable large hard drive support in older computers. you can't just "flash" the bios. you have to get a floppy from the bios or mother board maker. even then not done properly, you'll end up with a large door stop.

---

### Post by jerome1232 on 2008-07-19
Have you tried Loading failsafe defaults, or Optimised Defaults? I have a pheonix bios as well but they will still differ in menus. For me there is no option to turn off PnP either, I can set it to manual though.

---

### Post by cjv8888 on 2008-07-19
If you wish to flash your bios you should prepare for it carefully.
Read a guide such as [this]("http://www.pcstats.com/articleview.cfm?articleID=1605") carefully.
I have flashed the bios in 2 of my computers without problems, but if your computer doesn't have a floppy drive, it can be much more difficult.

---

### Post by jerome1232 on 2008-07-19
> **benerivo said:**
> If you want to disable pnp, then just enter the BIOS settings (like sdowney717 said) when the machine is first powered on. The only reason you would want to flash the CMOS is if the BIOS settings were password protected, and so you were unable to change them (in which case removing the battery inside the machine for 1 minute should remove the password protection).

Actually flashing CMOS will load the manufacturer set defaults which are usually correct for the machine, I've used it if i've gotten too curious in my CMOS setup screens and changed things I shouldn't have.

(over clocking memory/processor you can make the machine unbootable)

Flashing CMOS carries non of the dangers (at least that I know of correct me if wrong) of flashing BIOS, flashing BIOS for an update definitely can brick your computer. Also before flashing a BIOS you are supposed to flash CMOS to clear out settings.

---

### Post by BSG75 on 2008-07-19
I have a Compaq F730US with Gutsy Gibbon installed

---

### Post by oilchangeguy on 2008-07-19
> **jerome1232 said:**
> Actually flashing CMOS will load the manufacturer set defaults which are usually correct for the machine, I've used it if i've gotten too curious in my CMOS setup screens and changed things I shouldn't have.

(over clocking memory/processor you can make the machine unbootable)

Flashing CMOS carries non of the dangers (at least that I know of correct me if wrong) of flashing BIOS, flashing BIOS for an update definitely can brick your computer.

bios and cmos are the same thing. cmos is actually an outdated term.

---

### Post by jerome1232 on 2008-07-19
CMOS is the setup utility for BIOS.... they are not the same.

when you flash bios you update it, when you flash cmos you clear bios settings.

They are just used interchangably.

---

### Post by BSG75 on 2008-07-19
Is there anything I can do?

---

### Post by sdowney717 on 2008-07-20
[http://www.smartcomputing.com/editorial/article.asp?article=articles/archive/l0604/82l04/82l04.asp&guid=](http://www.smartcomputing.com/editorial/article.asp?article=articles/archive/l0604/82l04/82l04.asp&guid=)

read this to learn about changing cmos bios settings

---

### Post by BSG75 on 2008-07-20
I still can't fix the problem is it a possibility that I need a new live CD.

---

### Post by BSG75 on 2008-07-20
Never mind it works now, I made a new dvd with hardy heron, and it works fine.

---

