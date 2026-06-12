---
title: "[SOLVED] AWN show desktop button?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-04-30
i just installed avant window navigator yesterday and ive been trying to figure out how to make a "show desktop" button

when i google for how to make a show desktop button all i can find is stuff to fix awn from minimizing when its pressed

i know its possible because ive seen screenshots with the show desktop button on awn

can anybody point me in the right direction please?

---

### Post by TheSe7enthSin on 2008-04-30
Right click AWN --> Preferences
Click on "Applets" on the left & just add the Show Desktop applet.

---

### Post by tjwoosta on 2008-04-30
how do i add the show desktop applet?

i can only see one applet and it says 
"**Launcher/Taskmanager**- The main Awn Launcher/Taskmanager applet"

---

### Post by TheSe7enthSin on 2008-04-30
Looks like you dont have the awn extras installed.
Did you install from the source or from the synaptics package manager?

---

### Post by tjwoosta on 2008-04-30
yea i had installed from synaptec, but i figured out how to get applets ayway

first i had to enable theese repositories
```

deb http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main
deb-src http://ppa.launchpad.net/reacocard-awn/ubuntu hardy main

```

theres a guide here
[http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive]("http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive")
then i installed theese awn packages 
```

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

```

now i have like 30 applets to choose from

---

