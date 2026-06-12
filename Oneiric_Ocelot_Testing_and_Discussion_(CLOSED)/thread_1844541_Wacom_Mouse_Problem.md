---
title: "Wacom Mouse Problem"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Is Mise on 2011-09-15
With Oneiric my Wacom Mouse now defaults to absolute positioning instead of relative positioning, i.e. to click the top left corner of the screen, I have to move my mouse to the top left corner of the Wacom Pad.

I fixed this by setting org/gnome/settings-daemon/peripherals/wacom/cursor/is-absolute to false in dconf-editor, but a new Ubuntu user would definitely not be able to figure this out.

Anyone else experiencing this problem? I've filed a bug report about it here: [Bug #846509]("https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/846509")

---

### Post by Favux on 2011-09-15
Hi Is Mise,

lol  It's a feature not a bug!

Peter Hutterer wrote some basic Wacom tablet hooks into the gnome-settings-daemon quite a while ago.  I guess the change is finally hitting the distros.  This was in response to complaints about xf86-input-wacom dropping wacomcpl.  And in anticipation of a Gnome gui tablet front end.  Unfortunately development of the tablet gui seems to have stalled, see gnome-control-center:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Utilities](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=External_applications#Utilities)

Jason just realized a couple of weeks ago that the gnome-settings-daemon settings could trip up the uninformed.  See the little section he added to the mediawiki's Tablet Configuration:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#gnome-settings-daemon)

Looking like confusion will reign.  Once again proving no good deed goes unpunished.  ;)

---

### Post by Is Mise on 2011-09-15
Hi Favux,

I didn't have a problem with having to use dconf-editor to change the default, I just thought that for new users the default for the mouse should be relative positioning, as it was in previous versions of Ubuntu, and in Windows as well.

Also, Gnome 3 has a setting for Relative/Absolute tracking in the new Wacom settings dialog, but this only changes the tracking mode for the pen.

---

### Post by Favux on 2011-09-15
You're right, the Wacom tablet mouse/puck driver default is Relative Mode and that's what that key should be set to.
> Also, Gnome 3 has a setting for Relative/Absolute tracking in the new Wacom settings dialog, but this only changes the tracking mode for the pen. 
I haven't investigated the gnome-settings-daemon in my Fedora 15 install.  I really should see what's there.  Kind of wondering if Mode has a touch key and if it knows to set up tablet PC touch as Absolute and BambooPT as Relative.

I'm trying to think of a reason to keep my Natty install and failing.  So I'll probably upgrade it to Oneiric when Beta 2 comes out.  That's likely when I'll start looking into it.

---

### Post by Favux on 2011-09-16
Fedora 15 has the cursor key set to is-absolute also.

There will be a configuration panel UI in system-settings with GNOME 3.2.  In the meantime in addition to using dconf-editor to fix it you can use the gsettings CLI:
```
gsettings set org.gnome.settings-daemon.peripherals.wacom.cursor is-absolute 0

```

---

### Post by Is Mise on 2011-09-17
> **Favux said:**
> There will be a configuration panel UI in system-settings with GNOME 3.2.

That must be the one that's in Oneiric, since Oneiric will be released with GNOME 3.2. It only has settings options for the stylus though, as you can see in the attachment.

---

### Post by Favux on 2011-09-17
Ah. thanks for that.  And no options for puck obviously.

Tablet tracking mode is referring to the parent device i.e. the stylus obviously.  Which is why you can set eraser pressure too.  But apparently the gui doesn't handle any dependent devices yet.  Nice to see it appearing though!

Is the other option for Tracking mode *Tablet (relative)*?

Alright, I'll provided feedback on that too.

---

### Post by Is Mise on 2011-09-17
The other option is called "Touchpad (relative)"

---

### Post by Favux on 2011-09-17
Hmmm.  That's a little strange.  That is the Touchpad (i.e. BambooPT) default.  But it doesn't let you change modes and make the stylus relative if you wanted?  What does *All Settings* offer?  Any other choices?

---

### Post by Is Mise on 2011-09-17
No *Touchpad (relative)* changes the Stylus mode to relative, but it's oddly named since my tablet doesn't have a touchpad except for the the touch-ring at the top, which doesn't seem to have any GUI settings available for it.

*All Settings* just takes you back to the main GNOME System Settings dialog.

---

### Post by Favux on 2011-09-17
OK, so the Tracking mode option is actually active and lets you switch between Absolute and Relative Mode.  Clearly you're right and the relative option is mislabeled and should say Tablet (relative).  Actually both are mislabeled and should say:
Stylus (absolute)
Stylus (relative)
with eraser implied or alternatively:
Stylus/Eraser (absolute)
Stylus/Eraser (relative)
Folks shouldn't need to know that Tablet is equivalent to the parent device i.e. the stylus.

---

### Post by Is Mise on 2011-09-17
Yes, *Stylus (absolute)*/*Stylus (relative)* would be much clearer, or better yet, move the Tracking Mode setting to below the Stylus header and just say *Absolute*/*Relative*.

---

### Post by Favux on 2011-09-17
Good point.  That would be clearer.

---

