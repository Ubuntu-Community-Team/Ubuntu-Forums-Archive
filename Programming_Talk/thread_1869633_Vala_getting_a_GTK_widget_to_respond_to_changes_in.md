---
title: "Vala: getting a GTK widget to respond to changes in system settings"
date: 2011-10-26
forum: Programming Talk
---

### Post by V for Vincent on 2011-10-26
Hi, I'm working on a graphical frontend to some system settings. I'm kind of new to Vala and GTK, but getting the UI to look the way I want it too went surprisingly smoothly. What's giving me trouble, though, is adding the logic behind it. I've added the following bit of testing code, but I just can't see the switch (which is initially on) jump back to off.

```

var settings = new Settings ("org.gnome.settings-daemon.peripherals.mouse");
settings.changed["locate-pointer"].connect (() => {
    this.switch_horizontal_scroll.set_active(false);
});

```

The switch is an ordinary Gtk.Switch. Never mind that locate pointer is different from horizontal scroll, I just picked out some random items to see if the mechanism works. Pretty much the same code works in a console application which just prints out that there was a change, but I can't get the widget to change.

---

