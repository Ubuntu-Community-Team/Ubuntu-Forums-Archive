---
title: "Hyper Sensitive Touchpad"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Nodds on 2008-04-30
I've installed 8.04 onto my Sony Vaio laptop (VGN-FZ11L) through Wubi.

Everything seems to work well except for my touchpad which is mega  sensitive, you just need to to float over a link/file/folder etc to  open it. 

I enabled the Touchpad preferences application through Gsynaptics but this does not make anything better.

I've done some reading on the problem and it seems that I have an Alps touchpad, but my xorg.conf file lists a Synaptics one.

Unfortunately i've not been able to find anything in simple terms that can help me rectify this problem.

Any of the threads I have found either seem to be old (2005) or not very clear.

Any help with this would be greatfully appreciated and would help  me stick with Ubuntu (the wife will never let a dodgy touchpad convince her though!!!).

cheers

Nodds

---

### Post by sdennie on 2008-04-30
I'm not completely sure what you mean by "hyper sensitive" but, one thing you could try would be to go  System->Preferences->Mouse and adjust the speed.  If you are having problems with stuff being clicked accidentally (which is what it sounds like), you could also disable touchpad clicking via the Touchpad menu in that application (assuming you don't use it).

---

### Post by Nodds on 2008-04-30
> **vor said:**
> I'm not completely sure what you mean by "hyper sensitive" but, one thing you could try would be to go  System->Preferences->Mouse and adjust the speed.  If you are having problems with stuff being clicked accidentally (which is what it sounds like), you could also disable touchpad clicking via the Touchpad menu in that application (assuming you don't use it).

Basically I dont have to tap to activate a link,the touchpad just does it for me!!

I've tried disabling the touchpad but all that did was make me realise how much I did use it under Vista.

The settings under Mouse dont give me enough control over the touchpad, its either to much or to little for sensitivity.

Cheers 

Nodds

---

### Post by gpeck157 on 2008-04-30
One thing might help. Go to System>Preferences>Mouse>Touchpad and deselect "Enable mouseclicks with touchpad"and deselect "Enable horizontal scrolling". See if that helps.

---

### Post by reggie_mac on 2008-05-02
I've just installed gsynaptics (through package manager) and then done a small edit to Xorg.conf, SHMConfig = true

```
Section "InputDevice"
   Identifier   "Synaptics Touchpad"
   Driver       "synaptics"
   Option       "SendCoreEvents"      "true"
   Option       "Device"              "/dev/psaux"
   Option       "Protocol"            "auto-dev"
   Option       "HorizEdgeScroll"     "0"
   Option       "SHMConfig"           "true"
EndSection
```

Now i have touchpad specific options where i can change sensitivity, so maybe that will help. 

All i need to do is have the touchpad enable/disable itself when a mouse is pluged in.

---

