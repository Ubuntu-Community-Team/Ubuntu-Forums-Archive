---
title: "6 workspaces in 14.04 possible?"
date: 2014-04-30
forum: New to Ubuntu
---

### Post by genejohnson55 on 2014-04-30
I found a setting in dconf:  org.gnome.desktop.wm.preferences num-workspaces 6

but it didn't work. i'm still at 4.

Is it possible to get 6 workspaces "natively"? I don't want to install any 3rd party apps to do it. I want to know if there's a native way.

---

### Post by monkeybrain20122 on 2014-04-30
Try ccsm.

---

### Post by genejohnson55 on 2014-04-30
isn't that something else I have to install?

---

### Post by deadflowr on 2014-04-30
The setting in dconf is org.compiz.profiles.unity.plugins.core
change the values in hsize and vsize

---

### Post by genejohnson55 on 2014-04-30
> **deadflowr said:**
> The setting in dconf is org.compiz.profiles.unity.plugins.core
change the values in hsize and vsize

Thanks!

The "workspace switcher" icon no longer works? The icon on the launcher can't show your workspace place if you use more than 4 workspaces? Is this for everyone?

---

### Post by monkeybrain20122 on 2014-04-30
ccsm is the CompizConfigsSettingsManager, it is in the repo. I think there are some kind of hierarchies for the tweak tools so settings of one may override others. I don't know about using dconf to change compiz settings, I always use ccsm.

---

### Post by deadflowr on 2014-04-30
> **genejohnson55 said:**
> Thanks!

The "workspace switcher" icon no longer works? The icon on the launcher can't show your workspace place if you use more than 4 workspaces? Is this for everyone?

Do you mean how it shows windows inside the icon?
Then yes, it affects everyone.

---

### Post by monkeybrain20122 on 2014-04-30
It works and "workspace switcher icon" works too. Open ccsm and go to General Options > Desktop size set horizontal =3 vertical =2, for example.

Bear in mind that this is taken in an old 14.04 beta which i have not updated, I just haven't gotten a chance to erase it.  It should work with up to date 14.04 unless they have messed things up with some updates. I have a current, up to date 14.04 installation but I am not going to risk messing up my settings for this demo. :)

---

### Post by genejohnson55 on 2014-04-30
> **deadflowr said:**
> Do you mean how it shows windows inside the icon?
Then yes, it affects everyone.

yeah, the window inside the icon. I appreciate being able to see what workspace I'm in. It could get a little crazy with more than 4 workspaces and no indicator of which one you're in.

Thankx guys !

---

