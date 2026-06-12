---
title: "gtk/pygtk - menu popup not from button click"
date: 2010-12-14
forum: Programming Talk
---

### Post by giuspen on 2010-12-14
I'm trying to have a menu popup not from a button click but from a key press.
I call the same code that I use when clicking button number three but the menu does not appear.
I tried creating a button click event myself and emit it but still no popup menu visible.
Anybody can help?
Thanks.

---

### Post by SledgeHammer_999 on 2010-12-14
Show us some code. If you don't want to expose all your code publicly at least show us these things:
1.how you connect to the key press event
2.the function that is called as callback/signal handler.

---

### Post by giuspen on 2010-12-14
> **SledgeHammer_999 said:**
> Show us some code. If you don't want to expose all your code publicly at least show us these things:
1.how you connect to the key press event
2.the function that is called as callback/signal handler.

the code is GPL, can be fully browsed here: [http://code.google.com/p/giuspen-cherrytree/source/checkout](http://code.google.com/p/giuspen-cherrytree/source/checkout)

the involved functions are the following:

1) the button-press-event callback which pops up the menu properly at right click:
[PHP]   def on_mouse_button_clicked_tree(self, widget, event):
      """Catches mouse buttons clicks"""
      if event.button == 3:
         self.ui.get_widget("/TreeMenu").popup(None, None, None, event.button, event.time)
      elif event.button == 1 and event.type == gtk.gdk._2BUTTON_PRESS:
         self.node_modify()[/PHP]
2) the key_press_event callback which doesn't popup at "Menu" key presses:
[PHP]   def on_key_press_cherrytree(self, widget, event):
      """Catches ChooseNode Dialog key presses"""
      keyname = gtk.gdk.keyval_name(event.keyval)
      if keyname == "Return": self.node_modify()
      elif keyname == "Menu": self.ui.get_widget("/TreeMenu").popup(None, None, None, 0, event.time)[/PHP]

UPDATE: I can see some blinkings if I keep pressing the key as if the menu appears but disappears immediatly

Thanks.

---

### Post by giuspen on 2010-12-14
I got it working!
The problem is that I had to stop the signal because it caused the menu to disappear.

[PHP]   def on_key_press_cherrytree(self, widget, event):
      """Catches ChooseNode Dialog key presses"""
      keyname = gtk.gdk.keyval_name(event.keyval)
      if keyname == "Return": self.node_modify()
      elif keyname == "Menu":
         self.ui.get_widget("/TreeMenu").popup(None, None, None, 0, event.time)
         widget.stop_emission("key_press_event")[/PHP]

---

