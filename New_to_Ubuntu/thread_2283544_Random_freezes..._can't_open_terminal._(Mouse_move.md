---
title: "Random freezes... can't open terminal. (Mouse moves but clicks don't do anything)"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by gerardo10 on 2015-06-22
Hello guys, I just recently installed Ubuntu Gnome 15.04 and noticed that every time I start working or browsing the computer just freezes and can't open terminal nor click with the mouse, although I can move it through the whole screen. The only way too unfreeze is to hard reset my PC. This happens every time, just minutes after I launch the OS & start working or browsing, as I said before.
 What should I do? Reinstall the whole OS?

---

### Post by Ty_Scheun on 2015-06-23
How much RAM does your computer have? What is the device model?

If your computer is old or just a 'low-end' computer, then you cannot load apps as easy

---

### Post by gerardo10 on 2015-06-23
I have 8gb Kingston Blu; Intel I7 2700, Asus motherboard P8Z77 -M PRO, NVIDIA 560 SE & 400 gb hdd for the OS. It runs smoothly on windows 7.
I built it 3 years ago, give or take.

---

### Post by Ty_Scheun on 2015-06-24
[FONT=courier new]Alright, definetly not a hardware because your computer might as well be called a gaming computer. [/FONT]

[COLOR=#333333][FONT=monospace]update xserver-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]xorg-input-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]evdev helps.[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Package for amd64 - [/FONT][/COLOR][http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/pool/main/x/xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.5.0+git20100822.990540fa-0ubuntu0sarvatt_amd64.deb)
[FONT=courier new]Try this, too. see if it works[/FONT]
[FONT=courier new]```
sudo apt-get update && sudo apt-get upgrade
```

Software Update ALSO helps.

[/FONT]&#8203;[ATTACH=CONFIG]262841[/ATTACH]

---

### Post by gerardo10 on 2015-06-26
Hello! Just about an hour ago I just updated and everything is running smooth now! Thank you!

---

