---
title: "quit python gtk from physical Switch."
date: 2015-09-01
forum: Programming Talk
---

### Post by ace11 on 2015-09-01
Hello. Im running a gtk webbrowser using pythonGTK.
I have a code which loads everything up then runs gtk.main(), I want an if statement after that to check True or False and if true to run gtk.main_quit(). However when i put this in it doesn't run.

Can anyone help explain why it  wont run

```

  GNU nano 2.2.6                                       File: display2.py


import gtk, webkit
import sys
import time
import serial
import pyimport




rencoder = pyimport.main()


win = gtk.Window()
win.set_size_request(800, 480)
win.connect('destroy', lambda w: gtk.main.quit())


box1 = gtk.VBox()
win.add(box1)
box2 = gtk.HBox()
web = webkit.WebView()
box1.pack_start(web)
win.show_all()
web.open('http://0.0.0.0:3333')
gtk.main()


if pyimport.pressed == True:
        gtk.main_quit()

``` 


do i have to put these into functions at all ? or can it run like this.

---

