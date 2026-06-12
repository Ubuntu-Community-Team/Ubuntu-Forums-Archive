---
title: "Gtk c++ change label text on button press"
date: 2009-05-18
forum: Programming Talk
---

### Post by Ikee on 2009-05-18
Hi!

I am currently trying to figure out how to change a labels text when pressing a button.

My Dialog(dialog1) window i simpel:
A label(label1) and two buttons(button_label and button_quit).

I've followed a tutorial on how to create a simpel dialog window but haven't figured out how to utilize several buttons and how it works.

Here's my source so far: [http://www.pasteall.org/5609](http://www.pasteall.org/5609)

Hope someone can tell me how to do so by giving me some source code it would be great.

Regards Ikee

---

### Post by days_of_ruin on 2009-05-18
You will need to get a reference to the label using the ```
refXml->get_widget
``` method. Then in the button press callback you just use the labels set_text function (or whatever its called).

---

### Post by Marco A on 2009-05-18
.

---

