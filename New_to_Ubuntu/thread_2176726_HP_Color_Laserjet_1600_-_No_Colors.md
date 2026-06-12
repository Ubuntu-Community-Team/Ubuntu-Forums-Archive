---
title: "HP Color Laserjet 1600 - No Colors"
date: 2013-09-25
forum: New to Ubuntu
---

### Post by Glkanter on 2013-09-25
Hi Guys,

I finally bought a new cartridge for my HP Color Laserjet 1600 printer, so I connected it to my 64-bit 12.04 system for the first time.

The printer's test page prints colors, but the Ubuntu test page, and actual printing - from Firefox and LibreOffice are grey scale only.

Previous versions of Ubuntu worked fine, as I recall.

Any ideas?

Thanks!

---

### Post by DuckHook on 2013-09-25
Let's try simplest procedures first...

1. Do you have HPLIP installed?
2. If  so, are printer settings set to colour or black and white? Check by navigating to Print Settings>Color Options. The radio button for *HP EasyColor* should be "On". The option for *Print Color as Gray* should be "Off".

---

### Post by Glkanter on 2013-09-25
Yes, I have HPLIP installed.

But I can't find it on any menu.

The Ubuntu Software Center says to run it from a terminal. When I tried to run HP-info (just a guess), I got some error messages.

Please advise.

Thank you!

---

### Post by DuckHook on 2013-09-25
You need to run```
hp-toolbox
```If it is not installed, you will need to:```
sudo apt-get install hplip-gui
```*hp-toolbox* may need to be run with *gksudo*, but try it without first.

EDIT:
*hplip-gui* pulls down a ton of dependencies, primarily *QT*, which some people have an aversion to. Be aware that you will see some system bloat unless you already have *QT* installed for other apps.
/EDIT

---

### Post by Glkanter on 2013-09-25
I tried hp-toolbox.

The response was the sudo command in the exact format required.

I ran that, and followed your instructions.

Now I am printing in color.

And I can manage the print queue. Which is a capability I seemed to have otherwise lost.

Thank you so much!!

---

### Post by DuckHook on 2013-09-25
Glad it worked out.

You may also be interested in *hp-systray* which places an icon in your global menu system tray for easier future access.

---

### Post by Glkanter on 2013-09-25
I'm not sure what caused it, but I have an icon for the status service on my panel, and a menu option under System Preferences for the toolbox.

Thanks so much!

---

