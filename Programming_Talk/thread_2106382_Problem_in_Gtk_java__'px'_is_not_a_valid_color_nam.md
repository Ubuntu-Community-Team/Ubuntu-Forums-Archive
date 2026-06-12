---
title: "Problem in Gtk java : 'px' is not a valid color name"
date: 2013-01-18
forum: Programming Talk
---

### Post by c2tarun on 2013-01-18
Hi friends,

I am trying to learn Gtk Development with java, from this tutorial: [http://zetcode.com/gui/javagnome/firststeps/d](http://zetcode.com/gui/javagnome/firststeps/d)   
I am getting this error

```
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:91:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:177:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:179:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:239:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:245:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:298:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:311:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:317:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:335:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:460:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:467:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:474:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:480:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:486:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:492:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:498:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:505:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:512:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:518:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:524:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:533:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:654:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:663:17: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:829:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:834:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:891:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:909:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:927:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:945:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1061:28: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1109:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1141:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1196:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1318:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1338:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1389:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1401:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1412:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1449:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1456:23: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1597:17: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1806:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1821:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1833:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1846:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1903:0: unknown @ rule
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1988:97: 'currentColor' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:1996:32: Junk at end of value
DANGER: Gtk-WARNING, Theme parsing error: gtk-widgets.css:2008:13: 'animation' is not a valid property name
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:16:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:33:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:207:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:214:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:226:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:239:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:400:18: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:431:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:447:24: Horizontal and vertical offsets are required
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:458:23: 'px' is not a valid color name
DANGER: Gtk-WARNING, Theme parsing error: gtk-apps.css:463:23: 'px' is not a valid color name
Exception in thread "main" org.gnome.glib.FatalError: Gtk-WARNING
Theme parsing error: gtk-widgets.css:91:23: 'px' is not a valid color name
	at org.gnome.gtk.GtkMain.gtk_init(Native Method)
	at org.gnome.gtk.GtkMain.init(GtkMain.java:54)
	at org.gnome.gtk.Gtk.init(Gtk.java:95)
	at com.zetcode.GSimple.main(GSimple.java:26)

```

 I tried googling but the pages containing solution are in different language and google translator is not able to help.

Here is my code: 

```
package com.zetcode;

import org.gnome.gdk.Event;
import org.gnome.gtk.Gtk;
import org.gnome.gtk.Widget;
import org.gnome.gtk.Window;
import org.gnome.gtk.WindowPosition;

public class GSimple extends Window {
	public GSimple(){
		setTitle("Simple");
		
		connect(new Window.DeleteEvent() {
			@Override
			public boolean onDeleteEvent(Widget arg0, Event arg1) {
				Gtk.mainQuit();
				return false;
			}
		});
		
		setDefaultSize(250, 100);
		setPosition(WindowPosition.CENTER);
		show();
	}
	public static void main(String[] args) {
		Gtk.init(args);
		new GSimple();
		Gtk.main();
	}

}

```

Can anyone please help me with this problem?

---

### Post by helpee on 2013-01-18
Don't use 'px' as a color name lol

I couldn't find any reference to a color setting in the code on that page, "http://zetcode.com/gui/javagnome/firststeps/" so I can't really debug it for you blind.

---

### Post by c2tarun on 2013-01-20
bump

---

### Post by Toz on 2013-01-20
I think this is related to your theme and the version of GTK that you are using. I saw this error back in 12.04 with certain themes but haven't seen it yet in 12.10 (Bluebird theme). 

Have a look at this bug report for a possible workaround: [https://bugs.launchpad.net/ubuntu/+source/gnome-themes-standard/+bug/1052353]("https://bugs.launchpad.net/ubuntu/+source/gnome-themes-standard/+bug/1052353").

---

### Post by c2tarun on 2013-01-21
> **Toz said:**
> I think this is related to your theme and the version of GTK that you are using. I saw this error back in 12.04 with certain themes but haven't seen it yet in 12.10 (Bluebird theme). 

Have a look at this bug report for a possible workaround: [https://bugs.launchpad.net/ubuntu/+source/gnome-themes-standard/+bug/1052353]("https://bugs.launchpad.net/ubuntu/+source/gnome-themes-standard/+bug/1052353").

Thanks a lot :)
It was a theme problem only, I changed back to ambiance and it is working now.

---

