---
title: "How to restore icons"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by riftt on 2011-09-24
I upgraded to Oneiric and I am using fluxbox as default wm. All is well except the icons do not appear in PCManFM (nor in Nautilus). I attached an screenshot.

Is there something that I have to add to fluxbox autostart?

---

### Post by dino99 on 2011-09-24
load it from a terminal to see if you get some warnings/errors, but fluxbox may not had much maintenance and portage to run on our new beta; maybe Lubuntu is a better choice or gnome-session-fallback to have a gtk2 like.

---

### Post by riftt on 2011-09-24
Thank you for the reply. I will study the Lubuntu session starting scripts maybe I will find the answer.

Just a side note: I tried Openbox and there are no icons either.

The output in the terminal just says that the it cannot load the icons:

** (pcmanfm:2747): DEBUG: unable to load icon media-eject
** (pcmanfm:2747): DEBUG: unable to load icon user-home

(pcmanfm:2747): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (pcmanfm:2747): DEBUG: unable to load icon user-desktop

(pcmanfm:2747): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (pcmanfm:2747): DEBUG: unable to load icon system-software-install

(pcmanfm:2747): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (pcmanfm:2747): DEBUG: unable to load icon folder

(pcmanfm:2747): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
** (pcmanfm:2747): DEBUG: unable to load icon . GThemedIcon folder inode-directory gnome-mime-inode-directory inode-x-generic
** (pcmanfm:2747): DEBUG: unable to load icon . GThemedIcon application-pdf gnome-mime-application-pdf x-office-document application-x-generic
** (pcmanfm:2747): DEBUG: unable to load icon preferences-desktop-wallpaper
** (pcmanfm:2747): DEBUG: unable to load icon accessories-calculator
** (pcmanfm:2747): DEBUG: unable to load icon computerjanitor
** (pcmanfm:2747): DEBUG: unable to load icon preferences-desktop-remote-desktop

---

### Post by riftt on 2011-10-05
For completeness I post here the solution I found:

install Tango or Oxygen icons like this:

sudo apt-get install tango-icon-theme tango-icon-theme-extras

or:

sudo apt-get install oxygen-icon-theme oxygen-icon-theme-complete

create a file ~/.gtkrc.mine

And place the following line in it:

gtk-icon-theme-name = "Tango"

or:

gtk-icon-theme-name = "oxygen"

and the pcmanfm icons are back :)

---

