---
title: "System Font sizes"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by atypicalwinter on 2008-07-11
right,i'm new to linux so bare with me, i been using 7.10 on ps3 for over a year now and the other month i came accross a tick box to increase program font size for things like amorok and ktorrent which has there own font size. i did a fresh install and now i cant find this option is there anyone here that can help? i know how to make all other fonts bigger just not these progams thank you if anyone can help.

---

### Post by ChameleonDave on 2008-07-11
> **atypicalwinter said:**
> right,i'm new to linux so bare with me, i been using 7.10 on ps3 for over a year now and the other month i came accross a tick box to increase program font size for things like amorok and ktorrent which has there own font size. i did a fresh install and now i cant find this option is there anyone here that can help? i know how to make all other fonts bigger just not these progams thank you if anyone can help.

If you want to affect individual programs, you have only to go into the preferences for those programs.  All applications have a menu with an item such as "Preferences", "Settings", "Configure" or "Options".  Just look through it.

For example, I'm now going to open Amarok.  Let's see... There is a menu called "Settings", and under that a menu item called "Configure Amarok...".  A window comes up with various tabs.  One tab is called "Appearance".  I click it, and I see a section called "Fonts".

You really don't need someone to tell you this.  Just look.

---

### Post by atypicalwinter on 2008-07-11
thats the thing im trying to tell you i wouldnt of said otherwise.

i remember for a fact that there was a tick box to not have the programs set the text size and now i have lost it.

i know you can set it in eeach program but i didnt do that the other month otherewise i would have done it this time round

---

### Post by ChameleonDave on 2008-07-11
You mean a setting in the preferences of the desktop environment which will allow you to override the font settings of individual  programs?  You didn't express that clearly the first time.

What desktop environment are we talking about?  KDE 3?  KDE 4?  GNOME?  Xfce?  You mention the PS3 (PlayStation 3?); does that have a special interface?

---

### Post by atypicalwinter on 2008-07-11
ah thats exactly what i mean dude, sorry i couldn't be clearer i wasn't sure what it was in first place you see.

yeah its on ps3 and as far as i know its ubuntu 7.10 ppc version and i  think its gnome.

like i said perviously I'm pretty new to linux still learning the ropes.

---

### Post by ChameleonDave on 2008-07-12
> **atypicalwinter said:**
> ah thats exactly what i mean dude, sorry i couldn't be clearer i wasn't sure what it was in first place you see.

yeah its on ps3 and as far as i know its ubuntu 7.10 ppc version and i  think its gnome.

like i said perviously I'm pretty new to linux still learning the ropes.
I've just gone to have a look at GNOME.  Under the Preferences menu at the top of the desktop there is an Appearance option that let me change font sizes for GNOME applications.  However, I didn't see any way of forcing Qt-based applications (such as those of KDE) to obey those settings.

Under "Qt4 Settings" in Gnome Control Centre I can see how to set the fonts in Qt4 apps, but that wouldn't help with Qt3 apps like Amarok.

---

### Post by atypicalwinter on 2008-07-14
> **ChameleonDave said:**
> I've just gone to have a look at GNOME.  Under the Preferences menu at the top of the desktop there is an Appearance option that let me change font sizes for GNOME applications.  However, I didn't see any way of forcing Qt-based applications (such as those of KDE) to obey those settings.

Under "Qt4 Settings" in Gnome Control Centre I can see how to set the fonts in Qt4 apps, but that wouldn't help with Qt3 apps like Amarok.

thats starnge because thats how my system was before the re installation i did last week. how do you get to the gnome control center then. cant seem to find it lol

---

### Post by ChameleonDave on 2008-07-14
> **atypicalwinter said:**
> thats starnge because thats how my system was before the re installation i did last week. how do you get to the gnome control center then. cant seem to find it lol
Well, make sure you have it installed first.  You can look for it in Synaptic, or just do this command:

```
sudo apt-get install gnome-control-center

```Then run it with 
```

gnome-control-center

```

---

### Post by philinux on 2008-07-14
It's installed by default.

But the menu item needs enabling in prefs.

System>Prefs>Main Menu

---

### Post by atypicalwinter on 2008-07-14
yeah i found this out myself lol.

id like to say this helped me but it didnt really. i just think its strange how i had it before and now i cant remember how the hell i did it.

---

