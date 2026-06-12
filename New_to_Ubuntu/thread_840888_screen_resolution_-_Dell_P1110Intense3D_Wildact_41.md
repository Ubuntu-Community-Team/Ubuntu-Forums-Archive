---
title: "screen resolution - Dell P1110/Intense3D Wildact 4110 Pro"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by dgowans on 2008-06-25
I'm having issues getting my screen resolution set to anything useable.  I've got an older Dell workstation with an Intense3D Wildcat 4110 Pro video card and a Dell P1110 monitor with 8.04 installed.  I can't get anything better than 640x480 for my resolution.

I dug through the menus and added "Other, Screens & Graphics" to the Applications menu but I'm having no luck adding either the monitor or the video card - all configurations seem to fail.

Any nudges in the right direction would be most appreciated.

---

### Post by overdrank on 2008-06-25
> **dgowans said:**
> I'm having issues getting my screen resolution set to anything useable.  I've got an older Dell workstation with an Intense3D Wildcat 4110 Pro video card and a Dell P1110 monitor with 8.04 installed.  I can't get anything better than 640x480 for my resolution.

I dug through the menus and added "Other, Screens & Graphics" to the Applications menu but I'm having no luck adding either the monitor or the video card - all configurations seem to fail.

Any nudges in the right direction would be most appreciated.

HI and welcome, I have no personal experience with that graphics model but after searching for the specs you may change you default depth from 24 to 16 in your xorg. You can edit your xorg with the command ```
gksu gedit /etc/X11/xorg.conf
```
Example
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	[COLOR="Red"]Defaultdepth	24[/COLOR]
EndSection
```
Change the 24 to 16 then restart x with ctrl, alt, backspace keys then adjust your resolution.

---

### Post by dgowans on 2008-06-25
I edited the xorg.conf file to add the Defaultdepth line, but there are still no options to change the screen resolution to anyting other than 640x480 using:

System, Preferences, Screen Resolution

Other thoughts?

---

### Post by overdrank on 2008-06-25
> **dgowans said:**
> I edited the xorg.conf file to add the Defaultdepth line, but there are still no options to change the screen resolution to anyting other than 640x480 using:

System, Preferences, Screen Resolution

Other thoughts?

HI and are you using Hardy 8.04? Have you selected the correct driver for the graphics and monitor in Screens & Graphics?
Edit disregard the question as I reread your post and see that you have tried this.
I can not find anything info on the web for the driver so all I can suggest is using the vesa driver located under other in Screens & Graphics driver for the video card.

---

