---
title: "Ubuntu Software Center and Synaptic - question"
date: 2022-12-21
forum: New to Ubuntu
---

### Post by jonfisher on 2022-12-21
Does Ubuntu Software Center install using snaps?

I ask this because if I open Synaptic and search for say, Firefox, that I've installed in Ubuntu Software center, it's not listed as installed yet in Synaptic....

p.s. In Synaptic, it says something about a "dummy package"  - see screenshot...

I just checked Gimp also, which shows installed in Ubuntu software center & doesn't showed installed in Synaptic.  I could have sworn in the past that if Ubuntu software center showed something isntalled, it would show installed in Synaptic as well.    (?)

---

### Post by maglin2 on 2022-12-22
The clue is in your synaptic message. 
Firefox is now a snap package. I guess gimp is too.
In a terminal try 
[FONT=monospace][COLOR=#000000]$ snap list
I get
[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]$ snap list [/COLOR]
Name                                  Version           Rev    Tracking       Publisher   Notes 
bare                                  1.0               5      latest/stable  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]  base [/COLOR]
core20                                20221123          1738   latest/stable  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]  base [/COLOR]
firefox                               108.0.1-1         2211   latest/stable  mozilla[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]    - [/COLOR]
gnome-3-38-2004                       0+git.6f39565     119    latest/stable  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]  - [/COLOR]
gtk-common-themes                     0.1-81-g442e511   1535   latest/stable  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]  - [/COLOR]
kde-frameworks-5-96-qt-5-15-5-core20  5.96.0            7      latest/stable  kde[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]        - [/COLOR]
snap-store                            41.3-66-gfe1e325  638    latest/stable  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]  - [/COLOR]
snapd                                 2.57.6            17883  latest/stable  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]  snapd [/COLOR]
snapd-desktop-integration             0.1               49     latest/stable  canonical[COLOR=#18b218]&#10003;[/COLOR][COLOR=#000000]  -[/COLOR]

[/FONT]
```

---

### Post by Impavidus on 2022-12-22
Ubuntu Software Centre can install both snaps and the older debs and it doesn't make it very clear which version you're installing. Synaptic only deals with debs.

Firefox is only available as a snap nowadays (=in Ubuntu 22.04). The deb package for Firefox that you can see in Synaptic doesn't contain firefox itself. It only has a script that installs the snap package. Gimp is available both as a deb and as a snap. Synaptic installs the deb version, Software Centre can give you both the deb and snap version and it appears that you got the snap version.

---

### Post by oldos2er on 2022-12-22
Synaptic is "old school" in that it was developed long before snaps, appimages, flatpak, etc. were even thought of. As Impavidus says Synaptic only installs (removes, manages) deb packages.

The firefox dummy package is a deb package that installs the snap version of firefox.

---

### Post by mIk3_08 on 2022-12-23
> **jonfisher said:**
> Does Ubuntu Software Center install using snaps?
  
Ubuntu Software Center is also a snap "Snap Store". For more details of snap [click here]("https://linuxmint-user-guide.readthedocs.io/en/latest/snap.html"). Regards and cheers.

---

