---
title: "Listing Windows Per Monitor?"
date: 2010-07-04
forum: Programming Talk
---

### Post by detrate on 2010-07-04
I found this great applet called [DockbarX](http://launchpad.net/dockbar), which more or less emulates the Windows 7 Superbar.  I like it better than the "Window List" applet in all ways except one.  The way it handles dual monitors.  DockbarX assumes one instance of itself and collects windows from the entire "X Screen".  In my case, I'm using Nvidia TwinView, which defines both monitors as one "X Screen" and gives "hints" to the WM about drawing widnows.  All of these tools (wnck, xrandr, xwminfo) are seeing both monitors as screen0 and do not seem to have any knowledge about these hints.

I suppose a work around here would be to change my setup to xinerama but that would be going in the wrong direction. This should be possible with TwinView, I'm just not sure how.

The current code uses the wnck module which seems to be ignorant of multi monitors.

Thanks to the [PyGTK docs](http://www.pygtk.org/docs/pygtk/gdk-functions.html), I was able to put together a proof of concept in distinguishing the monitors through code but I'm not sure how to create a list of window objects from it.

```
#!/usr/bin/python
import gtk

screen = gtk.gdk.screen_get_default()
print screen.get_n_monitors()
print screen.get_monitor_geometry(0)
```

The above will get me proper output, (2 monitors, proper geometry for monitor 0) but the screen object is different than wnck's so I cannot just replace:

```
self.screen = wnck.screen_get_default()
```
with
```
self.screen = gtk.gdk.screen_get_default()
```

Any suggestions, hints or tips are very much appreciated.

---

