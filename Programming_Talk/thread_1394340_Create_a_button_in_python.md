---
title: "Create a button in python"
date: 2010-01-30
forum: Programming Talk
---

### Post by ubudog on 2010-01-30
Hello, I am very new to python, just started yesterday, and have managed to get a window up.  I want to make a button inside the window. I have tried ```
button = gtk.Button()
``` and it still doesn't work. Is there anything else I need to do?  This is my current code:```
#!/usr/bin/python
import gtk
import pygtk
window = gtk.Window()
window.set_title("My Program")
button = gtk.Button()
window.show_all()
gtk.main()
```

Thanks for any help

---

### Post by steeleyuk on 2010-01-30
```
#!/usr/bin/python
import gtk
import pygtk

window = gtk.Window()
window.set_title("My Program")
button = gtk.Button("Button text here")
window.add(button)
window.show_all()

gtk.main()
```

I've added some text to the button as well, otherwise it will show up as a tiny square in a tiny window. All you had missing was window.add(button). :)

---

### Post by ubudog on 2010-01-30
Thanks for helping a noob!! :p:p:p

---

