---
title: "Display link / Signing drivers"
date: 2020-12-22
forum: New to Ubuntu
---

### Post by ahpitre on 2020-12-22
Recently installed Ubuntu 20 on my laptop. I have a USB Type C Docking station from Pluggable, uses the Display Link Ubuntu driver to correctly make my 2 monitors work. The Display Link driver is not signed, when I try to install it it doesn't work if I leave UEFI enabled in the BIOS. When I disable UEFI Display Link works correctly. Is there a way to sign the drivers so they can work with Ubuntu even if UEFI is enabled? I was thinking about signing -> restart -> add MOC certificates -> restart, test, if it works, reboot and enable UEFI in BIOS. Basically, disable UEFI just to get MOC to add signed driver to kernel.

---

### Post by CelticWarrior on 2020-12-22
You're going at it the wrong way.

What prevents unsigned drivers from loading is Secure Boot, not UEFI. Yes, Secure Boot is a feature exclusively of UEFI, so when you change to Legacy it automatically doesn't and can't have Secure Boot. But you want UEFI mode anyway, **just disable Secure Boot.**

And yes, you can use mokutils to sign the drivers yourself but NO, you don't change anything to do that. Better and way more convenient is to disable Secure Boot.

---

