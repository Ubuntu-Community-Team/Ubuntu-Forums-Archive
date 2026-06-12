---
title: "How to overlock in Ubuntu 8.04?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by ljlhy on 2008-06-09
Guys, how to overlock cpu in Ubuntu 8.04?

---

### Post by gr4nf on 2008-06-09
Usually, overclocking is done at a lower level than the OS. Try the BIOS, or, if the option is not available there, just get a new ocillator and replace the old one on your motherboard.

---

### Post by ibuclaw on 2008-06-09
Usually you do this in your BIOS. Although sometimes it may not be obvious to you as of what function controls this at first.

As CPU clock speed can be distinguished as one of two things:

A) CPU Clock Speed (ie: change settings from 1.8Ghz to 2.5Ghz)
or
B) Bus Clock Speed (ie: change settings from 100Mhz to 166Mhz)

If you know which motherboard you own, download the PDF manual from the manufacturers' site.
That may prove to be of great use to you.

Regards
Iain

---

### Post by ljlhy on 2008-06-09
I have overlocked from 1.8 to 2.4 in BIOS actually, cpu apprars to run at 2.4 in WinXp but 1.8 in Ubuntu, weired!

---

### Post by stalkier on 2008-06-09
> **ljlhy said:**
> I have overlocked from 1.8 to 2.4 in BIOS actually, cpu apprars to run at 2.4 in WinXp but 1.8 in Ubuntu, weired!

That is strange. Mine is OC'ed from 1.29 to 1.54 and shows 1.54 in Ubuntu. Not sure of why it is showing wrong in your system. ?????? Sorry.

---

### Post by Golem XIV on 2008-06-09
I thought overlocking was something you did with a sewing machine ;-)

Overclocking is OS-independent, as mentioned.  The clock and bus speeds are set long before the OS even begins booting.  So, in Ubuntu you overclock the same as in Windows, by setting the bus speed or multiplier higher through BIOS setup or by playing with the jumpers on the motherboard.

---

### Post by gr4nf on 2008-06-09
> I have overlocked from 1.8 to 2.4 in BIOS actually, cpu apprars to run at 2.4 in WinXp but 1.8 in Ubuntu, weired! 

This is strange. Anyhow, it doesn't really matter what the OS says it's running at. If it's set to 2.4 in the BIOS, it's running at 2.4. My favorite method of assurance is booting into UBCD (look it up online) and running a CPU test.

---

### Post by Dr.Ninethousand on 2008-06-19
you may be looking at it while it's stepped down..  try running a heavy program and checking if the frequency goes up..

---

### Post by dracule on 2008-06-20
why does windows have "live" overclocking? I was reading that if your BIOS doesnt support it, you can get software that *may* help you.

---

