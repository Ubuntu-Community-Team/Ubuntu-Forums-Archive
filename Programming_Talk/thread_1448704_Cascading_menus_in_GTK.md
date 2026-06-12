---
title: "Cascading menus in GTK"
date: 2010-04-07
forum: Programming Talk
---

### Post by kumoshk on 2010-04-07
In GTK (I use Vala), how do I make cascading menus? I had a hard time trying to figure this out from the documentation, and I did a lot of experimenting.

Thanks!

---

### Post by SledgeHammer_999 on 2010-04-07
What do you mean by "cascading menus"? Can you give a screenshot-example?

---

### Post by kumoshk on 2010-04-07
> **SledgeHammer_999 said:**
> What do you mean by "cascading menus"? Can you give a screenshot-example?

Hmm. Print screen doesn't seem to work while I have a menu open.

Anyway, I mean nested menus&#8212;like in Firefox when you open the Bookmarks menu and then within there you'll see folders (or what I called cascading menus). You hover on the folder (a menu item with an arrow by it) and another menu opens up. Does that make sense?

Example:

Bookmarks->Bookmarks Toolbar->Latest Headlines->BBC World News

as opposed to

Bookmarks->Some site

In the program I'm making I want to do this:
Bookmarks->Remove bookmark->list of bookmarks to remove

Right now, I just have Remove Bookmarks as a top-level menu item, right next to Bookmarks (but I think it would be too easy to use by mistake, there, and it's not the most aesthetically appealing place for it).

---

### Post by steeleyuk on 2010-04-07
You just use a normal MenuItem widget, and then use [set_submenu()]("http://library.gnome.org/devel/gtk/unstable/GtkMenuItem.html#gtk-menu-item-set-submenu") to attach another Menu widget to the MenuItem.

Note: I don't know the exact code in Vala, coming from a PyGTK perspective.

Edit: You've already done something similar. Dated from November 2009. [http://ubuntuforums.org/showthread.php?t=1336048](http://ubuntuforums.org/showthread.php?t=1336048)

---

### Post by kumoshk on 2010-04-07
> **steeleyuk said:**
> You just use a normal MenuItem widget, and then use [set_submenu()]("http://library.gnome.org/devel/gtk/unstable/GtkMenuItem.html#gtk-menu-item-set-submenu") to attach another Menu widget to the MenuItem.[/url]

Awesome! It works great. Thanks!

(Using an extra MenuItem instead of what I had labeled as a launcher in my other post linked to above. Well, that was a MenuItem, but you get the idea&#8212;just using the sub_menu function on a regular MenuItem, I mean&#8212;not only on top-level ones.)

---

