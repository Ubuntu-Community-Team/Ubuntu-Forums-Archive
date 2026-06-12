---
title: "Gnome Services Launches Onboard"
date: 2011-10-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by TimHeckman on 2011-10-02
Hello,

Ran in to a bit of an interesting thing on Xubuntu 11.10.  I want to use the Gnome Keyring to manage my SSH pubkey passphrases.  This required me to have Xfce start some Gnome Services.  When enabling Gnome Services in XFCE "Sessions and Startup" the Onboard keyboard starts at every boot.

I've done a bit of looking around and have been able to find a way to stop this from happening.  Any thoughts?

-Tim

---

### Post by sffvba[e0rt on 2011-10-02
*Thread moved to **Ubuntu +1 (Oneiric Ocelot)**.*


404

---

### Post by Krytarik on 2011-10-02
Well, I don't know if this might be Oneiric 11.10 specific, or specific to running Gnome services in an XFCE session, but I would at first make sure that the key "/desktop/gnome/interface/accessibility" is not enabled in "gconf-editor". As, by now, that tool isn't installed by default anymore (damn it!), you might need to install it first.

Hope that helps!

---

### Post by TimHeckman on 2011-10-03
Thanks for the idea.  Yeah I needed to install gconf-editor to via apt.  Easy enough.  But as I expected accessibility is not enabled.  I've done a bit more digging and more searching online and have not found anything.

And I'm not sure if this is Oneiric related or Xfce + Gnome Services related.  If it was the latter I would expect more Google hits.  Maybe it's a bit of both? 

If anyone else has any ideas of what to check next I'm down.

-Tim

---

### Post by Krytarik on 2011-10-03
> **TimHeckman said:**
> And I'm not sure if this is Oneiric related or Xfce + Gnome Services related.  If it was the latter I would expect more Google hits.
Yeah, indeed, me too. And I've searched Google, too, before replying, and didn't get any related results either, not to mention a significant amount, to indicate the latter case.

---

### Post by crdlb on 2011-10-03
Gnome 3 has a settings key you could try disabling: ```
gsettings set org.gnome.desktop.a11y.applications screen-keyboard-enabled false
```

If that doesn't work, can you figure out the name of the keyboard? There appear to be two options: onboard and caribou.

Edit: I just noticed the title of the thread ...

/etc/xdg/autostart/onboard-autostart.desktop has two AutostartConditions, one makes sure that it only starts in GNOME3 (except gnome-shell, where caribou is used), and the other checks the settings key I mentioned above. It's likely that xfce's code doesn't know what to do with that condition and just ignores it. So it seems that something about ```
AutostartCondition=GNOME3 unless-session gnome

``` is confusing xfce.

---

### Post by crdlb on 2011-10-03
Upon further [research]("http://git.xfce.org/xfce/xfce4-session/tree/xfce4-session/xfsm-startup.c"), Xfce doesn't do anything with AutostartCondition; instead it launches any .desktop file containing 'OnlyShowIn=GNOME' if gnome compatibility is enabled. This behavior seems to be in violation of the [autostart spec]("http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html") which states: > The OnlyShownIn entry may contain a list of strings identifying the desktop environments that MUST autostart this application, all other desktop environments MUST NOT autostart this application.

---

### Post by cbrigstocke on 2011-10-06
I have that same problem.  I uninstalled onboard.  It doesn't fix the underlying problem, but it does the trick.

---

