---
title: "Shell script runs on startup when going to Startup Applications in UI, fails rc.local"
date: 2013-04-18
forum: New to Ubuntu
---

### Post by FrontLoadedAnvils on 2013-04-18
using Ubuntu 12.10 64 bit


I wrote a small shell script that sets up my resolution for my second monitor. When I put it in Startup Applications (through the unity interface) the script is run. However, I am trying to avoid using the UI and do everything through terminal.


When I edit my /etc/rc.local file and put


/home/anvils/resolution.sh


in the line before "exit 0", it changes nothing when I reboot.


I have also tried to put it in my /etc/init.d/rc.local file but it doesn't do anything either.


Why does the script work on startup when I put it in Startup Applications through the UI but not when I edit the rc.local file? Also, how can I make it work just by doing terminal commands?

---

### Post by dargaud on 2013-04-18
I guess rc.local are run even before X is launched. Also you should try 'disper' when playing with multi-monitors. It's very simple to use.

---

### Post by Cheesemill on 2013-04-18
> **dargaud said:**
> I guess rc.local are run even before X is launched.

+1
The rc.local script is run before the X server starts, so if any of the commands in your script need X to be up and running then they won't work.
If you can post the contents of your script then it will make it easier for us to diagnose.

Also is your home folder encrypted? If it is then this will stop the script from running because your home directory doesn't get unlocked until you log on, which again happens later in the boot process than the rc.local script gets executed.

If you want to add the script to your startup applications without using a GUI, then just create a link or copy it into your ~/.config/autostart directory.

---

### Post by FrontLoadedAnvils on 2013-04-19
Apologies for being late on the reply.

Extra information: When I posted this, my desktop environment was Unity. I have recently did a command-line install of ubuntu and tried to copy my file into the ~/.config/autostart in both LXDE and Gnome 3. It did not work either way.

Extra note: On the command line installation, I could not find the .config directory. When I installed the DE, I could find the .config folder but not the autostart directory. When I run the script on its own, it works. However, it does not work on reboot.

The file is as follows:

#!/bin/bash
xrandr --newmode "resolution1"  ... [modeline numbers]
xrandr --addmode VBOX0 resolution1
xrandr --output VBOX0 --mode resolution1

It works when I run the file, but it doesn't work on reboot.

---

