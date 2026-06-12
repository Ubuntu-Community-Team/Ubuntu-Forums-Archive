---
title: "Click event for GtkDrawingArea"
date: 2010-04-24
forum: Programming Talk
---

### Post by PaulM1985 on 2010-04-24
Hi

I am using a GtkDrawingArea with xine to create a video screen.  I want to add events so that I can click on the screen and this will toggle whether the media controls are visible or not.  So far I have used:

```

void onScreenClicked(GtkWidget *widget, gpointer data) {
	std::cout << "screen clicked" << std::endl;
}

// in my method initialising everything
	g_signal_connect(userInterface.vidScreen, "clicked",
					G_CALLBACK(onScreenClicked),&(userInterface.xine));

```

The problem I am having is when I run the program I get:
```
(<unknown>:5499): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.22.3/gobject/gsignal.c:2270: signal `clicked' is invalid for instance `0x8138858'
```

I am guessing this is because the area cannot accept click events.  Is there no way to add one?

Paul

---

### Post by simeon87 on 2010-04-24
I'm using "button_press_event" as signal in my Gtk program in Python so the error message is correct: the "clicked" signal is not valid. If that doesn't work, you can also try "button-press-event".

---

### Post by PaulM1985 on 2010-04-24
Thanks.  Thats work.

---

