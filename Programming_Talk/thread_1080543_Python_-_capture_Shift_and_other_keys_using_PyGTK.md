---
title: "Python - capture Shift and other keys using PyGTK"
date: 2009-02-25
forum: Programming Talk
---

### Post by tom66 on 2009-02-25
I am using the following code:

```

# This class mangages the editing interface, where the canvas is drawn.
# It also manages drag-and-drop decoding, and many other actions.
class EditorInterface(gtk.DrawingArea):

...
    
    # Initializer. 
    # parameters: view, slide
    def __init__(self, view, slide):

...

        # Unmask events.
        self.add_events(gdk.BUTTON_PRESS_MASK | gdk.BUTTON_RELEASE_MASK | gdk.POINTER_MOTION_MASK | gdk.KEY_PRESS_MASK | gdk.KEY_RELEASE_MASK)
    
        # Set up events.
        self.connect("key_press_event", self.key_press)
        self.connect("button_press_event", self.button_press)
        self.connect("button_release_event", self.button_release)
        self.connect("motion_notify_event", self.motion_notify)
        self.connect("expose_event", self.expose)

...

    # Key press handler.
    # parameters: widget, event
    def key_press(self, widget, event):
        # Reset all states. We'll set them back again if necessary.
        self.shiftPressed = False
        warning.print_debug("Key pressed. ")
            
        # Shift pressed?
        if event.state & gdk.SHIFT_MASK:
            warning.print_debug("SHIFT pressed. ")
            self.shiftPressed = True

```

But it doesn't work. :( Any help appreciated.

---

### Post by Can+~ on 2009-02-25
Are you using the Eventbox? (I can't tell as the script is snipped)

[http://www.pygtk.org/pygtk2tutorial/ch-ContainerWidgets.html#sec-EventBox](http://www.pygtk.org/pygtk2tutorial/ch-ContainerWidgets.html#sec-EventBox)

---

### Post by tom66 on 2009-02-25
No, I'm using a GtkDrawingArea... do I need an EventBox to capture keyboard events?

---

### Post by imdano on 2009-02-25
Is your callback getting run at all, or is checking for shift being held down just not working?  I'm not sure that this will fix your problem, but you probably want to use a key_release_event instead of a key_press_event.

---

### Post by tom66 on 2009-02-25
Callback isn't running, at all. No debug messages, no key response, nothing. Oh, and I tried using key_release_event. Didn't do anything different.

---

### Post by simeon87 on 2009-02-25
The drawing area needs to have focus so you have to set can_focus. You may also need grab_focus () to actually give it the focus.

---

### Post by tom66 on 2009-02-25
It worked when I set focus (I started getting key events, which was great). However, it still doesn't pick up the shift modifier. Is it possible to just pick up shift without any other keys depressed? (I ask this because I want to add the ability to select multiple objects in my program, by depressing the shift key.) I believe it's possible, because pressing the shift key *does* produce events.

---

