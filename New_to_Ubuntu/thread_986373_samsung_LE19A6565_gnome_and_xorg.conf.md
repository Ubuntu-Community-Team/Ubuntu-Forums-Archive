---
title: "samsung LE19A6565 gnome and xorg.conf"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by islandstone on 2008-11-18
I'm just trying to get the video settings right for my TV's (samsung LE19A6565) PC input (d-sub) . it has a varied spec's list , under mode=vesa from 640x480 up to 1360x768, the "advised" setting for windows is 1440x900.
It's lcd , refresh 60hz

It kept dropping to input not recognised , initially from the moment i powered up . I have now managed to get into "safe mode" in gnome via booting to recovery mode , selecting to roconfig X , and logging in to safe mode.

If I do not select safe mode the secong I hit return after entering password , the TV drops to input not recognised again and that's that.

I'm guessing gnome is resetting the xorg.conf maybe? and if it is how do I stop it? 
And then how do I make sure the setings I need are always used , and can anyone confirm what I should use?

Oh my graphics is an onboard Intel 845 chip , works fine so far.

Thanks

---

### Post by islandstone on 2008-11-18
I noticed that xorg.conf.failsafe specified vesa drivers , so I replaced xorg.conf with xorg.conf.failsafe.

I can now boot up all the way and login normally , but I still only get something like 800x600. I edited xorg.conf with the following.

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Modes   "800x600"
	EndSubSection

Then changed 800x600 to 1440x900 saved and rebooted.
After login to gnome session , resolution is still 800x600 , and the resolution gui shows no options to change that.

---

