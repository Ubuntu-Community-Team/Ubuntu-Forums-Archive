---
title: "[SOLVED] My Python/glade GUI isn't working"
date: 2008-01-11
forum: Programming Talk
---

### Post by NovaAesa on 2008-01-11
I've been learning Python, and decided that it's time I start messing around with GUIs. I've been following the instructions in a text book I have on Python, but they don't seen to be working. Here's the file I'm trying to run:
[PHP]
import gtk.glade

class SingleGUI(object):
    def __init__(self):
        self.window = gtk.glade.XML("OneButtonGUI.glade", "window1")
        
if __name__ == '__main__':
    SingleGUI()
    gtk.main()[/PHP]

And OneButtonGUI.glade is attached. You will have to change the file extension to .glade because the forum wouldn't let me upload a .glade file.

When I run the programme, nothing happens at all. So does anyone know what I am doing wrong?

---

### Post by af20001 on 2008-01-11
Do you need to import pygtk?

---

### Post by NovaAesa on 2008-01-11
I tried this, but it still didn't work. Thx for your reply though.
[PHP]
import pygtk
import gtk.glade

class SingleGUI(object):
    def __init__(self):
        self.window = gtk.glade.XML("OneButtonGUI.glade", "window1")
        
if __name__ == '__main__':
    SingleGUI()
    gtk.main()[/PHP]

---

### Post by bobbocanfly on 2008-01-11
> **NovaAesa said:**
> [PHP]
       
if __name__ == '__main__':
    SingleGUI()
    gtk.main()[/PHP]

I think that is what is causing your problems as to me it doesnt look like the class is being called properly. I dont know much (read anything) about pyGTK but you could give this a try:

[PHP]if __name__ == '__main__':
    gui = SingleGUI()
    gtk.main()[/PHP[/PHP]

---

### Post by NovaAesa on 2008-01-11
Nope, that didn't work either.

---

### Post by af20001 on 2008-01-11
Do you get any errors written to the terminal?

---

### Post by NovaAesa on 2008-01-11
No errors, it just goes to the next line, which is completely blank. I then have to press ctrl-c to stop the programme.

---

### Post by Wybiral on 2008-01-11
Try adding "window.show_all()" at the end of your "__init__" method.

---

### Post by NovaAesa on 2008-01-11
If I add window.show_all() I get a NameError: global name 'window' is not defined
and if I add self.window.show_all() I get an AttributeError: 'glade.XML' object has no attribute 'show_all'

---

### Post by af20001 on 2008-01-11
Have you got 

#!/usr/bin/env python

at the top of your script?

Other than that the only other suggestion I have is follow the example [here]("http://216.239.59.104/search?q=cache:f0W3V10eoN0J:www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/+pygtk+glade+example&hl=en&ct=clnk&cd=1&gl=uk&client=firefox-a").

---

### Post by Wybiral on 2008-01-11
> **NovaAesa said:**
> If I add window.show_all() I get a NameError: global name 'window' is not defined
and if I add self.window.show_all() I get an AttributeError: 'glade.XML' object has no attribute 'show_all'

Hmm, I've never used pythons glade module, I'm used to manually constructing them (where the "window" label would have been the actual "window" widget). Maybe glade stores the window widget somewhere that needs made visible?

---

### Post by NovaAesa on 2008-01-11
Okay, I know what's gone wrong. In glade, I didn't set visible to Yes under Common for window1. I saw info about that in the guide that was linked to a few posts back.

Thanks everyone for your help and patients!

---

