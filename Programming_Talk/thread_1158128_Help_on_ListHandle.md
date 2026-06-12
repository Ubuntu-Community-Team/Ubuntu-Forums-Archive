---
title: "Help on ListHandle"
date: 2009-05-13
forum: Programming Talk
---

### Post by cl333r on 2009-05-13
Can anyone fill in the missing line please?

```

Glib::RefPtr<Gtk::IconTheme> iconTheme = Gtk::IconTheme::create();
    Glib::ListHandle<Glib::ustring> icons = iconTheme->list_icons();
    
    for( int i=icons.size()-1; i>=0; i--) {
	//HOW DO I PRINT EACH ITEM?
    }

```

couldn't figure out even after googling.
Maybe I'm trying to iterate the wrong way?

---

### Post by simeon87 on 2009-05-13
```

for ( Glib::ListHandle<Glib::ustring>::const_iterator it = icons.begin(); it != icons.end(); ++it ) {
    // use it->c_str() to use current item
}

```

(adapted from [http://inkscape.modevia.com/doxygen/html/document-properties_8cpp-source.php](http://inkscape.modevia.com/doxygen/html/document-properties_8cpp-source.php))

---

### Post by cl333r on 2009-05-13
Finally, thanks a lot!
I ended up with this:
```

Glib::RefPtr<Gtk::IconTheme> iconTheme = Gtk::IconTheme::create();
    Glib::ListHandle<Glib::ustring> icons = iconTheme->list_icons();

    for(Glib::ListHandle<Glib::ustring>::const_iterator it = icons.begin(); it != icons.end(); ++it) {
	Glib::ustring us = *it;
	cout << us.c_str() << endl;
    }

```

---

