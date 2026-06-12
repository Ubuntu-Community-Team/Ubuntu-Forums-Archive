---
title: "Oneiric Beta - Fast"
date: 2011-09-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fjgaude on 2011-09-05
The Beta of 11.10 is fast:

Intel Core i5 655K, GMA HD video, 4GH, 4GB RAM at 1333MH, x64 Unity 3D, home-built box.

Ubuntu 11.10 Beta 1:
GtkPerf 0.40 - Starting testing: Mon Sep  5 09:06:59 2011

GtkEntry - time:  0.03
GtkComboBox - time:  0.93
GtkComboBoxEntry - time:  0.82
GtkSpinButton - time:  0.09
GtkProgressBar - time:  0.08
GtkToggleButton - time:  0.56
GtkCheckButton - time:  0.08
GtkRadioButton - time:  0.15
GtkTextView - Add text - time:  0.37
GtkTextView - Scroll - time:  0.07
GtkDrawingArea - Lines - time:  1.51
GtkDrawingArea - Circles - time:  2.19
GtkDrawingArea - Text - time:  0.84
GtkDrawingArea - Pixbufs - time:  0.22
 --- 
Total time:  **7.94**

Now for Ubuntu 11.04:
GtkPerf 0.40 - Starting testing: Mon Sep  5 09:13:41 2011

GtkEntry - time:  0.02
GtkComboBox - time:  0.99
GtkComboBoxEntry - time:  0.86
GtkSpinButton - time:  0.10
GtkProgressBar - time:  0.09
GtkToggleButton - time:  0.54
GtkCheckButton - time:  0.09
GtkRadioButton - time:  0.15
GtkTextView - Add text - time:  0.44
GtkTextView - Scroll - time:  0.15
GtkDrawingArea - Lines - time:  1.27
GtkDrawingArea - Circles - time:  5.81
GtkDrawingArea - Text - time:  0.71
GtkDrawingArea - Pixbufs - time:  0.13
 --- 
Total time: **11.37**

That's a clean **30% improvement** for 11.10 over 11.04. Way to go, guys!

---

### Post by t1497f35 on 2011-09-05
It has (almost) nothing to do with Oneiric nor with the Ubuntu devs, Oneiric simply ships with Mesa 7.11 to which the Intel developers submitted a lot of improvements.
If you follow phoronix.com you know what i mean.

---

### Post by fjgaude on 2011-09-05
It seems that the updated GTK had something to do with the improvements, eh? And also the new gnome?

---

### Post by t1497f35 on 2011-09-05
Obviously every new Gtk/Gnome release brings something to the table, but in your case the bulk of the speed comes from the newer Intel drivers. Hence imo Oneiric is the first Ubuntu release to ship with plausible Intel graphics drivers.

As to Gtk3/Gnome3, GDK drawing has been dropped in favor of Cairo, that's pretty much all I can figure out why Gtk3 would be faster than Gtk2 at drawing stuff:
[www.phoronix.com/scan.php?page=news_item&px=ODUxNA]("http://www.phoronix.com/scan.php?page=news_item&px=ODUxNA")

---

### Post by fjgaude on 2011-09-05
Yes, Cairo could be the reason that Oneiric draws circles so much faster than Natty.

---

### Post by lucazade on 2011-09-05
> **t1497f35 said:**
> Obviously every new Gtk/Gnome release brings something to the table, but in your case the bulk of the speed comes from the newer Intel drivers. Hence imo Oneiric is the first Ubuntu release to ship with plausible Intel graphics drivers.

As to Gtk3/Gnome3, GDK drawing has been dropped in favor of Cairo, that's pretty much all I can figure out why Gtk3 would be faster than Gtk2 at drawing stuff:
[www.phoronix.com/scan.php?page=news_item&px=ODUxNA]("http://www.phoronix.com/scan.php?page=news_item&px=ODUxNA")

agreed probably in this case mesa intel makes the differences, xorg is also still the same of natty.

It could be nice to see a gtkperf based on gtk3 to see gdk<>cairo and murrine<>unico rendering performances.

---

### Post by fjgaude on 2011-09-05
Now for a **Maverick**, gnome, 10.10 (2.6.35-30 kernel) with the same Intel-based computer:

GtkPerf 0.40 - Starting testing: Mon Sep  5 12:15:33 2011

GtkEntry - time:  0.02
GtkComboBox - time:  0.85
GtkComboBoxEntry - time:  0.81
GtkSpinButton - time:  0.12
GtkProgressBar - time:  0.09
GtkToggleButton - time:  0.50
GtkCheckButton - time:  0.07
GtkRadioButton - time:  0.10
GtkTextView - Add text - time:  0.41
GtkTextView - Scroll - time:  0.24
GtkDrawingArea - Lines - time:  0.94
GtkDrawingArea - Circles - time:  3.37
GtkDrawingArea - Text - time:  0.81
GtkDrawingArea - Pixbufs - time:  0.14
 --- 
Total time:  **8.48**

---

