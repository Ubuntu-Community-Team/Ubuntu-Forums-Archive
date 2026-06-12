---
title: "HP bios wont recognise usb boot stick"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by carlmather2001 on 2014-01-09
I bought a new HP laptop - pavillion 15-n008tx, because my old DELL bit the dust. I have a usb stick always ready to go with a backup OS reload, just in case. I've used this latest stick reload a few times on 2 different machines and worked just fine.
I plugged it into the new HP, reset bios boot order but no go.
I tried various changes in bios - enable 'legacy', but still no go.
I called "help desk" and they told that they couldn't assist me to 'downgrade' the operating system. I pointed out that its only the bios I'm having trouble with, but of course they stuck with their line.
What the heck do I do to get past this block?
At the moment I'm using windows and, after 6 years of using Ubuntu, its driving me crazy!

---

### Post by sudodus on 2014-01-09
Hi,

I think I know your problem. This Christmas I had a similar experience with fairly new HP laptops. First of all, you need to decide if you want UEFI or classic BIOS.

If you want UEFI only some new and 64-bit versions of linux will work, for example Ubuntu 12.04.3 and later, so I'd recommend some flavour of Ubuntu 12.04.3 or Ubuntu 13.10. Otherwise (with BIOS) you can ran almost any version and flavour of linux, as long as there are drivers for the hardware.

But back to booting: Some pendrives are better booters, and I had better luck with them to boot HP laptops, while other pendrives boot several other computers, but not these HP laptops. The cheap and slow ***Sandisk Cruzer Blade 4GB*** is a good booter.

See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL]

[Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

Anyway, a good booter like Sandisk Cruzer Blade 4GB can be used directly with the OS you want, or indirectly to chainload another pendrive with the OS you want.

Good luck :-)

---

