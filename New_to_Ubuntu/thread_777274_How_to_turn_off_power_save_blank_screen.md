---
title: "How to turn off power save blank screen"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by akparker on 2008-05-01
running xubuntu 7.10 on hp desktop pc 

it appears to go into a power saving mode, blanking the screen (like a screensaver)

wiggling the mouse wakes it up, and doesn't seem to affect performance, but it is annoying

i installed gnome-power-manager from the terminal but i can't get that sw to do anything.

any suggestions?

a secondary question: in general, when you install sw via terminal, how do you get it to appear in the applications menu?

thanks,
akp

---

### Post by tyroeternal on 2008-05-01
The screen going black is actually the screensaver.  There should be a screensaver option in the settings menu that should clear up the screen going blank.

As far as getting applications added to the menu, I'm not sure about xfce.  You could try to follow [this]("http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/") to edit it manually or (I'm at work so I cant verify this) Preferences -> Behavior -> Edit Menu

Hope this helps!

---

### Post by dreadlord_chris on 2008-05-01
There are a few lines that need to be added to xorg.conf to keep the monitor from *powersave* blanking:
open a terminal...
```

sudo nano /etc/X11/xorg.conf

```
first change, look for the **Section "Module"** and find **Load "extmod"**
you need to change this too:
```

SubSection "extmod"
	Option		"omit DPMS"
EndSubSection

```
next you'll want to scroll down to **Section "ServerLayout"** and add the following lines:
```

	Option		"BlankTime"	"0"
	Option		"StandbyTime"	"0"
	Option		"SuspendTime"	"0"
	Option		"OffTime"	"0"
	Option		"NoPM"		"True"

```
save the file and resart X - ctrl-alt-bksp
You monitor should now stay on until you **physically** turn it off..

HTH

p.s. **Note:** the screen blanking has **nothing** to do with screensavers. This can easily be shown by **not** making the changes above while setting a screensaver that *actually* displays something - you'll find the scrren still goes blank after a while. I discovered the above changes due to this very behaviour.

---

### Post by akparker on 2008-05-01
**dreadlord_chris**: yes, i noticed it was not the screensaver by the same experiment.

i'll try your process when i get home later

**tyroeternal**: thanks for the advice about adding sw to the apps menu. i'll try that as well.

thanks,
akp

---

### Post by akparker on 2008-05-01
also, is there a forum (here or elsewhere) dedicated to xubuntu?

thanks,
akp

---

### Post by akparker on 2008-05-01
problem solved ... thanks for your help.

akp

---

### Post by dreadlord_chris on 2008-05-04
> **akparker said:**
> problem solved ... thanks for your help.

akp

You're quite welcome...

---

### Post by koodough on 2008-11-12
THANK YOU so much. I was in a tight crunch getting xubuntu in a kiosk mode to play a slideshow.
:KS :KS
```

SubSection "extmod"
	Option		"omit DPMS"
EndSubSection

```

AND

```

	Option		"BlankTime"	"0"
	Option		"StandbyTime"	"0"
	Option		"SuspendTime"	"0"
	Option		"OffTime"	"0"
	Option		"NoPM"		"True"

```

Could find a ** Load "extmod"** in my xorg but no error when adding your code

THX

---

### Post by aimtb50 on 2009-01-23
Dear,

i could not find server layout in my xorg.conf

Should I writ a new section?

Regards,

---

### Post by deadmnky on 2009-02-19
thank you dread that was one of those annoying things i decided to fix today and you post helped on the first look

---

### Post by theozzlives on 2009-02-19
It annoys me to. Go to System > Preferences > Screen Saver and un check "Activate screen saver when computer is idle, or pick a screen saver (I like the floating Ubuntu, I set it to 20 mins). Then click Power Management and move the slider to never on blank screen. Then close, close and you're done.

---

### Post by deadmnky on 2009-02-23
> It annoys me to. Go to System > Preferences > Screen Saver and un check "Activate screen saver when computer is idle, or pick a screen saver (I like the floating Ubuntu, I set it to 20 mins). Then click Power Management and move the slider to never on blank screen. Then close, close and you're done.

i had done that but it still went to a blank screen. dreads solutions fixed it for me though now my monitor does not turn off at all unless the power is pushed. just how i like it.

---

