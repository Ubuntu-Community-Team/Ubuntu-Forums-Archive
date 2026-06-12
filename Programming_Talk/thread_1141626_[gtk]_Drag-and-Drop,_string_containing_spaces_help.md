---
title: "[gtk] Drag-and-Drop, string containing spaces help!"
date: 2009-04-28
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-04-28
Hi I am using gtkmm and have set a DND drop site which accepts text/plain targets. I am using it to accept files. The problem is, when I drop a file which has spaces in its name. The spaces are converted to "%20". Is there a way to get the spaces instead of the "%20"? 

I pass the path to gstreamer and it doesn't accept "%20".

I use the **get_text()** and **get_data_as_string()** methods of [Gtk::SelectionData](http://gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1SelectionData.html)

Any help is appreciated.

---

