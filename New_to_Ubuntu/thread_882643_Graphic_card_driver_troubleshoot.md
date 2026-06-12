---
title: "Graphic card driver troubleshoot"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by theblackphantom on 2008-08-07
Hey everyone 

I have a ATI radeon 9250 Graphic card & I need to install it. I was recommended to install EnvyNG and then this program will auto-install it with just a click. Well anyways I clicked "Install ATI driver manually" it downloaded some packages and made some configurations then said the operation was successful when I rebooted the pc. The display is all messed up a message popped up saying like "Your computer is running on low-graphic mode" :/ and the screen is now 800x600 :S. I'm really confused can anyone help me please


Note : My ubuntu version is hardy.

---

### Post by gjoellee on 2008-08-07
go to System->Administration->Hardware Drivers then enable the latest graphic card driver:)

---

### Post by theblackphantom on 2008-08-07
> **gjoellee said:**
> go to System->Administration->Hardware Drivers then enable the latest graphic card driver:)

I've gone there dude, but the list is blank :/.

---

### Post by gjoellee on 2008-08-07
hmmm....weird try this then:

right click on the desktop and go to change desktop background, then go to the visual effects tab, and click on either normal or extra and see if something happens (sometimes then doesn't download anything on first try)

if that doesn't work, check if your graphic card is supported yet

NOTE: Newer/newest cards may not supported before the next kernel updates come...

---

### Post by theblackphantom on 2008-08-07
> **gjoellee said:**
> hmmm....weird try this then:

right click on the desktop and go to change desktop background, then go to the visual effects tab, and click on either normal or extra and see if something happens (sometimes then doesn't download anything on first try)

if that doesn't work, check if your graphic card is supported yet

NOTE: Newer/newest cards may not supported before the next kernel updates come...

The desktop effects didn't work, But I checked the supported graphic cards list & yeah it is supported.

    *  Radeon 9250
          o Chipset: RV280
          o Driver: xorg-drivers
          o Notes: tested with Kororaa XGL Demo LiveCD 0.2

---

### Post by gjoellee on 2008-08-07
ok, before you do the command under read this: when you use this command you will come to a text based place, find and select the item in the menu that have something with **xorg** to do, when that is finished do a normal boot. This may fix your resolution...here is the code:

```
sudo shutdown now
```

---

### Post by gjoellee on 2008-08-07
when you are finished with the xorg thing go do the right click on the desktop and then select visual effects and select one of the visual effects

---

### Post by jrharvey on 2008-08-07
Just download [ENVY]("http://albertomilone.com/nvidia_scripts1.html") 

EDIT:the ling is in the work "envy"

---

### Post by gjoellee on 2008-08-07
I just found an envy site: [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by theblackphantom on 2008-08-07
It worked! I think that the driver is installed but am not sure. But listen the system is way too slow now. Is that normal :S ?

---

### Post by voteforpedro36 on 2008-08-07
> **theblackphantom said:**
> It worked! I think that the driver is installed but am not sure. But listen the system is way too slow now. Is that normal :S ?


Yeah, depending on the driver it installed and your computer, it can be slow. Run "gedit /etc/X11/xorg.conf", find the part that says "Device" and post what it says under "Driver". Mine looks like:

```

Section "Device"
        Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "RS300M AGP [Radeon Mobility 9100IGP]"
	BusID       "PCI:1:5:0"
EndSection

```

---

### Post by aman.agx on 2008-08-07
I had the same problem with my NVIDIA drivers. The restricted drivers from NVIDIA site installed fine the system also ran fine. But when I rebooted it it didnt work. but a small change solved the problem.

What I would suggest is install the restricted drivers. open /etc/default/linux-restricted-modules-common

it should look like this 
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```

make it DISABLED_MODULES="nv"

And reboot.


This should work. Hope it helps. 

Regards
Aman

---

### Post by theblackphantom on 2008-08-07
I gone again to the "Hardware drivers" & its still blank. I disabled the visutal effects & the system is fast again. But when before I did all that Envy process thing it was on normal effects & with a perfect speed am confused :S.

---

### Post by aman.agx on 2008-08-07
In my experience the restricted drivers were definitely better.

---

### Post by overdrank on 2008-08-07
> **theblackphantom said:**
> I gone again to the "Hardware drivers" & its still blank. I disabled the visutal effects & the system is fast again. But when before I did all that Envy process thing it was on normal effects & with a perfect speed am confused :S.

Hi and you may look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by theblackphantom on 2008-08-07
> **aman.agx said:**
> I had the same problem with my NVIDIA drivers. The restricted drivers from NVIDIA site installed fine the system also ran fine. But when I rebooted it it didnt work. but a small change solved the problem.

What I would suggest is install the restricted drivers. open /etc/default/linux-restricted-modules-common

it should look like this 
```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables both the nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```

make it DISABLED_MODULES="nv"

And reboot.


This should work. Hope it helps. 

Regards
Aman

I have entered in the Terminal 'open /etc/default/linux-restricted-modules-common' and the result was : 

> hadi@hadi-desktop:~$ open /etc/default/linux-restricted-modules-common
Couldnt get a file descriptor referring to the console
Could not get a file descriptor referring to the console


---

### Post by voteforpedro36 on 2008-08-07
> **theblackphantom said:**
> I have entered in the Terminal 'open /etc/default/linux-restricted-modules-common' and the result was :

Try "gksu gedit /etc/default/linux-restricted-modules-common". But "nv" respresents an Nvidia driver, whereas you have an ATI card.

---

### Post by theblackphantom on 2008-08-07
> **voteforpedro36 said:**
> Yeah, depending on the driver it installed and your computer, it can be slow. Run "gedit /etc/X11/xorg.conf", find the part that says "Device" and post what it says under "Driver". Mine looks like:

```

Section "Device"
        Identifier  "Card0"
	Driver      "radeon"
	VendorName  "ATI Technologies Inc"
	BoardName   "RS300M AGP [Radeon Mobility 9100IGP]"
	BusID       "PCI:1:5:0"
EndSection

```

It says 

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by theblackphantom on 2008-08-07
Hmmmm... If then all those replies & no one works. Then looks like my driver is not working well with Ubuntu because if then though I think it is installed but the system's speed is very slow :S. Although the system's processor is 2.02 GHZ & has a 1.25 GB of ram :S.

So there's a solution to speed it up while the driver is installed or I shall reset all the settings & run it without a graphic card ?

---

