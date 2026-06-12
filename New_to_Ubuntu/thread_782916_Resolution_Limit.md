---
title: "Resolution Limit?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by GTO7995 on 2008-05-05
Hey,

I just shifted to Ubuntu (Hardy) recently and I'm really enjoying the experience. I wanted to customize my desktop further but I can't get past 1280 x 780 wide (1280 x 800 is the highest but it cant show some parts of my screen). I have an Intel D865BGF board, 2Gbs RAM on a Pentium 4 3.0Ghz processor. My monitor is a 17-incher generic CRT (which is not even in widescreen). When I was using XP, my resolution was set to 1600 x 1200. Now(in Ubuntu), I'm using 1024 x 768. Any workaround to set it to a higher resolution or is this the limit of my hardware?

Just ask me if there any info needed.

TIA

---

### Post by hyper_ch on 2008-05-05
You can add a new resolution in your /etc/X11/xorg.conf

---

### Post by pro003 on 2008-05-05
usually ubuntu gives you the max resolution of your hardware i.e crt monitor max resolution... mine is tft at 1680x1050 and that's the maximum, and when i try to set above that resolution screen starts to flicker and the picture goes awful...

Did you install the driver for your graphic card? And how did you do it?

---

### Post by GTO7995 on 2008-05-05
Will I have to use the terminal for this? What commands do I have to put? I'm really a noob at this.

*edit
@pro003: I think I'm using the latest driver. I checked synaptic and it says that I have this> X.Org X server -- Intel i8xx, i9xx display driver ver. 2:2.2.1-lubuntu-12

---

### Post by pro003 on 2008-05-05
> **GTO7995 said:**
> Will I have to use the terminal for this? What commands do I have to put? I'm really a noob at this.

do this in terminal:

```
sudo gedit /etc/X11/xorg.conf
```

if you don't know what ur doing post the output here...

---

### Post by SumoRoller on 2008-05-05
I installed it this weekend and after updating my video card, Nvidia 7800 GTX, I am able to get 1900 x 1200.

---

### Post by GTO7995 on 2008-05-05
I got this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by phr0ze on 2008-05-05
Yeah, They really nerfed the xorg file and this is a VERY common problem in Hardy. I use a switchbox and of course hardy doesn't recognize the monitor. There still needs to be a GUI to define resolutions.

---

### Post by GTO7995 on 2008-05-05
I guess I'm stuck with 1028x768. I hope they find a workaround soon.

---

### Post by bodhi.zazen on 2008-05-05
> **GTO7995 said:**
> I guess I'm stuck with 1028x768. I hope they find a workaround soon.

Just some information (I feel your pain).

Basically this is now an issue with xorg and not limited to Ubutnu. For example, Fedora 9 preview there is no /etc/X11/xorg.conf. I am not sure how the new xorg can be manually configured, but this is what you would have to do.

You can try :```
gksu displayconfig-gtk
```If you make a mistake, you will need to fix X with ```
sudo dpkg-reconfigure xserver-xorg
```Now the problem is that you need to know what to add to /etc/xorg.conf and I have tried hand writing a configuration and some of the old options do not work.

Try something like this :

```
Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
       DefaultDepth 24
       Subsection "Display"
          Depth       24
          Modes       "1600x1200" "1280x1024" "1024x768" "800x600"
       EndSubsection

EndSection
```1. Add in your desired resolution on the Modes line.

2. Sometimes you need to add a single entry for a higher resolution then you intend to use.

3. Sometimes you need to reduce your display depth to 16

==========

The other thing to try, xrandr

In a terminal enter xrandr to display your options. Then 
```
xrandr -s 1600x1200
```

---

### Post by GTO7995 on 2008-05-05
^Thanks for the suggestions. 

Somehow, I got somewhere with this command.
```
gksu displayconfig-gtk
```
from 60Hz I got my 1024x768 reso to 75Hz. Unfortunately, It was back to 60Hz when I rebooted. I tried 1280x1024 @60Hz and it recognized it when I clicked Test. It did show the resolution correctly so I clicked Keep Configuration. When I applied the setting, it asked me to log off so I used the ctrl-alt-backspace shortcut. When it returned, It still shows the old 1024x768 resolution.

*edit

Finally, I got to work at 1280x1024!! :D I'm not sure what I actually did to fix it but it involved changing the monitor type and playing around with the resolutions a bit.

Thanks to master Bodhi and to the others who helped. It may not have been my usual resolution but I'm happy with this much larger screen. Ubuntu rocks \m/

---

