---
title: "Play &quot;alert&quot; sound"
date: 2010-10-15
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-15
In System->Preferences->Sound is an option to set the system "alert" sound.

How would one go about programming to actually playing said chosen alert sound?


p.s. dw... found it :)
[php]
  gdk_display_beep(gtk_widget_get_display(MainWindow));
[/php]

where "MainWindow" is any GtkWidget on that display

---

