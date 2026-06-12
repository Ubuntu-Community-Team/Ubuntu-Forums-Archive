---
title: "Gtkmm: Right click menus?"
date: 2012-09-14
forum: Programming Talk
---

### Post by fallenshadow on 2012-09-14
Hi all,

I have been working on getting my right click menu to work recently. Documentation seems sparse on this... but this is what I have so far:

```
bool mainWindow::on_button_press_event(GdkEventButton* event)
{
	
  if( (event->type == GDK_BUTTON_PRESS) && (event->button == 3) )
  {
	Gtk::Menu *m_Menu_Popup = new Gtk::Menu();
	Gtk::MenuItem *pItem = new Gtk::MenuItem("item1");
	Gtk::MenuItem *pItem2 = new Gtk::MenuItem("item2");
	m_Menu_Popup->add(*pItem);
	m_Menu_Popup->add(*pItem2);
	m_Menu_Popup->show_all();
    m_Menu_Popup->popup(event->button, event->time);
    return true; //It has been handled.
  }
  else
    return false;
}
```

I also have these declared above:

```

protected:
        bool on_button_press_event(GdkEventButton* event);
	
private:
	Gtk::Menu* m_Menu_Popup;

```

Anyone ever worked with these?

---

### Post by PaulM1985 on 2012-09-14
In your function:
bool mainWindow::on_button_press_event(GdkEventButton* event)

You declare a LOCAL variable: m_Menu_Popup, which you initialise, add menu items etc.

You also have a CLASS variable with the same name.

You haven't mentioned what your problem is, or what is going wrong, so I don't know how to help you.  I just noticed the issue described above.

Paul

---

### Post by fallenshadow on 2012-09-14
Ok I got rid of the class variable.

Well to put it simply, it doesn't work. The code compiles but no menu pops up when I right click.

---

