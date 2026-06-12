---
title: "GLib Signals"
date: 2008-01-01
forum: Programming Talk
---

### Post by caclratm on 2008-01-01
Hi,

I'm trying to modify clock.c in the code for gnome-panel so that the calendar widget is shown whenever the cursor hovers the button (so it's not necessary to click on the button anymore) but I'm kind of stuck. What is the signal that gets launched to activate the tooltips (I think that's the one I need)?

---

### Post by bruce89 on 2008-01-01
Based on GTK+'s documentation, it's "[query-tooltip]("http://library.gnome.org/devel/gtk/stable/GtkWidget.html#GtkWidget-query-tooltip")".

I suspect no-one's replied because Ubuntu tends to be rather Pythony.

---

### Post by caclratm on 2008-01-01
Actually, what I want to know is when is this signal called, so I can call another callback (the one that will show the calendar instead of showing the tooltip). How can I know that the cursor is over the button?

Thanks a lot anyway :)

---

### Post by caclratm on 2008-01-01
I think I just found it. My guess is that it is "enter-notify-event".

---

### Post by MicahCarrick on 2008-01-02
Yes, you should be able to do it by attaching your callbacks to "enter-notify-event" and "leave-notify-event".

---

