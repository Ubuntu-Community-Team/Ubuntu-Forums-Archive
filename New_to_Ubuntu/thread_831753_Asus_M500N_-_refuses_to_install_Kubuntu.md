---
title: "Asus M500N - refuses to install Kubuntu"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-06-17
I have an Asus M3000N running XP. I have tried to boot from the live CD...it gets only part way through and stops. I have tried both installing within windows and doing a complete KDE4 install...neither of them have got very far....I installed the helper from the CD and still that does not work.

However I have got to the stage when it now asks me whether I want to boot undex XP or Kubuntu....but when I choose Kubuntu, same thing....it just hangs!

What am I doing wrong?

I have found that the Kubuntu folders are installed in Windows. When doing a verbose boot, the only error I can find is ACPI: Looking for DSDT in initramfs....error, file /DSDT.aml not found,

Then later SMP motherboard not detected,

and furhter down ACPI: EC: Look up EC in DSDT and then it stops.

I got a little bit further in the installation by starting the installed with ACPI workarounds...but then it kind of died after a while also...

PnPBIOS Resource structure does not contain and end tag is one of the errors that appears when you choose to install with ACPI workarounds.

Another error is Partman crashed - in the part install under the ACPI workaround.

I have manged to copy the syslog - see attached.

I have now managed to get Kubuntu running....but the screen seems very fragile and almost ghost like. I am guessing that when I close down, this install will disapear and I will have to start over.

---

