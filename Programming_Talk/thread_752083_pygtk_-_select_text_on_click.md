---
title: "pygtk - select text on click"
date: 2008-04-11
forum: Programming Talk
---

### Post by mailbinoy on 2008-04-11
Hi,

I am using pygtk and glade to design an app for personal use. 
I have a textbox(GTKEntry) . 
I want the text in the textbox selected when I single click in the textbox. I have been googling for this for some time, not sure why selecting text in a textbox is this difficult

Can somebody please help

---

### Post by nanotube on 2008-04-11
check the pygtk manual for gtk.Entry:
[http://www.pygtk.org/docs/pygtk/class-gtkentry.html](http://www.pygtk.org/docs/pygtk/class-gtkentry.html)

it is derived from gtk.Widget, which has a signal "focus", and a signal "focus-in-event".

it is also derived from gtk.Editable, which has a method "select_region" ([http://www.pygtk.org/docs/pygtk/class-gtkeditable.html](http://www.pygtk.org/docs/pygtk/class-gtkeditable.html))

now, i have never actually coded anything in gtk or pygtk, i was just curious, so i looked this up. 

so won't give you any actual code examples, but i suspect that that it's something along the lines of 
mytextbox.focus = mytextbox.select_region(0,-1)

(look up what the actual idiom is for assigning callbacks to signals)

so ... use the docs :)

---

