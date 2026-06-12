---
title: "Python - pygtk2 - version confusion..."
date: 2009-10-16
forum: Programming Talk
---

### Post by BkkBonanza on 2009-10-16
Hello,

I'm writing a program using pygtk. 
I seem to have run into a roadblock where I want to use gtk.CellRendererCombo but it is not present. But I'm confused about this.
My code references this widget and I get no error but it doesn't work.

I'm using Ubuntu 9.04 and according to Synaptics my version of python-pygtk2 is 2.14. Is Ubuntu really this far behind? According to the pygtk docs this widget is only available in 2.6.

I've tried looking around to find pygtk 2.6 in any repos so I can easily install it. I mean if I write this program I'll want the suitable version of pygtk to be easy for users to get.

So I'm confused about this. According to the docs the Combo widget is deprecated in 2.4 so it makes little sense to try and code a workaround that will later be deprecated, doesn't it. What's the best approach to take now if I want to use the gtk.CellRendererCombo in my TreeView?

Maybe I just don't understnad the versioning because it seems unlikely that Ubuntu wouldn't have access to recent versions of GTK. Anyone expert in this can shed some light?

Thanks!

---

### Post by Flimm on 2009-10-16
Hi BkkBonzana.

First off, version numbers are ordered differently from decimal numbers. So pygtk 2.14 is actually a later release than pygtk 2.6, because 14 > 6. Use dpkg --compare-versions if you're ever not sure.

Does running the following code in Python give you any errors?[php]import gtk
crc = gtk.CellRendererCombo()[/php]

---

### Post by steeleyuk on 2009-10-16
2.14 is greater than 2.6. You need to look at the number as 2.06.

---

### Post by BkkBonanza on 2009-10-16
Ah, of course. Now I see it. I was thinking like 2.1.4 I guess.
I don't get an error when I create an gtk.CellRendererCombo() instance.
I guess I'll have to look into it deeper as I get no error but it doesn't behave as I would expect. That is I thought I was using it correctly but I do not get any Combo rendered in the TreeView. So then I started thinking maybe it's not in my version. Obviously I see it must be there otherwise I'd get an unrecognized object type error.
Hmmm. Well, must be something wrong with my code. Not the first time, ha ha.
Thanks for the replies. At least I know I need to look at something else now.

Maybe I'll post a code snippet here shortly for suggestions.

---

