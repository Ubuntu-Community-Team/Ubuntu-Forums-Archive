---
title: "Problem with GNOME Development"
date: 2009-10-04
forum: Programming Talk
---

### Post by Masterofpsi on 2009-10-04
Hi, I am having a problem trying to develop a GNOME app using the Glade graphical builder.

I have installed glade and glade-gnome, but when I open Glade, all of the GNOME widgets are greyed out. That is, everything in the pallete under "GNOME User Interface," "GNOME UI Obsolete" and "GNOME Canvas" is visible, but greyed out, and unusable.

Has anyone had this problem/have any idea how to fix this?

---

### Post by haTem on 2009-10-04
I think those are all depreciated. I remember reading that libgnomeui was being phased out in gnome 2.28.

I'm assuming you're using glade-3. Those are all grayed out if you select GtkBuilder as the file format when you create a new project. If you really need those widgets, select libglade as the file format instead, but keep in mind libglade is also depreciated, and you really shouldn't use it if you're making a new project.

Edit: Which of those widgets did you need? I think they all have replacements in gtk. Druid=Assistant, Cavnas=Drawing Area, etc. If you post which ones you need, someone could point you to what the modern equivalent is.

---

### Post by Masterofpsi on 2009-10-04
> **haTem said:**
> I think those are all depreciated. I remember reading that libgnomeui was being phased out in gnome 2.28.

I'm assuming you're using glade-3. Those are all grayed out if you select GtkBuilder as the file format when you create a new project. If you really need those widgets, select libglade as the file format instead, but keep in mind libglade is also depreciated, and you really shouldn't use it if you're making a new project.

Edit: Which of those widgets did you need? I think they all have replacements in gtk. Druid=Assistant, Cavnas=Drawing Area, etc. If you post which ones you need, someone could point you to what the modern equivalent is.

So Glade just isn't a good solution for GNOME development right now?

---

### Post by haTem on 2009-10-04
No, using the glade designer is fine. It's supported and widely used.

There's a difference between glade and libglade. Glade is the application itself that you use to design the UI. This part is fine. Libglade is the library you use to load the glade project file into your program (from C/C++/python/whatever). This part has been depreciated. Gtk now has the functionality to load a glade interface file built-in (starting from gtk 2.12 I think, but I'm not sure). It's called GtkBuilder and does the exact same thing libglade does. Just save your glade project in GtkBuilder format and you're all set!

So essentially it boils down to this. Before, in order for your program to use the interface you created with the glade designer, you had to have libglade installed to load it into your program. Now, all you need is a relatively recent version of gtk. Just use the GtkBuilder api.

Similarly, libgnomeui is being phased out in favor of the similar widgets that are already included in gtk. This all cuts down on external library usage, so that your program won't have to depend on so many external libraries.

---

### Post by mmix on 2009-10-06
> **Masterofpsi said:**
> So Glade just isn't a good solution for GNOME development right now?

IMHO, yes. gtk code simply fine.

---

