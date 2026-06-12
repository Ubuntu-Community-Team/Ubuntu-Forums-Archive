---
title: "Cannot activate Visual Effects"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by fredscripts on 2008-10-31
Hi!

Ubuntu 8.10. In Change Desktop Background, the Visual Effects tab is set to None. I've set it to Normal.

Then it started looking for drivers and finally couldn't load them properly.

My graphics card is a GeForce2 MX/MX 400 . Anyone knows if I could enable at least Normal effects?

Thanks!

---

### Post by sharkster2007 on 2008-10-31
Hiya fredscripts,

I have a similar problem too i have located the drivers manually (.deb) files my thread is at 
[http://ubuntuforums.org/showthread.php?t=964375](http://ubuntuforums.org/showthread.php?t=964375) 

I too seem to be getting ignored on this matter, I think I have the driver installed but can't activate it from the System>Administration>Hardware Drivers settings (Menu)

I hope I have helped you with the drivers issue. I f only we could activate it :-(

---

### Post by eternalnewbee on 2008-10-31
I hate to be the one to bring you bad news, but I found a thread where it's listed under cards that cannot handle 3D acceleration.
[http://ubuntuforums.org/showthread.php?t=961366&highlight=GeForce2+MX%2FMX+400](http://ubuntuforums.org/showthread.php?t=961366&highlight=GeForce2+MX%2FMX+400)
Another thread:
[http://ubuntuforums.org/showthread.php?t=955213&highlight=GeForce2%2C+MX%2FMX%2C+400+intrepid](http://ubuntuforums.org/showthread.php?t=955213&highlight=GeForce2%2C+MX%2FMX%2C+400+intrepid)

---

### Post by LegoAddict on 2008-10-31
So just to make sure:

You've checked System => Administration => Hardware Drivers?  You occasionally have to go do that manually.

You could also try looking at NVidia's website.  It's worth a shot.

From what I've heard, NVidia has very good support

I've also heard from friends that Ubuntu identifies the wrong drivers for them but I've never personally encountered that (oc, I'm ATI... never again...)

sudo apt-get update is always a good command to check, just to see if they're there.

And it's worth saying (I know you probably don't need to hear this and that this is a waste of electrons) that you need an internet connection.  Just saying.

---

### Post by cariboo on 2008-10-31
There are new legacy drivers coming that support Xorg 7.4 I just saw a notice yesterday in the maintainers blog, he said it would be at least acouple of days before the drivers would be in the repositories.

Jim

---

### Post by fredscripts on 2008-11-01
Thank you all very much for answering.

So I've installed from apt-get 
```

nvidia-glx-71 - NVIDIA binary Xorg driver
nvidia-glx-96 - NVIDIA binary Xorg driver
```

as a result from a search to "GeForce2". Nothing seems to happen.

After reading your posts I think I will give up trying it! What a pity though!

Thanks again!

---

### Post by diablo75 on 2008-11-01
If I were you, I'd chuck at least 20 bucks out there for a new video card.  The one you are using is really on the shallow end of the swimming pool.  Try ebay.

---

### Post by Kevbert on 2008-11-01
Try running [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") It will probably confirm if you can use compiz or if the card doesn't support 3D graphics acceleration.

---

### Post by fredscripts on 2008-11-01
Thanks for answering:
```

diffred@fredlab:~$ ./compiz-check


Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
 Driver in use:         nv
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

Would you like to know more? (Y/n) Would you like to know more? (Y/n) y

 The nv driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

diffred@fredlab:~$
```

It seems I would need to install some drivers. I dunno which are the good ones though and where to find them.

Yep, I should probably buy a new card, it's not the first time anyone suggest it to me haha.

Thanks for answering!

---

### Post by Kevbert on 2008-11-01
Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=1406&highlight=NV11&page=2") on the compiz forums.

---

### Post by fredscripts on 2008-11-01
> **Kevbert said:**
> Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=1406&highlight=NV11&page=2") on the compiz forums.

Thanks for the link. I've read the thread and seems I should edit the famous xorg file.

But mine isn't similar to the one of the last post of that link, I would have to do much more editing, which I have no idea how.

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Generic Keyboard"
#	Driver		"kbd"
#	Option		"XkbRules"	"xorg"
#	Option		"XkbModel"	"pc105"
#	Option		"XkbLayout"	"es"
#EndSection

# commented out by update-manager, HAL is now used
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#EndSection

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
        DefaultDepth    24
        SubSection     "Display"
            Depth       24
            Modes      "1280x960"
	    Virtual    1280 960
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

If you knew which changes should I do on my xorg I would be very grateful.

Thanks!

---

### Post by Kevbert on 2008-11-01
The important changes are shown in red
```
Section "Device"
	Identifier	"Configured Video Device"
       [COLOR="Red"]Driver          "nvidia"
       Option          "AddARGBGLXVisuals" "True"[/COLOR]
EndSection
```The other changes in that post are there to allow you to have different screen resolutions and depths.
It's probably best for you to back up your original xorg.conf file with
```
gksudo cp xorg.conf xorg.old
```prior to making changes, in case anything goes wrong. If it gives you new problems just copy the old file to xorg.conf.

---

