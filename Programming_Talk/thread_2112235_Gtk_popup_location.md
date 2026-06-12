---
title: "Gtk popup location"
date: 2013-02-04
forum: Programming Talk
---

### Post by bird1500 on 2013-02-04
Hi,
I'm creating and show_all() a Gtk::Menu at runtime, when user moves the mouse over a menu item by processing the signal_select() of a menu item.

The issue is the menu doesn't show up at the (right) end of the item it's tied to (MenuItem->set_submenu(menu)), but at the cursor location, or, first at the cursor location then at the proper place.

How can I fix it to show straight at the right-end of the item it's tied to?

[Video]("http://www.youtube.com/watch?v=2Nxdf9P3SHs").

I tried
menu->popup(3, 0);
and longer version:
menu->popup(*this, *openWithItem, slot, 3, timeMs);

None seem to work, also I don't know what the time is for, setting it to present, past or future doesn't seem to have any effect.

---

### Post by bird1500 on 2013-02-04
Apparently the main issue was sigc::slot was going out of scope, so:
1) Define sigc::slot in the class constructor.
```

slot = sigc::mem_fun(*this, &Popup::on_popup_menu_pos);

```2) In the create components function:
```

openWithItem->set_submenu(*menu);
openWithItem->show_all();
menu->popup(*this, *openWithItem, slot, 0, 0);

```3) The virtual function computing the correct position:
```

void
Popup::on_popup_menu_pos(int &x, int &y, bool &pushIn)
{
    openWithItem->get_window()->get_origin(x, y);
    x += openWithItem->get_width();
}

```

[Video]("http://www.youtube.com/watch?v=Cz-wOHWfKW4").

Still don't have a clue what the mouse button and time params in popup() are for. I just set them to zero which still works ok.

---

