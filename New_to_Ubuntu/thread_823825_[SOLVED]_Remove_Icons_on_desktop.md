---
title: "[SOLVED] Remove Icons on desktop"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by clive littlewood on 2008-06-09
Hi All

Hardy with Gnome desktop

I have just installed cairo-dock which is working great.
I have tried to remove my old icons on the desktop.

All the apps shortcuts went into the trash no prob,but trash,computer and home shortcuts will not move.

Any ideas please.

Regards  Clive

---

### Post by stchman on 2008-06-09
> **clive littlewood said:**
> Hi All

Hardy with Gnome desktop

I have just installed cairo-dock which is working great.
I have tried to remove my old icons on the desktop.

All the apps shortcuts went into the trash no prob,but trash,computer and home shortcuts will not move.

Any ideas please.

Regards  Clive

All desktop shortcuts are symbolic links in your ~/Desktop folder.

You should be able to remove all of them unless you mounted a filesystem in your fstab.

---

### Post by RomeReactor on 2008-06-09
Hi. Open a terminal (Applications->Accessories->Terminal) and write or paste:
```
gconf-editor
```
There, go to 'apps->nautilus->desktop' and uncheck the boxes for the icons you want.

---

### Post by Grishka on 2008-06-09
> **clive littlewood said:**
> Hi All

Hardy with Gnome desktop

I have just installed cairo-dock which is working great.
I have tried to remove my old icons on the desktop.

All the apps shortcuts went into the trash no prob,but trash,computer and home shortcuts will not move.

Any ideas please.

Regards  Clive

run gconf-editor, and uncheck the boxes in apps/nautilus/desktop. this can also be done with ubuntu-tweak. if you don't want any icons at all on your desktop, you may also uncheck the "show desktop" box in /apps/nautilus/preferences, but you'll lose the right click desktop menu as well.

---

### Post by diablo75 on 2008-06-09
Taken from:  [http://www.manast.com/2008/03/13/show-computer-trash-icon-on-desktop-in-ubuntu/](http://www.manast.com/2008/03/13/show-computer-trash-icon-on-desktop-in-ubuntu/)

[IMG]http://tech1scripts.googlepages.com/Screenshot-ConfigurationEditor-deskt.png[/IMG]

   1. Hit Alt + F2 and type gconf-editor in the dialog that comes up. Click Run to start the GNOME Configuration Editor.
   2. Go to the key apps/nautilus/desktop
   3. On the right hand side,Â there is an entry called trash_icon_visible. Check the box.
   4. Also check the entry called computer_icon_visible.
   5. You can do two more things from that place too, change the trash_icon_name and computer_icon_name.

---

### Post by drs305 on 2008-06-09
This will clear the Desktop. If you want it back, change the value to 'true':
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'false'
```

I have icons on my top panel with both commands so I can quickly display or hide the desktop items.

---

### Post by clive littlewood on 2008-06-09
Hi

I have tried both methods suggested and the following happened

When i go into the editor and into the nautilus, desktop the icons are there but unchecked !!

If i go into ~/desktop no icons are there (nothing on desktop)

HELP

Clive

---

### Post by drs305 on 2008-06-09
> **clive littlewood said:**
> Hi

I have tried both methods suggested and the following happened

When i go into the editor and into the nautilus, desktop the icons are there but unchecked !!

If i go into ~/desktop no icons are there (nothing on desktop)

HELP

Clive

I am not sure which you mean by "both methods". I also don't quite understand where you stand. Your first post was that you wanted to get rid of the desktop trash, home and computer icons. Are they still on your desktop or have you moved on to another item?

If you provide more details we can help.

---

