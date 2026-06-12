---
title: "Ubuntu vs Kubuntu"
date: 2009-12-03
forum: Recurring Discussions
---

### Post by Drjim on 2009-12-03
Can someone tall me the difference between ubuntu and kubuntu?


Jim

---

### Post by mienai on 2009-12-03
Kubuntu is a product of Canonical Ltd that is simply Ubuntu utilizing a KDE desktop environment instead of Gnome

---

### Post by jbrown96 on 2009-12-03
Ubuntu uses the Gnome Desktop Environment and Kubuntu uses the KDE SC Plasma Desktop.

It's a contentious issue, which is better. I prefer KDE SC, but many people really like Gnome. 

KDE SC is really customizable, and Gnome tends to be more stable and conservative. 

It's definantly worthwhile to try both. 
I would recommend trying Ubuntu first for two reasons. #1 it's easier to learn. The interface is simpler, and you will have your hands full learning Linux, and a more customizable DE would be a lot to learn at once. #2 Gnome is the main DE. There are many more people that use Gnome, so more people on these forums can give advice. 

You can install KDE SC in Ubuntu and Gnome in Kubuntu. I don't because each DE comes with it's own applications, and the menus can get really crowded with all the apps. 
To install KDE SC ```
sudo apt-get install kubuntu-desktop
```
For Gnome ```
sudo apt-get install gnome-desktop
```


I should also mention the technical difference between the two. Applications generally use "libraries" to ease the work of the programmer. Gnome and KDE SC use substantially different core libraries (GTK+ and QT, respectively). When you boot Ubuntu/Kubuntu the appropriate libraries are automatically loaded. This means if you run a QT app in Kubuntu (or GTK+ app in Ubuntu), it generally starts fast because there isn't as much to load. The applications also look slightly different. Similar to how "widgets" (buttons, scroll bars, all the parts of a GUI) look different between Mac OS X and Windows. The problem is that if you run a GTK+ app in Kubuntu, the QT libraries have to sort of convert the GTK+ app; this process isn't perfect, and visually the apps don't look quite as nice if they are used outside their environment. Consequently, if you use Ubuntu, then you tend to (and are recommended to) try to use GTK+ apps, and the same is true for Kubuntu. 
When you are choosing apps there are some clues to help you know if it is GTK+ or QT; GTK+ apps tend to start with a "g", and QT apps tend to start with "k" or use "k's" where "c's" belong. This rule is far more true for QT than GTK+. For example, gthumbs is a GTK+ app and Konversation is a QT app.

It's worth mentioning that QT is technically far superior to GTK+, but it's up to application developers to use the libraries to their full potential.

---

### Post by Aflack on 2009-12-03
id recommend installing ubuntu then trying out kde inside of ubuntu.... visit the link

[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

have fun.

---

### Post by 3rdalbum on 2009-12-03
In absolute complete layman's terms, Kubuntu has a different set of preinstalled programs, and a different GUI. So, it looks and feels different to regular Ubuntu.

---

### Post by mvalviar on 2009-12-04
May I add that running the kubuntu desktop from an ubuntu install is quirky. I got disappointed with kubuntu at that time. I made a thread regarding this before. But most kubuntu users told me that a default kubuntu install works OK. I'd wanted to use kubuntu since amarok, k3b and a number of kde apps work better than their gnome counterparts. But being an ubuntu user from the start I'm not used to the kde way doing things. Like always having to click apply when you change a setting.

---

### Post by PariahVayne on 2009-12-04
x

---

### Post by travmanx on 2009-12-04
> **PariahVayne said:**
> Ubuntu works, Kubuntu bounces from one bug to the next. Avoid.

Ouch ><. Although I can't agree more so, if his system only meets the minimum requirements that Ubuntu requires, I'd suggest going the Kubuntu way. I've found Ubuntu can be very sluggish with minimum setup. 
As long as you keep up to date with everything, Kubuntu should be fine. It just takes a little more getting used to.

---

### Post by Sef on 2009-12-04
Moved to recurring discussions.

---

### Post by jbrown96 on 2009-12-04
I run Gnome and KDE, but I can't stand to have them installed in the same setup. I have two different *buntu installations (one KDE SC and the other Gnome), then I share a /home partitions. It's great; I get all my documents and settings (like Firefox history/bookmarks) seamlessly, but don't have to deal with all of that nasty Gnome stuff taking over my KDE (haha, I'd say the opposite if I primarily used Gnome). This setup may be beyond a new user, though.

---

