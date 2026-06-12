---
title: "Compiz"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Sly-.- on 2008-05-02
Hey, so I have a freshly installed Ubuntu 8.04. I want to mess around with compiz a bit now, I check how to install it and in this tutorial is says to go to system > Administration > Synaptic Package Manager, install compizconfig-settings-manager but when I search for compiz it doesn't come up with the option to install. Anyone know where I'm going wrong and what I can do to install it properly? Cheers.

---

### Post by Saint Angeles on 2008-05-02
make sure all your repositories are enabled (system->administration->software sources)

then open up a terminal (applications->accessories->terminal) and type: ```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by vishzilla on 2008-05-02
Go to applications>add/remove and search for 'ccsm' check it and Apply Changes
Cheers!

---

### Post by Sef on 2008-05-02
Have you opened the Universe Repos?  System > Administration > Software Sources > check Community-Maintained Open Source Software (universe.)

---

### Post by frup on 2008-05-02
Can you see compiz-settings manager in Synaptic? Click on the square box to the left of the name, then go apply in the toolbar. It will install. Then compiz settings manager can be found in System > Administration > Preferences. 

If you have already got the basic versions of desktop effects going you shouldn't have a problem but otherwise you will need to make sure you have the right video card driver installed. Go to system > administration > hardware drivers and see if it prompts you to install a 3d driver. I warn these maybe proprietary.

In Compiz settings manager each plugin for compiz is listed and you can manipulate some very advanced details of them. For some you probably won't need to configure, others you might. I would have a good play around with each thing and it's various settings to find out what you find disgustingly unnecessary and what you find incredibly useful.

---

### Post by Sly-.- on 2008-05-02
Thanks guys, I went to Applications > Add/Remove, it said my stuff was not up to date, updated it and compiz-settings manager is now in synaptic. Cheers again.

---

### Post by vishzilla on 2008-05-02
Good. Always before installing any program check if you have the sources enabled and ```
sudo apt-get update
``` before installing ;)

---

### Post by Sly-.- on 2008-05-02
Pretty much all the different effects are working but desktop cube seems to do nothing when I press the keys to activate it. Even Rotate Cube works but it's just the 2 dekstops, Any clue to how to get the cube working? Thanks.

Edit: Nevermind, I got it. ;)

---

