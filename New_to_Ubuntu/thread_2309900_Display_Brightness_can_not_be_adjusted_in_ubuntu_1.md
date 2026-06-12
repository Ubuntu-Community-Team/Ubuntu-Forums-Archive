---
title: "Display Brightness can not be adjusted in ubuntu 14.04."
date: 2016-01-14
forum: New to Ubuntu
---

### Post by vigneshwaran2 on 2016-01-14
I am using ubuntu 14.04 in lenova B460e, I can't adjust the display brightness, if i adjust the brightness slider nothing happens. Please any one help with this issue. thank you.

---

### Post by leunam12 on 2016-01-14
Maybe this?

[http://askubuntu.com/questions/286516/how-do-i-get-the-brightness-control-working-on-a-lenovo-yoga-13](http://askubuntu.com/questions/286516/how-do-i-get-the-brightness-control-working-on-a-lenovo-yoga-13)

---

### Post by vigneshwaran2 on 2016-01-21
That didn't work for me dude.

---

### Post by vigneshwaran2 on 2016-01-21
I found a solution from the following link [URL="http://itsfoss.com/fix-brightness-ubuntu-1310/"]http://itsfoss.com/fix-brightness-ubuntu-1310/.
[/URL]Create the following file -> /usr/share/X11/xorg.conf.d/20-intel.conf
and fill this code.
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
But only works for intel graphics card.):P

Sometimes the system won't remember the brightness adjustment after restart, to solve this do the following:
Install the following script

sudo add-apt-repository ppa:nrbrtx/sysvinit-backlight
sudo apt-get update
sudo apt-get install sysvinit-backlight

Now everything works fine.

---

