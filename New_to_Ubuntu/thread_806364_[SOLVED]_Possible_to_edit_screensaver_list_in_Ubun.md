---
title: "[SOLVED] Possible to edit screensaver list in Ubuntu8.04?"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by Gyrotwister on 2008-05-24
I'd like to set my screen saver to random but I don't want to see any mundane looking screensavers.  In short I'd like to delete the boring ones and leave the more exciting ones.  The "Screensaver Preferences" dialog doesn't seem to offer any options in this regard so I was wondering if there is a folder where they all reside so I can get in there and delete the screensavers I don't want.   

Has anyone tried this?  
Am I likely to break something if I play around with this?

---

### Post by sdennie on 2008-05-24
Once you have the screensaver set to random, you can hit Alt-F2 and type gconf-editor.  Then navigate to /apps/gnome-screen-saver.  If you double click on themes, you should be able to edit he list of screensavers that will be run while on random.

---

### Post by Vadi on 2008-05-24
An easier way to go about it is to install screensaver-settings, where you can just check off the screensaves you wouldn't like to see.

Get it from here: [http://getdeb.net/search.php?keywords=screensaver](http://getdeb.net/search.php?keywords=screensaver)

---

### Post by Gyrotwister on 2008-05-25
Thankyou Vor, that worked OK.  

Vadi, I see there is a Screensaver Settings package available for Hardy.  
Do you use it, does it work OK?  
Would I have to uninstall GNOME screen saver first before installing it?

---

### Post by Vadi on 2008-05-25
It works well, and you don't have to uninstall the gnome one, they can both can be installed at the same time.

---

### Post by eryksun on 2008-06-16
Vadi, 

I'm surprised you say the screensaver-settings program works well for you.  :confused:  The package installs xscreensaver, which overrides gnome-screensaver [undesired, IMHO]. The program itself has a bad bug; it changes the "cycle_delay" gconf key in "apps/gnome-screensaver" from an integer to a floating point value, which makes gnome-screensaver crash until you manually change the key back to an integer. :(

---

### Post by Vadi on 2008-06-16
I'm not sure what do you mean overrides, because I see both entires for it and the gnome one, and both work. Eitherway, report that bug to the developer, I'm sure he'll fix it (he's responsive to emails).

---

