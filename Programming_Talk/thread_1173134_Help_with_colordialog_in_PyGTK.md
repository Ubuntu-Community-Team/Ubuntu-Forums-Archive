---
title: "Help with colordialog in PyGTK"
date: 2009-05-29
forum: Programming Talk
---

### Post by TheVerySpecialAgent on 2009-05-29
So I don't have any experience with python, or any other programing language for that matter. But somehow I manage to put together this simple script below. What it does is it opens a colordialog and then print out each color value in hexadecimals. Now that works well and all. The problem is with the colordialog. When you press the cancel button it returns the same values as if one had chosen the ok button. How can I make the cancel button _not_ return a value?

```
#!/usr/bin/python

import gtk

class colorpicker(gtk.Window): 
    def __init__(self):

        colordialog = gtk.ColorSelectionDialog("Select color")
        colordialog.run()
        colorsel = colordialog.colorsel
	
        colordialog.destroy()
        color = colorsel.get_current_color()

        red=color.red*255/65535
        green=color.green*255/65535
        blue=color.blue*255/65535
        red="%X" % red
        green="%X" % green
        blue="%X" % blue
        print red, green, blue

	exit()

colorpicker()
gtk.main()
```

---

### Post by steeleyuk on 2009-05-29
You'll probably need to put the code which prints the values into a separate function, which is called when the user presses the OK button.

I'm also presuming you'll want the application to close when the cancel button is pressed, which can also be put into a separate function.

Still learning myself so someone else might have a better or more efficient way of doing it.

---

### Post by crdlb on 2009-05-29
colordialog.run() will return one of gtk.RESPONSE_CANCEL (cancel button), gtk.RESPONSE_OK (ok button), or gtk.RESPONSE_DELETE_EVENT (X in titlebar). Therefore you should write: ```

if colordialog.run() == gtk.RESPONSE_OK:
    do stuff

colordialog.destroy()
```

---

### Post by TheVerySpecialAgent on 2009-05-29
> **crdlb said:**
> colordialog.run() will return one of gtk.RESPONSE_CANCEL (cancel button), gtk.RESPONSE_OK (ok button), or gtk.RESPONSE_DELETE_EVENT (X in titlebar). Therefore you should write: ```

if colordialog.run() == gtk.RESPONSE_OK:
    do stuff

colordialog.destroy()
```

Tanks, this worked really good! Exactly what I was looking for.

---

