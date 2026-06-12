---
title: "Problem after updating Ubuntu"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by 6_sigma on 2008-07-12
After last night's update of Hardy Heron on my laptop - something I've done many times before - I have three problems:

[LIST=1]
[*]Intall problem: The configuration defaults for GNOME Power Manager have not been installed correctly. This error warning pops up often.
[*]I have no shutdown icon on my menu bar any longer. Just a running green guy which only restarts Ubuntu.
[*]I cannot change the background image on my desktop.
[/LIST]

Thanks to anyone who can point me toward solutions.

---

### Post by prshah on 2008-07-12
> **6_sigma said:**
> 
[LIST=1]
[*]Intall problem: The configuration defaults for GNOME Power Manager have not been installed correctly. This error warning pops up often.
[*]I have no shutdown icon on my menu bar any longer. Just a running green guy which only restarts Ubuntu.
[/LIST]



The first two seem related; try:

Open a terminal, (Application-Accessories-Terminal) and give the command```
gnome-power-manager
``` which should either enable the power features or display an illuminating error message that you should post back here.

---

### Post by 6_sigma on 2008-07-12
That command caused the same message to pop up: *Install Problem:The configuration defaults for GNOME Power Manager have not been installed correctly. *

Thanks for your help!

---

### Post by prshah on 2008-07-12
> **6_sigma said:**
> That command caused the same message to pop up: *Install Problem:The configuration defaults for GNOME Power Manager have not been installed correctly. *


Looks like the configuration has been left incomplete after the update.. was the update interrupted? Try this```
sudo apt-get update
sudo apt-get -f install

```, then restart. if these don't give an error, but fail to fix the problem, give this command```
sudo dpkg --configure gnome-power-manager

``` If that gives an error, please post output of ```
ls -l ~/.gconf/apps/gnome-power-manager
```

In a pinch, you can use```
sudo dpkg --configure -a
``` WARNING: This command _may_ revert _all_ config files to their defaults, including but not limited to networking/samba, video, audio, etc, so use with caution and only if necessary.

---

### Post by 6_sigma on 2008-07-12
> ls -l ~/.gconf/apps/gnome-power-manager
total 28
drwx------ 2 spilgrim spilgrim 4096 2008-06-15 11:07 actions
drwx------ 2 spilgrim spilgrim 4096 2008-07-12 11:05 ambient
drwx------ 2 spilgrim spilgrim 4096 2008-07-12 11:05 backlight
drwx------ 2 spilgrim spilgrim 4096 2008-07-12 11:05 buttons
drwx------ 2 spilgrim spilgrim 4096 2008-07-12 11:05 cpufreq
-rw------- 1 spilgrim spilgrim    0 2008-06-15 11:07 %gconf.xml
drwx------ 2 spilgrim spilgrim 4096 2008-07-12 06:48 timeout
drwx------ 2 spilgrim spilgrim 4096 2008-07-12 11:05 ui

That's the output from the ls command. I'm no longer getting an error message, however, I have no way to shut the computer down except to click on the "green running man," let that take me back to the login screen, then use the "options" menu in the lower left corner to choose "shutdown."

We may well be in the area of operator error at this point. I'm simply baffled as to why the "quit..." option and the "green runner" no longer provide a shutdown option.

---

### Post by stans on 2008-12-13
I'm having this problem also - does anyone have any suggestions ? None in the above replies worked for me.

---

### Post by simplr on 2009-11-03
I had a similar problem. Found the cause to be that the drive partition for Ubuntu was full. Deleted some files after booting to the command prompt and that fixed it.

---

