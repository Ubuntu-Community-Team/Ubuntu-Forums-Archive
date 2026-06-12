---
title: "[SOLVED] how do I stop mousewheel workspace switching"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by mr.v. on 2008-11-10
Hi all,

any idea how to turn off workspace switching on mouse wheel action? It's been somewhat frustrating as the mouse-wheel will cause workspace switching if it strays off the active window during scrolling and I've caught it a few times switching workspaces even when the cursor is over the active window. Haven't figured out how to reproduce that reliably but it happens just enough to be really annoying. I'd like to just turn off the feature but can't find the place to do that.

Steps I've tried already:
1) looking in the System|Preferences|Mouse but the option to enable/disable workspace switching for the mouse wheel is not present
2) Turned off ZAxisMapping but this solution stops mouse wheel input in general which was the old cannon-to-kill-a-fly solution.

---

### Post by keplerspeed on 2008-11-10
Do you have the compiz config settings manager? if not, it is avaliable via synaptic. then under rotate cube>bindings disable rotate the cube with the mouse.

cheers

---

### Post by REDace0 on 2008-11-10
That should be it. Just want to make sure this thread gets thanked and solved (yellow medal next to above's post and Thread Tools>something).

---

### Post by mr.v. on 2008-11-10
> **keplerspeed said:**
> Do you have the compiz config settings manager? if not, it is avaliable via synaptic. then under rotate cube>bindings disable rotate the cube with the mouse.

cheers

Thanks for the reply. I forgot to mention that I had already tried that. The settings in the CCSM are for cube rotation. Cube rotate Left/Right are both disabled (were disabled by default as well) via the mouse but it still keeps rotating.

I think what's going on is that the mouse-wheel is bound to "workspace switch" rather than cube rotate. I'm having trouble finding where workspace switching bindings are to remove mousewheel up/down from it. I looked all through CCSM to find workspace switch and was unable. I even looked for any binding in both the general settings under compiz or the cube for mousewheel bindings and didn't see any.

Anyone have any other ideas?

---

### Post by dhtseany on 2008-11-10
System -> Preferences -> Appearance -> Visual Effects -> and select None. See if that helps.

Peace
Sean

---

### Post by mr.v. on 2008-11-10
> **dhtseany said:**
> System -> Preferences -> Appearance -> Visual Effects -> and select None. See if that helps.

Peace
Sean

Found it. It's actually called "viewport switcher" and the settings for it are under the CCSM. There's the mousewheel binding for switching viewports.

---

### Post by dhtseany on 2008-11-11
Oh I thought you said that it didn't work.

Whatev

Peace
Sean

---

### Post by fawzley on 2009-04-10
> **mr.v. said:**
> Found it. It's actually called "viewport switcher" and the settings for it are under the CCSM. There's the mousewheel binding for switching viewports.

Having the same spontaneous workspace switching weirdness.   How do I find  CCSM settings? Checked in synaptic manager and the software is installed; but I am unable to find it on the menus...

Thx, in advnace...

F

---

### Post by mr.v. on 2009-04-10
CCSM stands for CompizConfig Settings Manager

it's not installed by default so you can go to the synaptic package manager and search for it to install or go to a terminal and type in
```
sudo apt-get install compizconfig-settings-manager
```
to get access...then it'll show up in the menus.


There's lots of other features you can enable with it too. Hope this helps!

---

