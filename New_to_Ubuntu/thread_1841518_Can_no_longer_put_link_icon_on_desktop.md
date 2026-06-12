---
title: "Can no longer put link icon on desktop"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by blatzer on 2011-09-09
ubuntu 11.04
I want to put an icon for link to cache on the desktop.

I was able to right-click on desktop which gave an option to create a folder - this will no longer work.

I was able to put a link icon on the desktop but now I have done something so that I am only allowed to put the icon into a panel.
Either;
 1. Is there a way to quickly restore the system settings to status at install?
   or
 2. What is it that prevents me from moving the link I have set up to cache onto the desktop?

Thanks for any help.

---

### Post by terrykiwi83 on 2011-09-09
AM sorry I have no idea what you want to do, do you want to create a shortcut on your desktop?

---

### Post by blatzer on 2011-09-10
Thank you for the reply.

I am trying to place an icon on the desktop. I guess you may call this a shortcut?

Before accidentally making a change (don't know what) I was able to place icons on the desktop.

One way was to have home open on the desktop and dragging an icon from there to the desktop.
Another way was to right-click on the desktop and create a file or folder.

As an alternative, I have looked for some way to re-set to the system at the time of install.

---

### Post by Enigmapond on 2011-09-10
You want to create a launcher or a shortcut to a folder?

---

### Post by Krytarik on 2011-09-10
If you can't see any icons on your desktop, and right-clicking with the mouse does nothing, make sure the key "/apps/nautilus/preferences/show_desktop" is enabled in "gconf-editor".

Greetings.

---

### Post by blatzer on 2011-09-10
Thank you for the solution.

I looked at this as suggested and checked it to enable and that did it.
Have no idea what I did to have changed the settingf for:

/preferences/show_desktop" is enabled in "gconf-editor".

The Configuration Editor is hidden by default in the System Tools submenu. Access it by pressing Alt+F2 and typing gconf-editor

---

