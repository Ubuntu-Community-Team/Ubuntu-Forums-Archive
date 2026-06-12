---
title: "Missing xfce xubuntu desktop at boot."
date: 2008-09-18
forum: New to Ubuntu
---

### Post by zagas on 2008-09-18
Problem is that every time i log in, in order to be able to see my
desktop, i have to click a checkbox at:
menu/settings/desktop settings/
Allow Xfce to manage the desktop
How do i set this option from default so i don't have to each time I
start my machine?

---

### Post by cardinals_fan on 2008-09-18
That's odd, it should be saved.  Try checking the "Save Session" checkbox when you log out.

---

### Post by zagas on 2008-09-19
Not work for me:(

---

### Post by mali2297 on 2008-09-19
Do you use Nautilus?

[QUOTE=http://spuriousinterrupt.org/projects/xfce4#faq]Help!  My Xfce desktop disappeared!  It looks like GNOME!  And the desktop menu is gone too!  What do I do?

    * 	You ran nautilus, didn't you?  By default, Nautilus takes over the desktop when it runs.  First you need to kill Nautilus, and then you should run xfdesktop to make sure Xfce's desktop manager is running.  In the future, when you run Nautilus, pass it the --no-desktop option to instruct it to avoid drawing the desktop.  A more permanent solution is to set the gconf key /apps/nautilus/preferences/show_desktop to "false" (the --no-desktop will no longer be required).  This can be done using the graphical gconf-editor, or the command-line gconftool utility.[/QUOTE]

---

### Post by frankleeee on 2008-09-19
Are you using more then one desktop? if you are using a auto login hit ctrl alt backspace to stop x and to bring up the login window hit options choose xfce and log in and you will be asked if you want it as default, or just this session. I am assuming you have xubuntu desktop with the gnome Ubuntu desktop or some combination.

---

### Post by zagas on 2008-09-22
franklee you are right.Thanks to all.

---

