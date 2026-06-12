---
title: "[PyGTK] About Dialogue does not load once already closed!"
date: 2009-08-03
forum: Programming Talk
---

### Post by Umang on 2009-08-03
Hi!
I'm coding a small game called [Pynagram]("https://launchpad.net/pynagram"). I have used Glade (with gtk.Builder, not libglade) to make this game. I have a problem with the About Dialogue (which can be reproduced by starting a project from scratch also).

On an event (eg. menu item activate or button clicked, etc) I have the following code:
```
self.widgets["aboutdialog1"].run()
```
The About dialogue appears, as expected.

Now if you close the about dialogue window and try to open the window again, a tiny window (with only the title bar showing, and hardly any width) opens. Since the close button also doesn't show in the window, either Esc or right-click -> Close is required to close the window. Also, opening the about dialogue a second time yields the following terminal output (doesn't come when opening for the first time):
> XYZ.py:123: GtkWarning: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed.

Where is the error, on my part or in PyGTK? What should I do?

Thanks so you much

Umang

PS: If you want to see the code and don't want to download Pynagram then I've attached a simple program that just opens the about dialogue only.

If you want to download Pynagram then type in: "bzr branch lp:pynagram" into the terminal (in an appropriate directory, of course). [Or download pynagram from Launchpad.]("https://launchpad.net/pynagram/+download")

[Pynagram bug report on Launchpad]("https://bugs.launchpad.net/pynagram/+bug/406936").

---

### Post by days_of_ruin on 2009-08-03
This works:
```
def on_m_help_about_activate(self, widget, data=None):
        self.widgets["about_pynagram"].run()
        self.widgets["about_pynagram"].hide()

```

This just hides the dialog instead of destroying it which is what you were doing.

---

### Post by Umang on 2009-08-04
Thanks!

I could have sworn the "Close" button would not work unless I connected an event... Now it just works, without any events!

Thanks again!

---

