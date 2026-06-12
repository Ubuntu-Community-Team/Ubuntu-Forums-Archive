---
title: "Poor display in Heron 8.04"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by Rad1 on 2008-07-27
Hi.

Just installed Heron 8.04 desktop yesterday. Today you guys helped get me connected wirelessly.

Now I'd like to see if my display can be improved here. It's kinda pixelated .. not sure how to describe it .. but not nearly as good as in WXP.

I use onboard gfx .. laptop, 2 years old, Intel chipset. i915, nothing fancy, but still looks good in Windows. I'm talking about text in Firefox. 

Anything I can do about this?

Thanks.

---

### Post by Ryadt on 2008-07-27
Try enabling your graphic card in System > Administration > Hardware Drivers.

---

### Post by Catalyst2Death on 2008-07-27
If you go to System>Preferences>Screen Resolution, you should be able to select a resolution appropriate for you.  Otherwise, you may need to install drivers appropriate to your chipset.  I'm not sure about intel drivers, but vesa should at least give you the right resolution.

If your feeling adventurous, you can play around with xorg.conf:

```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
$ sudo nano /etc/X11/xorg.conf

```
find the section labeled Device: 

```
Section "Device"
        Identifier  "<name of intel chipset>"
        Driver      "vesa" #you may need to edit this line to read vesa
	BusID       "PCI:1:5:0"
EndSection
```

There should also be a section under Screen to manually edit your screen resolution.

If anything goes wrong when your playing around, X11 will likely crash, don't worry, make sure that your select recovery mode from your boot menu, then you can restore your old settings by copying xorg.bak to xorg.conf:

```
$ sudo cp /etc/X11/xorg.bak /etc/X11/xorg.conf
$ sudo reboot

```
alternately you can use start X after the copy command:

```
$ sudo startx
```

---

### Post by Rad1 on 2008-07-27
> Try enabling your graphic card in System > Administration > Hardware Drivers.
Nothing there. It's blank. Do I need to d/l some drivers?

> If you go to System>Preferences>Screen Resolution, you should be able to select a resolution appropriate for you. 
It is already set at the correct/proper rez > 1280x800.

Seems the display only looks krappy in Firefox.

---

### Post by Rad1 on 2008-07-27
I just d/l'ed & installed the package for Periodic table (very colorful) and it looks *beautiful* .. even better than what I've seen in Windows. So I'm a little confused why Firefox looked so krappy b4 .. altho now it doesn't look so krappy.

---

### Post by markbuntu on 2008-07-27
You can try changing the fonts in firefox preferences.

---

### Post by paul101 on 2008-07-27
try installing M$ fonts

---

### Post by Rad1 on 2008-07-27
I don't understand it, but now it looks good. Maybe cuz I d/'l'ed and installed all the patches (~40-ish) .. and at least one was for Firefox.

> try installing M$ fonts
How?

---

### Post by Rad1 on 2008-07-27
I have the Intel i915 chipset on my laptop. Do I need to (should I?) install chipset drivers, or gfx drivers?

Do the default vesa drivers support hardware acceleration?

---

### Post by zipperback on 2008-07-27
> **Rad1 said:**
> I don't understand it, but now it looks good. Maybe cuz I d/'l'ed and installed all the patches (~40-ish) .. and at least one was for Firefox.


How?



Open a terminal with:

```

Applications -> Accessories -> Terminal

```

Then use the following

```

sudo apt-get update && sudo apt-get install msttcorefonts

```


Follow the on screen prompts and it will install the fonts for you.

- zipperback
:popcorn:

---

### Post by Liakath on 2008-07-27
Dear Rad1,

> **Rad1 said:**
> I don't understand it, but now it looks good. Maybe cuz I d/'l'ed and installed all the patches (~40-ish) .. and at least one was for Firefox.


How?

Use synaptic and search for msttcorefonts. It is in the repos. It will install these additional fonts after downloading them during install.

Edit: zipperback you bet me to it.

Liakath

---

### Post by Rad1 on 2008-07-27
> Follow the on screen prompts and it will install the fonts for you.
Thanks Zip. Will do right now.

---

### Post by Rad1 on 2008-07-27
> All done, no errors.
All fonts downloaded and installed.

Wow. That was a major rush of terminal text.

How do I use them now?

---

### Post by zipperback on 2008-07-27
Also, you can try adjusting the font rendering method.

```


System -> Preferences -> Appearance


```


Now click on the "Fonts" tab and try each of the various rendering methods until you find the one which looks best for your display. You can also change the default fonts and such on this page as well.

I've included a screenshot for your reference.

[IMG]http://i257.photobucket.com/albums/hh216/zipperback1234/Screenshot-AppearancePreferences.png[/IMG]

- zipperback
:popcorn:

---

### Post by Rad1 on 2008-07-27
Thanks. I like Human-Clearlooks. And I changed Sans to Verdana.

It's looking pretty tight. Text in Firefox is worst part of visuals, expecially light text on dark background.

What about installing Intel i915 gfx/chipset drivers? (onboard gfx)

---

