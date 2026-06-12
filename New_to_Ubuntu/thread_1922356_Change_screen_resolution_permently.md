---
title: "Change screen resolution permently"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by paul6 on 2012-02-08
I want to change Lubuntu 11.10 so it boots into a reasonable 1920x1080 instead of a huge 2560x1440 (which makes text unreadable). I have already read these resources - ([HOWTO: change resolution/refresh rate in Xorg ]("http://ubuntuforums.org/showthread.php?t=83973")), ([Ubuntu Wiki: X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution"))

However, I still don't know how to edit my "/etc/X11/xorg.conf" file, which is almost completely empty:

```

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

There isn't even an entry for my monitor. Any ideas or suggestions?

---

### Post by Rodney9 on 2012-02-08
So you don't see anything in 
> Menu - Preferences - Monitor Settings
as shown below ?

Do you have a nvida card ?, check 
> Menu - Preferences - Additional Drivers.

Rodney

---

### Post by paul6 on 2012-02-08
> **Rodney9 said:**
> So you don't see anything in 

as shown below ?

Do you have a nvida card ?, check 


Rodney

Hi Rodney,

I do have that menu, and I can manually change the resolution to what I want (1920x1080), however I want to make it the default resolution upon startup.

My computer graphics card is a Nvidia Geforce 8800GT.

EDIT - I used an alternate solution. I followed [these instructions]("https://wiki.ubuntu.com/X/Config/Resolution#Setting_XRandR_changes_persistently") to make an .xprofile file that would change my resolution automatically upon login.

---

