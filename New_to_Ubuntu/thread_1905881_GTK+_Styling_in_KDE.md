---
title: "GTK+ Styling in KDE"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by lolpenguin on 2012-01-07
I'm trying out KDE for a while, and considering installing Kubuntu when 12.04 is released, but many of the applications I use use GTK+, which is not themed in KDE (and I don't like the alternative in the KDE Software Compilation, e.g. Chrome/Thunderbird). GTK+ Appearance (tried oxygen-gtk and oxygen-molecule) in System Settings has no effect. I have installed all GTK3 engines (there isn't many) relevant.
Also, can Dolphin could be configured to require a double-click to open folder and files?

---

### Post by alexandari on 2012-01-08
Why are you using KDE if you like the gtk+ stuff more,makes no sense. Using GTK+ mixed with qt is an unpleasant mixture whatsoever,and yes you can set your mouse to open "things" with double clicks,but as I am currently not using KDE,I can't tell it by heart,should be in the system settings (where else can it be) ,mouse settings

---

### Post by PaulW2U on 2012-01-08
> **lolpenguin said:**
> Also, can Dolphin could be configured to require a double-click to open folder and files?

Go to System Settings | Input Devices | Mouse | General and you'll find the option to configure a double-click to open files and folders.

---

### Post by tartalo on 2012-01-08
> **lolpenguin said:**
> GTK+ Appearance (tried oxygen-gtk and oxygen-molecule) in System Settings has no effect.

Use QtCurve instead, it does work.

---

### Post by KdotJ on 2012-01-08
> **tartalo said:**
> Use QtCurve instead, it does work.

QtCurve is good, it does iron out some of the differences and give you options for themes. but unfortunately as others have pointed out, the Qt apps will always integrate better

---

### Post by lolpenguin on 2012-01-09
Qtcurve won't work either :(. I might be missing some packages as I did not install kubuntu-desktop or the core packages in their entirety, only what I thought was essential.

---

### Post by mastablasta on 2012-01-09
> **lolpenguin said:**
> Qtcurve won't work either :(. I might be missing some packages as I did not install kubuntu-desktop or the core packages in their entirety, only what I thought was essential.
 
 
ah that explains it. i just wanted to mention you would need to install it to test it out.
 
no worries with TB, Firefox, chrome, libre office, gimp etc. they integrate just fine.
some applicaiton you won't even know they are GTK based :-)

---

### Post by KdotJ on 2012-01-09
> **lolpenguin said:**
> Qtcurve won't work either :(. I might be missing some packages as I did not install kubuntu-desktop or the core packages in their entirety, only what I thought was essential.

From what I've found in the past, KDE is a bit of a pain when trying to do a "bare bones" install with minilmal packages. There's always something missing or not quite right.. like fonts or theming. 

Once you installed QtCurve, were you able to configure it in the system settings?

---

### Post by z3nhakr on 2012-01-09
try emerald

---

### Post by Frogs Hair on 2012-01-09
Emerald has been removed from the 11.10 repository . [http://www.ubuntuupdates.org/packages/show/329590](http://www.ubuntuupdates.org/packages/show/329590)

---

### Post by sleepingdragon on 2012-01-09
QtCurve doesn't convert Gnome apps nicely on 11.10.

I'm just wondering if it is because KDE configures GTK2 apps (as is the Gnome QtCurve package), but 11.10 runs GTK3 for Gnome. There's no obvious tool to handle that.

---

### Post by digithal on 2012-01-09
> **alexandari said:**
> Why are you using KDE if you like the gtk+ stuff more,makes no sense. Using GTK+ mixed with qt is an unpleasant mixture whatsoever,and yes you can set your mouse to open "things" with double clicks,but as I am currently not using KDE,I can't tell it by heart,should be in the system settings (where else can it be) ,mouse settings
Actually, why not? :)
For example, GTK based apps like GIMP and Inkscape are common used and there are no Qt alternatives for them. Some other examples could include Firefox/Chromium and even LibreOffice which most people still prefer instead of KDE's native.
Of course, when you're using another, GTK/ETK powered desktop environment the things are still same. VLC and Skype are good examples of Qt applictions.
Don't get me wrong, I also don't like to mix the things, but why not to use the programs you want and need to? You have the power to choose :)

---

### Post by sleepingdragon on 2012-01-09
Hold on, install *gtk-theme-switch* and run it as *gtk-theme-switch2* from the CLI. Pick QtCurve from the drop-down options - all assuming of course you have installed the KDE appearance tool for GTK apps and have set it for QtCurve.

Seems to work here.

EDIT - it only seems to work on some GTK apps but not others.... damn.

---

### Post by lolpenguin on 2012-01-11
Tried on a Kubuntu install, and QtCurve and Oxygen-GTK look good, and Oxygen Molecule doesn't look that good. So I guess that something is missing in my system...
...which means I can install Kubuntu when Precise comes out! (Not that GNOME Shell or Unity is bad).

---

