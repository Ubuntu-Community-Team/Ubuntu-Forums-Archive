---
title: "[Gtk] Programmatically get theme's selected row color?"
date: 2011-05-25
forum: Programming Talk
---

### Post by t1497f35 on 2011-05-25
Hi,
Any ideas?
see 1st screenshot.

I'm drawing a widget (with Cairo) that's supposed to look like a gtk table, so when a user clicks on such a "row" it's supposed to be redrawn with the background color corresponding to the current theme background color for a selected table row. So far I'm using a hard-coded yellow background color for a selected row, see 2nd screenshot.

---

### Post by t1497f35 on 2011-05-25
[PHP]
Gtk::Table table;
Glib::RefPtr<Gtk::Style> pTableStyle = Gtk::RC::get_style(table);
Gdk::Color c = pTableStyle->get_bg(Gtk::STATE_SELECTED);
double tableBgSelColors[3];
tableBgSelColors[0] = c.get_red_p();
tableBgSelColors[1] = c.get_green_p();
tableBgSelColors[2] = c.get_blue_p();
[/PHP]Not an ideal solution cause I have to create a real Gtk::Table to query for its style, that ain't too bad though, at least I can use the right bg color now (see screenshot).

---

