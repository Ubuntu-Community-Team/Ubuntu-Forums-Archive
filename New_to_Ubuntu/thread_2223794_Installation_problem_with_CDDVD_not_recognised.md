---
title: "Installation problem with CD/DVD not recognised"
date: 2014-05-12
forum: New to Ubuntu
---

### Post by Dave327 on 2014-05-12
Hi I'm Dave and new to Linux.
I'm attempting to change my laptop and 2 desktops to Ubuntu 14.04, however, I have the following problems:

Laptop - AMD 1.2GHz with 1Gb RAM - replaced Windows XP with 32 bit 14.04. Installed fine, but is very slow.

Desktop 1 - AMD 1.7GHz and 2Gb RAM - installed 32bit alongside Windows XP, however, the DVD drive isn't recognised and it installed a floppy drive ( which the PC doesn't have) in it's place. I reinstalled with the same result. Windows still recognises the DVD drive.

Desktop 2 - Intel Dual Core and 4 Mb RAM - installed 64 bit alongside Windows 8.1 - this time no DVD and no floppy.

Any advice or remedy would be appreciated.

---

### Post by ibjsb4 on 2014-05-13
> [COLOR=#000000]Laptop - AMD 1.2GHz with 1Gb RAM - replaced Windows XP with 32 bit 14.04. Installed fine, but is very slow.[/COLOR]

Using a different desktop may speed it up.  I would suggest adding flashback to your current install.

```
sudo apt-get install gnome-session-flashback
```

And choose the flashback-metacity desktop at boot (the login screen) by clicking on the icon.

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by Vladlenin5000 on 2014-05-13
How's the DVD not recognized? It doesn't show like in Windows. It'll show up only if there's some media inserted.

---

### Post by Dave327 on 2014-05-13
Hi - thanks. I've decided to get the desktop 2 running properly 1st. I think I was a bit ambitious doing 3 at once! However, I will take your advice and let you know how I go.

---

### Post by Dave327 on 2014-05-13
Thanks, I am new! I'm concentrating on desktop 2 1st - the floppy disc appears on the left, so I assumed the DVD would.
When I insert a CD with a .PDF file it works fine. However, when I put in a DVD movie, the screen goes blank and the the error "no signal detected" is all I get. Something simple as well, I hope.

---

### Post by mastablasta on 2014-05-14
that is correct in that case the DVD/CD is not automounted.

however you can still mount it and you can view it. to view it you need to install lidvdcss library: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

it will also help if you install ubuntu-restricted-extras found in software center (if you haven't done it already during OS install)

also for the first mashicne (laptop) i suggest you use Xubuntu or Lubuntu instead. unlike default Unity interface they do not use 3D acceleration just to draw windows. flashback suggestions is also aiming to adress this concern. 

btw - how to automount DVD: [http://askubuntu.com/questions/256587/how-to-mount-dvd-rw-drive-create-mount-point](http://askubuntu.com/questions/256587/how-to-mount-dvd-rw-drive-create-mount-point)

---

### Post by Dave327 on 2014-05-14
Totally awesome - all good and I'm getting up to speed - Thanks for taking an interest.
Cheers, Dave

---

