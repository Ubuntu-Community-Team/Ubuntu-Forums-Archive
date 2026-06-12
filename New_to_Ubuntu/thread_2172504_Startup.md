---
title: "Startup"
date: 2013-09-05
forum: New to Ubuntu
---

### Post by narendra4 on 2013-09-05
How can I post a welcome message on system startup
like
"Have a Great Day!!"
/etc/motd ??
but what to do in that?

---

### Post by blackbird34 on 2013-09-05
/etc/motd is for console (tty) sessions. If that is what you want, this tutorial might come in useful: [http://www.mewbies.com/how_to_customize_your_console_login_message_tutorial.htm](http://www.mewbies.com/how_to_customize_your_console_login_message_tutorial.htm)

And this: [http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/](http://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/)

A little ```
man motd
``` might also help. 

(quite interesting discoveries btw :D )

However if you want something in the graphical environment I can't help much.

EDIT: someone else can.[[SIZE=2]Tip - MOTD the GUI way [/SIZE][SIZE=2](2009 - Ubuntuforums)[/SIZE]]("http://ubuntuforums.org/showthread.php?t=1367398")
I can't help with it though, and it's pretty old, even if it's written in Python...

---

### Post by Jonathan Precise on 2013-09-05
> **narendra4 said:**
> How can I post a welcome message on system startup
like
"Have a Great Day!!"
/etc/motd ??
but what to do in that?

Make a text file and save it to your home folder as "have-a-nice-day.py".

Put this in your text file:
```
#!/usr/bin/python

import pygtk
pygtk.require('2.0')
import gtk


print "Loading..."
print "Loading...</  >"
print "Loading...<-  >"
print "Loading...<|  >"
print "Loading...</  >"
print "Loading...<-/ >"
print "Loading...<-- >"
print "Loading...<-| >"
print "Loading...<--/>"
print "Loading...<--->"
print "Loading...<--|>"
print "Loading...<--/>"
print "Loading...<--->"
		
class HelloWorld:
    def __init__(self):
		
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_border_width(10)
    
        self.window.connect("delete_event", self.delete_event)
        self.window.connect("destroy", self.destroy)
    
        self.button = gtk.Button("Have a nice day!!! (Click here to dismiss)")
        self.button.connect("clicked", self.hello)
        self.button.connect_object("clicked", gtk.Widget.destroy, self.window)
    
        self.window.add(self.button)
        self.window.show_all()


    def hello(self, widget):
        print "Dismissing (due to pressing the button)..."


    def delete_event(self, widget, event, data=None):
        print "Delete event occurred (maybe you pressed the X button?)... Now exiting window..."


        return False


    def destroy(self, widget, data=None):
        print "Destroy signal occurred... Exiting PyGtk script..."
        gtk.main_quit()


    def main(self):
        gtk.main()


if __name__ == "__main__":
    hello = HelloWorld()
    hello.main()
```

Now open a terminal and type:
```
gnome-session-properties
```

Add a new application:

> Name: Whatever you want.
Command: ```
python ~/have-a-nice-day.py
```
Description: Whatever you want.

Logout/Login-again. You should get a dialog with a welcome message.

---

### Post by JKyleOKC on 2013-09-05
Excellent little script! I've been looking for a way to do a few things that Zenity doesn't handle well; can you tell me where to find the docs for writing this?

---

### Post by Jonathan Precise on 2013-09-05
> **JKyleOKC said:**
> Excellent little script! I've been looking for a way to do a few things that Zenity doesn't handle well; can you tell me where to find the docs for writing this?

Please download Ubuntu-tweak from the tualatrix ppa. In the Admins tab, click on Templates. Enable the PyGtk example. Then navigate to your home folder, right-click the white background, select "Create New" -> "PyGTK example". Rename and adjust to your liking!

---

