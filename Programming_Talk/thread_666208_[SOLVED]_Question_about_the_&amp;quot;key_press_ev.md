---
title: "[SOLVED] Question about the &amp;quot;key_press_event&amp;quot; in pyGTK"
date: 2008-01-13
forum: Programming Talk
---

### Post by NovaAesa on 2008-01-13
What I'm trying to do it catch the key_press_event and then do something based on what key was pressed. I am able to catch the event using the following code, but I can't work out how to tell which key was pressed.

[PHP]import gtk
import pygtk

class MyGUI(object):
    
    def __init__(self):
        window = gtk.Window()
        window.connect("key_press_event", self.key_press_event)
        window.show()

    def main(self):
        gtk.main()
        
    def key_press_event(self, widget, event):
        print 'a key was pressed'
        
if __name__ == "__main__":
    gui = MyGUI()
    gui.main()[/PHP]

What I'm trying to do, is execute a different piece of code depending on which key was pressed. Anyone know how to do this?

---

### Post by NovaAesa on 2008-01-13
Hey don't worry about it guys/gals, I worked it out :)

[PHP]import gtk
import pygtk

class MyGUI(object):
    
    def __init__(self):
        window = gtk.Window()
        window.connect("key_press_event", self.key_press_event)
        window.show()

    def main(self):
        gtk.main()
        
    def key_press_event(self, widget, event):
        if event.keyval == 65362:
            do_this()
        if event.keyval == 65363:
            do_that()
        
if __name__ == "__main__":
    gui = MyGUI()
    gui.main()  [/PHP]

---

### Post by llonesmiz on 2008-01-13
In order to maintain readability I would change:

```
[COLOR=#000000][COLOR=#0000bb]def key_press_event[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]self[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]widget[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]event[/COLOR][COLOR=#007700]): 
        if [/COLOR][COLOR=#0000bb]event[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]keyval [/COLOR][COLOR=#007700]== [/COLOR][COLOR=#0000bb]65362[/COLOR][COLOR=#007700]: 
            [/COLOR][COLOR=#0000bb]do_this[/COLOR][COLOR=#007700]() 
        if [/COLOR][COLOR=#0000bb]event[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]keyval [/COLOR][COLOR=#007700]== [/COLOR][COLOR=#0000bb]65363[/COLOR][COLOR=#007700]: 
            [/COLOR][COLOR=#0000bb]do_that[/COLOR][COLOR=#007700]() [/COLOR][/COLOR]
```to:
```
[COLOR=#000000][COLOR=#0000bb]def key_press_event[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]self[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]widget[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]event[/COLOR][COLOR=#007700]): [/COLOR][/COLOR]
[COLOR=#000000][COLOR=#007700]        if [/COLOR][COLOR=#0000bb]event[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]keyval [/COLOR][COLOR=#007700]== [/COLOR][COLOR=#0000bb]gtk.keysyms.Up[/COLOR][COLOR=#007700]: 
            [/COLOR][COLOR=#0000bb]do_this[/COLOR][COLOR=#007700]() 
        if [/COLOR][COLOR=#0000bb]event[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]keyval [/COLOR][COLOR=#007700]== [COLOR=Navy]gtk.keysyms.Right[/COLOR][/COLOR][COLOR=#007700]: 
            [/COLOR][COLOR=#0000bb]do_that[/COLOR][COLOR=#007700]() [/COLOR][/COLOR]
```You can find the complete list of keyvals [here]("file:///usr/share/python-support/python-gtk2/gtk-2.0/gtk/keysyms.py"). 

Edit: If the link doesn't work just open the file /usr/share/python-support/python-gtk2/gtk-2.0/gtk/keysyms.py .
Edit2: Indentation fixed.

---

### Post by Majorix on 2008-01-13
Your code won't work because of the indentation rules. Look at the if's ;)

---

### Post by NovaAesa on 2008-01-13
> **llonesmiz said:**
> In order to maintain readability I would change

Hey thanks! That's even better :)

---

