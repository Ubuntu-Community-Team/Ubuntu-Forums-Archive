---
title: "screensaver"
date: 2011-05-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by trufflesdad on 2011-05-28
Cannot find the screensaver config file..Any help welcome..

---

### Post by seeker5528 on 2011-05-28
No screensaver appears to be a Gnome 3 thing.

What that means for the future of screensavers in Unity, Gnome Shell, and the Gnome fallback environment seems to be uncertain.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-screensaver](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-screensaver)

Later, Seeker

---

### Post by seeker5528 on 2011-07-01
Finally got fed up enough with the screensaver/blanking situation to look at this further.

If you uninstall gnome-screensaver and, if not already installed, install xscreensaver, xscreensaver-data, and any additional xscreensaver-* packages that sound like they may provide screen savers you want, you can use xscreensaver to provide the screensavers.

There may be additional hacks necessary to make 'Lock Screen' and other related menu items work and instructions you can find around the net for doing this may or may not be current for what's necessary with Gnome 3 stuff, but I expect more people probably don't care about that than do.

If you can't find the configuration for 'Startup Applications' you can run it from the command line with the command ```
gnome-session-properties
```

Then click the '+Add' button to add an item for xscreenscreensaver that uses the command ```
xscreensaver -no-splash
``` for the command to start it.

I'm logged in to a Lubuntu session at the moment and the menu item for xscreensaver configuration shows at 'Preferences --> Screensaver'.

I suspect this would show up in Unity if you right click the application icon on the launcher and click 'System' on the jump menu.

If you can't find it on the menu you can use the command ```
 xscreensaver-demo
``` to get to the configuration.

X has it's own default for putting the monitor into power saving mode after some number of minutes so at the login screen X will be controlling that, once you log in and xscreensaver runs it takes over until you log out. 

Later, Seeker

---

### Post by dsfitzpat on 2011-08-20
For me, the inability to set things like a screensaver is the biggest issue with Gnome 3 at the moment.  At least it sounds like the Ubuntu devs are thinking about it.  Is there any word on whether Ubuntu has people working on repopulating the list of system settings GUIs?
From a number of threads I've read it sounds like Ubuntu is getting a lot of complaints for things that have been decided upstream by Gnome.  Bringing back some of the standard system settings interfaces (theme customisation - and general desktop appearance settings - is another that comes to mind) might be a good way for Ubuntu to start getting people back onside.

---

### Post by cariboo on 2011-08-21
> **dsfitzpat said:**
> For me, the inability to set things like a screensaver is the biggest issue with Gnome 3 at the moment.  At least it sounds like the Ubuntu devs are thinking about it.  Is there any word on whether Ubuntu has people working on repopulating the list of system settings GUIs?
From a number of threads I've read it sounds like Ubuntu is getting a lot of complaints for things that have been decided upstream by Gnome.  Bringing back some of the standard system settings interfaces (theme customisation - and general desktop appearance settings - is another that comes to mind) might be a good way for Ubuntu to start getting people back onside.

I wouldn't hold my breath, as Canonical doesn't have the resources to rewrite many of the Gnome 3 apps, and add extra functionality. The best thing to do would be to start threads on the gnome development mailing list to try and get the changes you want. Keep in mind, you need to create well thought out posts and not just a rant about why some things don't work.

---

### Post by wedderburn on 2011-08-21
Are screen savers actually of any use in this day and age, i mean back when everyone had a crt monitor they were needed but most computers have a lcd screen. Why the waste of resources on something most people don't need, in todays age having a moving picture on your screen is a bit of a gimmick more than anything.

---

