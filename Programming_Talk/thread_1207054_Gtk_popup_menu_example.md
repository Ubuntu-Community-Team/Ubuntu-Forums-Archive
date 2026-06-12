---
title: "Gtk popup menu example"
date: 2009-07-07
forum: Programming Talk
---

### Post by froggyswamp on 2009-07-07
```

//inside on button press function..
Gtk::Menu *pMenu = new Gtk::Menu();
Gtk::MenuItem *pItem= new Gtk::MenuItem("New File");
pMenu->add(*pItem);
pMenu->popup(event->button, event->time);

```Folks, what pops up is a thin line instead of a menu - as if the Gtk::MenuItem hasn't been added (properly), anyone knows what's the matter?

On the gtkmm site there's an example of popup menu created from a resource string, but I need to create my right-click pop up menu dynamically as above..

---

### Post by days_of_ruin on 2009-07-07
Do you get any errors? Are you sure you need to use "*"? I don't see that in the gtkmm tutorial [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-container-widgets.html#sec-single-item-containers]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-container-widgets.html#sec-single-item-containers").

---

### Post by monraaf on 2009-07-08
You have to call the show() method for the menuitem to be visible.

---

### Post by SledgeHammer_999 on 2009-07-08
> **froggyswamp said:**
> 
On the gtkmm site there's an example of popup menu created from a resource string, but I need to create my right-click pop up menu dynamically as above..

You can create the resource string dynamically too. I do it that way. The only thing you need afterwards is a way to indentify your dynamically added menuitems if you want to modify them on runtime. Just think of Gtk::UIManager as filesystem. Every widget it manages can be viewed as a "file" and every file has a path. Eg "/menubar/FileMenu/Open" this is the path of a menuitem(Open) in a menu(FileMenu) of a menubar(menubar).

---

### Post by froggyswamp on 2009-07-08
Thanks! I indeed had to call "show()" for every widget, or, looks like I can  just call "show_all":
```

//inside on_button_press_event function
Gtk::Menu *pMenu = new Gtk::Menu();
Gtk::MenuItem *pItem = new Gtk::MenuItem("New File");
Gtk::MenuItem *pItem2 = new Gtk::MenuItem("New Folder");
pMenu->add(*pItem);
pMenu->add(*pItem2);
pMenu->show_all();
pMenu->popup(event->button, event->time);

```

---

