---
title: "No GnomeApp widget in glade available"
date: 2006-01-06
forum: Programming Talk
---

### Post by Danila on 2006-01-06
I started with some gnome programming tutorials and saw a GnomeApp widget in one of it ([http://www.micahcarrick.com/v2/content/view/13/3/)](http://www.micahcarrick.com/v2/content/view/13/3/)), I would like to use it, but this class is not available in my glade.

How can I "add" the GnomeApp widget to glade?

---

### Post by m87 on 2006-01-06
[quote=Danila]I started with some gnome programming tutorials and saw a GnomeApp widget in one of it ([http://www.micahcarrick.com/v2/content/view/13/3/)]("http://www.micahcarrick.com/v2/content/view/13/3/%29"), I would like to use it, but this class is not available in my glade.

How can I "add" the GnomeApp widget to glade?[/quote]

is it a custom widget? i don't get what it does and what the screenshot explains

---

### Post by GazaM on 2006-01-07
You can use the GnomeApp window widget in Glade when creating a Gnome project. Basically, when you start a new project in Glade it should give you the option of creating a GTK+ project or a Gnome project. If you select the Gnome project, certain Gnome specific widgets will become available to you.

---

### Post by m87 on 2006-01-07
[quote=GazaM]You can use the GnomeApp window widget in Glade when creating a Gnome project. Basically, when you start a new project in Glade it should give you the option of creating a GTK+ project or a Gnome project. If you select the Gnome project, certain Gnome specific widgets will become available to you.[/quote]

AHH. It's a glade-specific thing... ok, that's the glade-gnome stuff... anyway i don't recommend using "GNOME project" in glade, it's on the road to deprecation :)
sorry for the misunderstanding, i rarely use glade :)

~marco

---

### Post by pisewip on 2008-02-20
If you are using Glade 3 you have to install the glade-gnome-3 package to be able to look at Gnome elements

---

### Post by pisewip on 2008-02-20
For add a BonoboDockItem to the BonoboDock the only way I've found is right-click the BonoboDockItem, copy it, then select the BonoboDock and paste it inside.
There is another way, to add a BonoboDockItem to a BonoDock?

---

