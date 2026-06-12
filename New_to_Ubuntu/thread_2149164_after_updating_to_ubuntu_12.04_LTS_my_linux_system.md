---
title: "after updating to ubuntu 12.04 LTS my linux system will not recognize canon printer"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by encoopermd on 2013-05-27
think i need the "device uri" for Canon PIXMA MX870 printer/fax/scanner...thanks much, utter computer novice!

---

### Post by KnownSyntax on 2013-05-29
Have you made sure to also update/re-install any device drivers? Just because you have upgrading all of the software and the core system doesn't always mean that it has updated the drivers to reflect these new changes.

---

### Post by encoopermd on 2013-05-29
Thank you for answering...when I went to the Canon site and chose linux, it said there were no drivers available...then a smart computer fellow (unavailable this eve) sent me commands from a launchpad forum saying to do 3 codes: starting with "sudo add-apt-repository" and ending in "install cnijfilter-mx870series" and I followed that and things were updated... but apparently the printer needs a device uri somehow using the cnijfilter address (the cups one doesn't work) so it still will not work...any ideas appreciated...i really need to print out tonight for work...thanks much

---

### Post by pdc on 2013-05-30
Canon make a printer driver for your device; and a scanner driver;

to get the printer driver, go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100272302.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100272302.html)

the file come down as [COLOR="#008000"]cnijfilter-mx870series-3.30-1-i386-deb.tar.gz
[/COLOR]
can I suggest some commands to install this, assuming you select when you download it, to save it to your Downloads directory?

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf  cnijfilter-mx870series-3.30-1-i386-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd  cnijfilter-mx870series-3.30-1-i386-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

...........that should do everything and create an MX870 driver icon for you; the device URI may well be [COLOR="#A52A2A"]cnijusb:/dev/usb/lp0[/COLOR] but the install will have created that

_____________________________________________________________________________________________________________________________________

Canon provide a scanner programme called [COLOR="#0000FF"]ScanGearMP[/COLOR] and you can get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100273002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100273002.html)

it comes down as scangearmp-mx870series-1.50-1-i386-deb.tar.gz

so having done the above; if you close; and then open a terminal again; and use the commands

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf scangearmp-mx870series-1.50-1-i386-deb.tar.g[/COLOR]z

> [COLOR="#FF0000"]cd scangearmp-mx870series-1.50-1-i386-de[/COLOR]b

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

...........that should have scangearmp installed and run it with the command

> [COLOR="#FF0000"]scangearmp[/COLOR]

_____________________________________________

you can create a launcher.....to repeatedly launch it.........if you need guidance on how to do this, please ask

---

