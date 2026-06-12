---
title: "UBUNTU 15.10 for NewBY"
date: 2015-11-19
forum: New to Ubuntu
---

### Post by peterlessjim on 2015-11-19
Please excuse my ignorance, I am running windows xp on an oldish system, attempted to install U15.10 from USB both 64 and 32 both fail, when attempting to 'try' it get to desktop screen then either freezes of reboots and USB is not seen by BIOS. The system is GF7050 MB, LE1620 2.4GH AMD 64, 3GB RAM, 1 x 200gb sata, 1 x 200gb IDE, realtek 8185 wireless, CD,FLOPPY, and thats about it. What I firstly perceived as an easy path seem to be prone with problems. Tried the hit character on startup got to try,install,boot first screen no function keys indicated at bottom, got to that screen somehow where it displays all Fkeys in menu but none seem to work. I am presuming I am at fault here but would be greatful of some simpletun help at this stage

---

### Post by Vladlenin5000 on 2015-11-19
Hi and welcome.

If your MB is [this one]("http://www.biostar.com.tw/app/es/mb/introduction.php?S_ID=311") and you have no additional graphics card you're running with an infamous onboard NVIDIA GeForce 7050 GPU.
Assuming the aforementioned specs you should:

1. Prefer 64-bit;
2. Use *nomodeset* -> Press any key as soon as you see the keyboard and human figure (or something like that), select language and then press F6 and select nomodeset.
3. Try Ubuntu and proceed with the installation as usual.

Obs.: If you're burning your USB from Windows I strongly recommend Rufus.

---

### Post by grahammechanical on 2015-11-19
With onboard graphics of 512 MB shared from the system memory RAM, I would suggest Lubuntu. And when installing do not tick the box "Install third party software." That will get you a Nvidia driver and the latest Nvidia drivers may not support that video adapter any more. So, if you get Ubuntu installed and it does not seem as fast as you would like consider this

[http://lubuntu.net/](http://lubuntu.net/)

Regards

---

### Post by Vladlenin5000 on 2015-11-19
> **grahammechanical said:**
> With onboard graphics of 512 MB shared from the system memory RAM...

With 3GB of total System RAM, whatever amount must be reserved for the integrated GPU - which, BTW, is way less than 512MB, 64MB is more likely - makes no difference at all. There's no need to "downgrade" here ;-)

And, again assuming the specs I Found are correct, the required nvidia driver to make something out of that horrible GPU is the legacy 304 and it's probably a must because, from experience, that chip isn't supported by nouveau.

---

### Post by peterlessjim on 2015-11-20
Gents thanks very much for your prompt reply it, just to update a few items, I tried rufus it created a zip device(removable) and would not boot, so went back to pendrive and created a 64 ubuntu as suggested, this now boots from the usb stick. VLADLENIN suggested pressing key when keyboard etc. shown, this never occurs it comes up if I press a key immediately after boot attempt to a UBUNTU screen with 5-6 menu opion ie try, install, advanced all in black and white, the next item select language never appears I select try, ie put cursor on try press F6 it boot to desktop cursor is able to be moved for some period then everything freezes and requires a reboot, cannot go to any item without it freezing. Thanks for the help hope this provides some other clues.

---

