---
title: "[SOLVED] Customizing gnome"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by pikabuntu on 2008-07-10
How can I learn how to customize gnome more?
I would like to know how to be able to put things like custom buttons (instead of the standard ubuntu symbol  for the menu & stuff like that) on the panels, etc.

(also, when is inappropriate to keep using the absolute beginner section)

---

### Post by RiceMonster on 2008-07-10
Check out [http://www.gnome-look.org](http://www.gnome-look.org). 

If you want to change the icons, look under icon themes, then download a theme you like, extract it, and copy or move it to ~/.icons. If you want to change your GTK/metacity theme, do the same, but copy or move it to ~/.themes. 

Then change your icon theme at system > preferences > appearance. To change just the icon theme, click on customize.

---

### Post by iaculallad on 2008-07-10
What about exploring gconf-editor?

---

### Post by pikabuntu on 2008-07-10
> **iaculallad said:**
> What about exploring gconf-editor?

what exactly is this?

EDIT:
Ok, i found it but how do i use it?

---

### Post by RiceMonster on 2008-07-10
It's where you can access all the advanced gnome options (and it looks a lot like regedit.exe to me). Hit alt-f2 and type gconf-editor

---

### Post by sdennie on 2008-07-10
> **pikabuntu said:**
> what exactly is this?

I agree with iaculallad in that gconf-editor allows you to customize your system in fairly powerful way.  It presents essentially all available options for a particular application and allows you to tweak otherwise unavailable options.  However, before you start playing with settings in gconf-editor, I *highly* recommend that you first:

```

cd
tar cvf gconf.tar .gconf

```

In the unlikely event that you break your machine by changing gconf settings, this will insure that you have a backup of settings that are known to work.

---

### Post by iaculallad on 2008-07-10
> **pikabuntu said:**
> what exactly is this?

EDIT:
Ok, i found it but how do i use it?

The graphical equivalent of gconftool.

GUI editor for the GConf  configuration database. It is being used to tweak preferences on GNOME.

To access it: Press Alt+F2 and type gconf-editor.

EDIT: And if you need to recover your default settings (in gconf-editor), then you only need to delete ~.gconf and ~.gconfd directories.

---

### Post by pikabuntu on 2008-07-10
thanx

---

