---
title: "[SOLVED] C++ can't connect mouse event to Gtk::DrawingArea"
date: 2008-06-12
forum: Programming Talk
---

### Post by xlinuks on 2008-06-12
Hi, can someone please write a working snippet so that when clicking on a Gtk::DrawingArea it prints "clicked"?
I tried binding signal handlers but couldn't. It compiles fine but doesn't work.
I have
```

class PaintArea : public DrawingArea {...}

```
Then inside the constructor I write:
```

signal_button_press_event().connect( sigc::mem_fun( *this, &PaintArea::onMouseDown ) );

```

The onMouseDown method is:
```

bool PaintArea::onMouseDown( GdkEventButton *event ) {
	cout << "clicked" << endl;
        return true;
}


```
But I never get to see the "clicked" line printed.
On the other hand the on_expose_event works fine, but unfortunately I not only need to do custom painting but also track the mouse events.

---

### Post by xlinuks on 2008-06-12
Turns out windows don't accept mouse events unless one first enables support for mouse events one is interested in, like this:
```

pWindow->add_events( Gdk::BUTTON_PRESS_MASK | Gdk::BUTTON_RELEASE_MASK );

```

---

