---
title: "[SOLVED] After reboot system preferences disappear"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by captain_rob on 2008-08-19
Hello Forum members,


I am a newbie and have a problem with my System>Preferences settings In Ubuntu (Heron Hardy 64, Gnome 2.22.3). 

Some of this settings, like the keyboard settings, power management and Sessions go back to their old settings after reboot. When I renew X (Ctrl-Alt-Del) the settings remain. I already put all authorisations on me as user.

Who can help me out? 
:confused:

---

### Post by ggaaron on 2008-08-19
It depends on the settings that revert themselves. Recently much settings that had been previously set statically in some configuration file like xorg.conf are set dynamically on boot. Example is XOrg using HAL for almost anything. So what do you exactly want to change? The more specific you are, the bigger the chance that someone will be able to help=)

---

### Post by captain_rob on 2008-08-19
It doesnt matter wat I change, after reboot the preferences just disappear. 
For example if I add an applet to the panel, after reboot gone. 
If I change the Keyboard settings in System>preferences>keyboard, after reboot gone.
If I change the session settings in System>preferences>sessions , after reboot gone.
If I change the power management settings the same and so on.

---

### Post by natiminc on 2008-08-19
same here, im not sure what to do either

---

### Post by ggaaron on 2008-08-20
You aren't talking about using live CD by accident?

---

### Post by captain_rob on 2008-08-20
No live CD, installed on a desktop and updated. Kernel 2.6.24.-19-generic

---

### Post by ggaaron on 2008-08-20
And do program settings persist? Like firefox's for example?

---

### Post by captain_rob on 2008-08-20
I did a test, changing settings of firefox persist after reboot.

---

### Post by ggaaron on 2008-08-20
Seems like GNOME related issue then if panels reset themselves. I'd recommend posting on Desktop Environments part of the forum.

---

### Post by captain_rob on 2008-08-20
I solved it already myself. The .config and some subdirectories were owned by root (don't know what changed it), after chowning everything is back to normal.

---

