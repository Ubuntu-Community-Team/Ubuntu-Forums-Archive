---
title: "using python to locate gnome resources"
date: 2010-01-23
forum: Programming Talk
---

### Post by OgreProgrammer on 2010-01-23
How can I have my python program ask the system what the desktop background image is/or where it is?

---

### Post by denarced on 2010-01-23
You could try and parse $HOME/.gnome2/backgrounds.xml
It would appear to contain a list of background-images

---

### Post by denarced on 2010-01-23
or you could use gnome's own tool to find out
gconftool-2 --get /desktop/gnome/background/picture_filename

---

### Post by unutbu on 2010-01-23
This code comes from Davyd Madeley's [change-background.py]("http://oracle.bridgewayconsulting.com.au/~danni/misc/change-background-py.html") script:

```
import gconf
class GConfClient:
    def __init__ (self):
        self.__client__ = gconf.client_get_default ()
    def get_background (self):
        return self.__client__.get_string("/desktop/gnome/background/picture_filename")
    def set_background (self, background):
        self.__client__.set_string (
            "/desktop/gnome/background/picture_filename", background)

client = GConfClient ()
print(client.get_background())

```

---

### Post by OgreProgrammer on 2010-01-24
Thanks unutbu and denarced. That was exactly what i needed.

Is there also some way for a window to know where it has been placed at after the mouse moves it?

---

### Post by Kegusa on 2010-01-25
Using gnome (gtk) you can determine the position of the window with gtk.Window.get_position(). 

Take a look at [www.pygtk.org](www.pygtk.org) for the python docs on gtk, but be warned there is a brickload of docs to dive into! 

Not sure if there are other methods to find this out, if there are I'm interested aswell.

---

