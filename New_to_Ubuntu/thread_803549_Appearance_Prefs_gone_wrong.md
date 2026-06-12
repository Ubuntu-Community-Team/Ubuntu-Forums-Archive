---
title: "Appearance Prefs gone wrong"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by m_ad on 2008-05-22
All of a sudden, my System->Preferences->Appearance, Theme tab has gone bad. Everything shows up with a ? (question mark). Every time I go and add a new theme, it adds it to the Custome theme instead of adding a new one.

any ideas why this happened? I don't use compiz or any other visual effects, just plain gnome.

---

### Post by sayakb on 2008-05-22
Open Nautilus as root
```
gksudo nautilus
```
Then extract the theme files and copy it to /usr/share/themes folder using the root nautilus window.
See if this works

---

### Post by m_ad on 2008-05-22
this doesn't work. I see a lot more files/folders in /usr/share/themes than I do in themes tab in Appearance. something happened to the Appearance Preferences dialog.. it didn't used to be like this.


any idea on how to fix it? (preview the themes, instead of showing a dim, basic window with a huge ? in it)

---

### Post by m_ad on 2008-05-22
this is the same problem I'm having


[http://ubuntuforums.org/showthread.php?t=722704](http://ubuntuforums.org/showthread.php?t=722704)


update: this is the error I get:
```
gnome-appearance-properties: symbol lookup error: gnome-appearance-properties: undefined symbol: meta_preview_get_clip_region
```

---

### Post by m_ad on 2008-05-22
one last try

---

### Post by m_ad on 2008-05-22
I lied.. :lol:


anyone else having this problem/know a solution?

---

### Post by philinux on 2008-05-22
Go to synaptic and reinstall ubuntu-desktop

---

### Post by m_ad on 2008-05-23
> **philinux said:**
> Go to synaptic and reinstall ubuntu-desktop

haven't used synaptic, only the cli package manager..


do I just tick the box, and "mark for install?" the box isn't ticked already, and I'm worried since it says there are packages that are going to be removed :confused:

---

### Post by philinux on 2008-05-23
Mark it for reinstallation then click apply

---

### Post by m_ad on 2008-05-23
after apt-get install ubuntu-desktop

```
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  brasero bug-buddy gimp gimp-data gimp-gnomevfs gimp-python gvfs-fuse
  hal-cups-utils jockey-common jockey-gtk libatspi1.0-0 libavahi-ui0
  libbeagle1 libcupsys2 libgimp2.0 libgpgme11 libgtk-vnc-1.0-0
  libgtksourceview2.0-0 libgtksourceview2.0-common libldap-2.4-2 libotr2
  libpth20 libpulse-browse0 libpulsecore5 mousetweaks nautilus-cd-burner
  nautilus-share pidgin-otr pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils scim-bridge-agent scim-bridge-client-gtk seahorse
  system-config-printer-common system-config-printer-gnome totem-mozilla
  vinagre
Suggested packages:
  gstreamer0.10-fluendo-mp3 gimp-data-extras libgimp-perl xvncviewer gpgsm
  libotr2-bin samba padevchooser paman paprefs pavucontrol pavumeter
Recommended packages:
  libasound2-plugins
**The following packages will be REMOVED**:
  gimp-print restricted-manager restricted-manager-core system-config-printer
The following NEW packages will be installed:
  brasero bug-buddy gimp-gnomevfs gvfs-fuse jockey-common jockey-gtk
  libavahi-ui0 libbeagle1 libgpgme11 libgtk-vnc-1.0-0 libldap-2.4-2 libotr2
  libpth20 libpulse-browse0 libpulsecore5 mousetweaks nautilus-cd-burner
  nautilus-share pidgin-otr pulseaudio pulseaudio-esound-compat
  pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11
  pulseaudio-utils scim-bridge-agent scim-bridge-client-gtk seahorse
  system-config-printer-common system-config-printer-gnome totem-mozilla
  ubuntu-desktop vinagre
The following packages will be upgraded:
  gimp gimp-data gimp-python hal-cups-utils libatspi1.0-0 libcupsys2
  libgimp2.0 libgtksourceview2.0-0 libgtksourceview2.0-common
9 upgraded, 33 newly installed, 4 to remove and 894 not upgraded.

```

---

### Post by FuturePilot on 2008-05-23
Looks safe to proceed. Don't worry about the removed packages. Those have been replaced with other packages.

---

### Post by m_ad on 2008-05-23
> **philinux said:**
> Mark it for reinstallation then click apply

doesn't even look like it's installed. no option for "REinstallation" only "mark for install.."


I'll just use apt-get install ubuntu-desktop.. if anything goes wrong I'll report [-o<

---

### Post by philinux on 2008-05-23
You just click the green box :)

sorry should have said.

How come it's uninstalled?

---

### Post by m_ad on 2008-05-23
no idea, I never uninstalled it.

---

### Post by m_ad on 2008-05-23
installing ubuntu-desktop didn't work..


```
ubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 894 not upgraded.

```


now should I go into synaptic and chose "mark for reinstall?"

---

### Post by m_ad on 2008-05-23
I just reinstalled it using synaptic and even restarted, didn't fix the problem.

---

### Post by stchman on 2008-05-23
> **m_ad said:**
> All of a sudden, my System->Preferences->Appearance, Theme tab has gone bad. Everything shows up with a ? (question mark). Every time I go and add a new theme, it adds it to the Custome theme instead of adding a new one.

any ideas why this happened? I don't use compiz or any other visual effects, just plain gnome.

Are you using a theme you downloaded from a website?  I have found that some themes cause unpredictable behavior.  I stick with the themes that Ubuntu provides.

You might want to just blow away your themes folder.

```
rm -rf ~/.themes
```

Remember rm is a dangerous command so make sure you want to do completely delete before you use this command.

---

### Post by m_ad on 2008-05-23
> **stchman said:**
> Are you using a theme you downloaded from a website?  I have found that some themes cause unpredictable behavior.  I stick with the themes that Ubuntu provides.

You might want to just blow away your themes folder.

```
rm -rf ~/.themes
```

Remember rm is a dangerous command so make sure you want to do completely delete before you use this command.

wouldn't deleting my whole ~/.themes get rid of the default ones that come with ubunutu? or are they stored elsewhere..?

---

### Post by m_ad on 2008-05-23
so far I have reinstalled ubuntu-desktop, and removed my entire ~/.themes folder. the problem isn't solved..


should I report this as a bug?

---

### Post by m_ad on 2008-05-23
is this a bug? or does someone have a solution?

---

### Post by FuturePilot on 2008-05-23
Do you have either of these packages installed?
```
gtk-qt-engine
gtk2-engines-gtk-qt
```

---

### Post by m_ad on 2008-05-23
> **FuturePilot said:**
> Do you have either of these packages installed?
```
gtk-qt-engine
gtk2-engines-gtk-qt
```

seems that they weren't installed..

just installed them, rebooted and the problem persists :confused:

```
gtk-qt-engine is already the newest version.
gtk2-engines-gtk-qt is already the newest version.

```


just a reminder, this is the error I'm getting from terminal
```
matt@matt-laptop:~$ gnome-appearance-properties
gnome-appearance-properties: symbol lookup error: gnome-appearance-properties: undefined symbol: meta_preview_get_clip_region

```

---

### Post by m_ad on 2008-05-24
see if anyone can help this morning :D

---

### Post by philinux on 2008-05-24
I'd give

metacity --replace

a go in the terminal.

---

### Post by m_ad on 2008-05-24
metacity --replace blinked my screen quickly, terminal still had it running and in the Appearance Preferences nothing changed. after closing the terminal again nothing changed.

---

### Post by m_ad on 2008-05-24
I am ready to report this as a bug. I wonder why nobody else has run into this problem.

---

### Post by philinux on 2008-05-24
You must have tweaked something.

---

### Post by m_ad on 2008-05-24
> **philinux said:**
> You must have tweaked something.

definitly haven't tweaked anything. didn't even install any new apps or anything.

and regardless, if I have "tweaked" something, it should be fixable.

---

### Post by FuturePilot on 2008-05-24
Ok, some things to try.
Try creating a new user and see if the new user has the same problem. If the new user does, this might be a larger problem. Then you might want to try reinstalling the gnome appearance properties. But I'm not sure what package that is in. Or try reproducing it from a live CD. If a new user doesn't have the problem then it's probably some odd setting somewhere. Try removing the following directories. 

~/.themes
~/.icons
~/.gnome
~/.gnome2
~/.gconf

(Or just rename them something else so if this doesn't work you won't loose all your setting. You can just rename them back to their original name.)

Log out and back in and try gnome-appearance-properties again.

---

### Post by m_ad on 2008-05-24
I evaded the problem by doing a clean install from 7.10 to 8.04. everything works great now :D


thanks to everyone who helped, and if the problem occurs again I'll try what you said FuturePilot :)

---

