---
title: "[lubuntu] PPC MAC G4 733Mhz LIVE NO BOOT"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by Copper_City on 2013-10-05
Greetings, I downloaded and burned the standard 13.04 PPC image off the lubuntu site. My Mac is a G4 733Mhz Quicksilver with 40gb drive and 1gb of ram. When I boot to the CD and try to run the live version. I get the normal splash screen start up with the dots and lubuntu name after that. the splash screen go's away and the computer just sits there. The display flash's no input and the optical drive will spin down. Only way out is pushing the reset button. I tired the diff graphics option and even tired the commnds listed on the live-help  all have the same effect.

Any clue what's going on?

---

### Post by Kevin McCready on 2013-10-06
bump
c'mon guys, new member! I'd help if I could. Good luck

---

### Post by heir4c on 2013-10-06
Don't use 13.04 (End of Life: jan 2014).
Use 12.04 (5 year support):
Ubuntu:
[http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/releases/precise/release/ubuntu-12.04-desktop-powerpc.iso)
Lubuntu:
[http://cdimage.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-desktop-powerpc.iso)
Alternate Lubuntu (text-based):
[http://cdimage.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-alternate-powerpc.iso)
Other iso:
[https://wiki.ubuntu.com/PowerPCDownloads/](https://wiki.ubuntu.com/PowerPCDownloads/)

Burn your iso on a low speed 2x or 4x. Burn it as 'image' not as 'data'.

---

### Post by Lars Noodén on 2013-10-06
Do you by chance have radeon graphics?  If so you will need to use this line at the Yaboot prompt, befor the splash screen:

[live video=radeonfb:1024x768-32@60 ](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/PPC)

Substitute your actual screen resolution for the 1024x768 part.

---

### Post by Copper_City on 2013-10-06
heir4c, Thanks, I am burning the image at 4x with verify written data this time.  I will post back shortly when it's done and try it out.

Lars Nooden, Thanks, According to "About this mac" it has a Geforce 2MX card.

---

### Post by Lars Noodén on 2013-10-06
Ok but only the parts of Lubuntu 12.04 that overlap with Ubuntu 12.04 are actually LTS.  The first LTS for Lubuntu as a whole will be the upcoming 14.04.

---

### Post by heir4c on 2013-10-06
> **Lars Noodén said:**
> Ok but only the parts of Lubuntu 12.04 that overlap with Ubuntu 12.04 are actually LTS.  The first LTS for Lubuntu as a whole will be the upcoming 14.04.

ThX, good to know.

---

### Post by Copper_City on 2013-10-06
Still no go, now have a different set of problems with Lubuntu 12.04. No splash screen just a black screen northing on it, just hangs there, DVD drive spins down after a bit. I get the Yaboot prompt hit enter, it flash's to the white screen then go's black then northing. Any more ideals?

[COLOR=#ff0000]**Edit:**[/COLOR] Should be noted the the Apple in question works fine with OS X. It has a fresh install of 10.4 and 9.2.  I also have a Dell PII 450Mhz that booted lubuntu 13.04 just fine. My main PC runs Mint 15 as it's only OS.

---

### Post by heir4c on 2013-10-06
A white screen is most of the time an graphics issue. I have not install Ubuntu on a PowerPC so I don't now it's different of a PC but I think is the same and you can use boot arguments like "nomodeset". Than linux use the default vesa driver. (basis/low configuration for all the graphics).

---

