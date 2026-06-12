---
title: "Intel Graphics Dashboard?"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by GUZZLR on 2014-02-19
Hello All...
I have converted an old Dell Latitude D630 to Ubuntu 13.10.
I see in settings this computer has an: Intel 965 GM x86/MMX/SSE2 graphics
Processor: Intel Core 2 Duo T7250 @2.00 GHz
Questions:  How do I access this graphics  to change settings?...How do I know if it is even activated?
Thanks for the help!

---

### Post by epikvision on 2014-02-19
Perhaps, you want to take a look at the [Intel Graphics Installer]("https://01.org/linuxgraphics/downloads/2013/intelr-graphics-installer-1.0.2-linux").

---

### Post by GUZZLR on 2014-02-19
> **epikvision said:**
> Perhaps, you want to take a look at the [Intel Graphics Installer]("https://01.org/linuxgraphics/downloads/2013/intelr-graphics-installer-1.0.2-linux").

The first step I did was paste into a terminal: 
wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | \
sudo apt-key add -

However, the code never completes so I can run the next code: 
wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | \
sudo apt-key add -

Am I correct in thinking these two codes must be done first, before I click on the "Graphics Installer for Ubuntu 13.04"?
Thanks for the help

---

### Post by varunendra on 2014-02-20
Hello Guzzlr!

> **GUZZLR said:**
> I see in settings this computer has an: Intel 965 GM x86/MMX/SSE2 graphics

This card should be natively supported by Linux kernel, most probably by i915 driver. To confirm that, you can take a look at the output of command -
```
lspci -nnk | grep -iA3 vga
```
Do you see a driver in "Kernel driver in use" line ? Post back the output if not.

And what kind of settings do you wish to change? Does the "Displays" option in "System Settings" not give you those options?

---

### Post by GUZZLR on 2014-02-20
```
[COLOR=#000000]And what kind of settings do you wish to change? Does the "Displays" option in "System Settings" not give you those options?[/COLOR]
```

Hello Varunendra...nice to hear from you again.
I'm at work now so I'll report back later on running the code to see about kernel support, and Ill report back

For your other question: I like to brighten the colors, among other things like gamma adjustment, etc.  For example, with Nvidea, i tend to "crank up" the digital vibrance, to make the colors really "pop"...similar to saturation with Intel HD graphics.
Thanks for the help

---

### Post by GUZZLR on 2014-02-20
```
guzzlr@LATITUDE:~$ lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
    Subsystem: Dell Latitude D630 [1028:01f9]
    Kernel driver in use: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)

```

Ran the code. here's what I get. so the i915 driver is in use as you said.  How do I access the graphics controller?
Thanks

---

### Post by varunendra on 2014-02-20
So you already have a suitable driver installed which can handle the tweaks you want.

Unfortunately, there is no control panel like Nvidia or ATI offer to do the tweaks, and there is probably no easy way to do that using Ubuntu's default tools.

In my 12.04 installation here, there is an item "Color" in "System Settings" that seems to be related with what you want to do (read "Color Management" in the "Help"). But it seems that calibrating the monitor will need you to install some tools *(from within repositories though, so that should be pretty straight forward)* before you can actually do the calibration. You can choose from some existing (or downloaded) "Color Profiles" to see if they suit your taste, but I seriously doubt they will.

So while you are not really 'stuck' with what you have, there is probably no quick and easy way either. And as should be already clear now, I personally have zero experience with that kind of tweaking on Ubuntu (I used to do that on Windows).

I didn't try very hard, but a quick search turns this up that seems more or less the only way to go when the Graphics vendor hasn't provided a control panel you want : [http://www.ubuntufieldmanual.com/?q=node/38](http://www.ubuntufieldmanual.com/?q=node/38)

Unless someone more experience can enlighten us on this, I'm afraid you'll have to do the experiment yourself and then probably you'll yourself be able to help us with the task.

---

