---
title: "[Gtkmm] howto get rid of warning"
date: 2010-02-23
forum: Programming Talk
---

### Post by kahumba on 2010-02-23
Hi,
I have this code:
```

bool DetailsTable::on_button_press_event (GdkEventButton* event) {
    
    if(event->button == 1 && event->type == Gdk::DOUBLE_BUTTON_PRESS) {
        std::cout << "it's double click" << std::endl;
    }
    return false;
}

```and it compiles and works fine but the compiler keeps warning me, how do I get rid of this warning?

> 
warning: comparison between &#8216;enum GdkEventType&#8217; and &#8216;enum Gdk::EventType&#8217;
Looks like I'm accessing the "unwrapped" enum of Gtk..

---

### Post by kahumba on 2010-02-23
Nevermind, used GDK_2BUTTON_PRESS and warning is gone, though I don't know why I have to use C Gtk+ instead of Gtkmm.

---

### Post by SledgeHammer_999 on 2010-02-23
> **kahumba said:**
> Nevermind, used GDK_2BUTTON_PRESS and warning is gone, though I don't know why I have to use C Gtk+ instead of Gtkmm.

Probably because the function provides a [GdkEventButton](http://library.gnome.org/devel/gdk/stable/gdk-Event-Structures.html#GdkEventButton) and not a Gdk::EventButton(which doesn't seem to exist in gtkmm :S)

---

