---
title: "Sluggish Graphics, ATI Radeon X1650"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by noahTHEpurdy on 2008-04-29
Hey all!

I'm relatively new to the Linux world, keep that in mind with the responses here.

With the new release of Hardy, I decided to do the switch from Vista to Ubuntu on my machine. Everything looks golden so far, except for the video drivers it seems.

My card is a PCI Express PNY Radeon X1650. 

I tried with the drivers that came with Hardy, and scrolling in Firefox and things like chess pieces moving were incredibly sluggish, choppy even. I then installed the drivers directly from ATI (Ran the .run file they have for download and did nothing more, though I read about aticonfig?), to no avail as I suffer from the same sluggish graphics.

HELP! I beg of you, I'm really liking Ubuntu, just would like to get this issue sorted out.

---

### Post by noahTHEpurdy on 2008-04-29
No one? I can't possibly be the only one experiencing sluggish graphics with an ATI card, can I?

---

### Post by U83RMENSCH on 2008-04-29
Try this, this got mine working XD  ( Thanks to SOXS! )  ( i just installed via envy, worked great.. now if only counter strike will work :/ )

> **soxs said:**
> First remove all ati drivers you ever installed. Therefore use the tool envyng. get it via ```
apt-get install envyng-gtk
```
Run it from a terminal and selecte the option *delete ati drivers*
After that reboot. ```
sudo init 6
``` or ```
sudo reboot
```
After reboot, you have two options.
1. Either you install your driver with envyng-gtk or
2. do it the ubuntu way
Both will install fglrx driver v. 8.3

Doing the ubuntu way:
Go to System > Systempreferences > Restricetdrivers
Let the 8.3 driver install.
Afterwards go type into a terminal:
```
cp -vf /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_vesa
sudo nano /etc/X11/xorg.conf
```

Goto the "device" section (within your xorg.conf file) and where it reads vesa replace it with fglrx (do not forget " " ")
You might add some of these options which will enable/speed up 2D/3D acceleration:
```
        ## Driver / Performance Options
        Option          "XAANoOffscreenPixmaps" "1"
        Option          "TexturedVideo" "1"
        Option          "TexturedVideoSync"     "1"
        Option          "BackingStore"  "1"
        Option          "Textured2D"    "1"
        Option          "TexturedXRender"       "1"
        Option          "BackingStore"  "1"
        Option          "AccelMethod"   "EXA"
        Option          "DRI"   "1"
        Option          "DynamicClocks" "1"
        Option          "ForceGenericGPU"       "0"
        Option          "VideoOverlay"  "0"
        Option          "OpenGLOverlay" "0"
```

For AIGLX 2D acceration, make sure that it is enabled, so search for and if missing add this:
```
Section "ServerFlags"
        Option          "AIGLX" "1"
EndSection
```
Same here:
```

Section "DRI"
        Mode    0666
EndSection

```
Extensions required for full acceleration
```

Section "Extensions"
        ## For Textured2d and Textured XRender
        Option          "RENDER"        "1"
        Option          "XVideo"        "1"
        Option          "Composite"     "1"
        Option          "Damage"        "1"
EndSection
```

---

### Post by noahTHEpurdy on 2008-04-29
Thanks! However when I go to appearance and change the visual effects to turn the extra visual effects on, I still have the sluggish graphics. It runs just the same as with the ATI drivers directly from their site. Firefox scrolls slowly, and games like Chess just bog.

You would think a 512mb video card could handle a Linux GUI.

---

### Post by Saint Angeles on 2008-04-29
check out my mini ATI tutorial here!

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

Good Luck!

---

### Post by noahTHEpurdy on 2008-04-29
> **Saint Angeles said:**
> check out my mini ATI tutorial here!

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

Good Luck!

Thanks for the help, but I'm still getting this sluggishedness. Maybe being my first foray into Linux I'm expecting too much? The drivers are installed correctly, it just seems that any sort of 2d scrolling is slow.

---

### Post by Saint Angeles on 2008-04-30
> **noahTHEpurdy said:**
> Thanks for the help, but I'm still getting this sluggishedness. Maybe being my first foray into Linux I'm expecting too much? The drivers are installed correctly, it just seems that any sort of 2d scrolling is slow.
2d scrolling? like in firefox?

in firefox preferences, goto advanced->general... click on use autoscrolling.

or are you having compiz problems? try these settings in advanced desktop settings manager->general options->display settings:

---

### Post by park8b156 on 2008-04-30
As far as games go, if you don't have the ati control center.  Then go to applications> Add and Remove. Then select all available apps on the show menu. Then select all in the description panel then scroll till you find ati control center. Install, then look for it in the menus and see if you can tweak the controls till it work right for you.

---

### Post by noahTHEpurdy on 2008-04-30
> **Saint Angeles said:**
> 2d scrolling? like in firefox?

in firefox preferences, goto advanced->general... click on use autoscrolling.

or are you having compiz problems? try these settings in advanced desktop settings manager->general options->display settings:

Bear with me, as I'm at work, but I'd like to clearify all of this so when I get home I have time to toy around.

What is compiz?

---

### Post by robbiev80 on 2008-04-30
I'm running an ATI Radeon X1300 Pro and everything seems to be running well except my full screen video. It is much more choppy than it used to be with Gutsy. I had to turn off a bunch of special effects in order to make it watchable...but still. Something must have changed in Hardy to make it more "sluggish".

---

