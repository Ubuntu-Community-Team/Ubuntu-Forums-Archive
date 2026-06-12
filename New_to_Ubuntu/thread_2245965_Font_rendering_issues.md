---
title: "Font rendering issues"
date: 2014-09-27
forum: New to Ubuntu
---

### Post by Sun_Master on 2014-09-27
I've recently upgraded from 12.04 to 14.04 and found that some text doesn't render properly anymore.
Indicator-sysmonitor displays an unknown character [ATTACH=CONFIG]256740[/ATTACH]
and text shown in a terminal seems to have a problem with spacing. The letter 'm' runs into the characters after it, 'i', 'j'  and 'l' leave too much space and the special characters vary in size by more than they used to.
[ATTACH=CONFIG]256742[/ATTACH]

It renders fine in other programs like firefox and nautilus. It might be linked to another issue I'm having in which I can't change the system font. Trying to apply a different font in unity-tweak-tool has no effect.

I've looked through several other forum posts but can't seem to find a similar enough issue. I've also tried reinstalling my fonts packages, changing theme and rebooting. If you need any other information, please ask.

---

### Post by ibjsb4 on 2014-09-27
I use dconf-editor to change fonts, maybe that would also work with the Unity desktop.  Don't know for sure since I do not use compiz or the unity desktop.  Go to:

org>gnome>desktop>interface>font-name

I assume your running gnome-terminal which does have problems with certain fonts.  Open a terminal and go to:

Edit>Profiles>Edit (default)>General and just use the default font (Monospace) or search for another one that works right.

---

### Post by Sun_Master on 2014-09-27
Ubuntu registers that I've changed the font, but visually it doesn't make a difference.

---

### Post by pissedoffdude on 2014-09-27
Do you remember installing fonts from 3rd party repos?  Sounds like it might be related to that.  Is there an error when you try changing the system fonts?  You might want to check what fonts you have set as default, then see if you installed a package that also provides that font and adjust that package for 14.04.

---

### Post by nenad6 on 2014-09-28
Try installing ttf-mscorefonts-installer package. It might be related to some fonts not being installed.

---

### Post by Sun_Master on 2014-09-28
After a thorough search through Synaptic for anything tagged 'font', I'm pretty certain I have all essential font packages and very few non-essentials. I certainly didn't install/uninstall any font-related packages prior to it breaking. The problem only appeared after upgrading to 14.04, but that doesn't narrow it down much.

---

### Post by Sun_Master on 2014-10-03
I couldn't find a solution for this. Due to a wide variety of problems I ran into using 14.04, I formatted and reinstalled 12.04 which solved everything.

---

### Post by buzzingrobot on 2014-10-03
The indicator likely came from a 12.04 PPA and perhaps needs to be upgraded for 14.04.  Did you back out that PPA before the upgrade, and reinstall it afterwards? 

Terminals typically control their own font settings via a 'Settings' or 'Preferences' menu listing.  The choices made elsewhere won't affect them. (Except for "Sans" and "Serif" which are always placeholder names that map to specific fonts. If the system uses Deja Vu Sans for "Sans", then a terminal set to use Sans will display in Deja Vu Sans. "fc-match Sans" will show you which font is mapped to Sans.  In Ubuntu it is typically Deja Vu Sans.)

---

