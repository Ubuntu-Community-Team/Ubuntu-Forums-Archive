---
title: "How to display string from socket in a textview (gtkpy/quickly)?"
date: 2012-06-12
forum: Programming Talk
---

### Post by UbuKunubi on 2012-06-12
Hello,

I have a working program in python that reads strings from a socket.
Having now worked through the tutorial that comes with ```
quickly tutorial
```, I am trying to find how to get the strings from the socket into a textview.

The pure python code that works is:

```

import os
import socket
import select
import struct

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.connect(("gmail.com",80))
print "This Computers IP Address is "+(s.getsockname()[0])
s.close()


server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(("", 8888))
server_socket.listen(5)
print "TCPServer Waiting for client on port 8888"
while 1:
    client_socket, address = server_socket.accept()
    print "Addr=", address
    data = client_socket.recv(512)
    print "RECIEVED:" , data

```

Can anyone help?

All the best,
Ubu

---

### Post by UbuKunubi on 2012-06-13
With pointers from kkantnaik, I've written the following code.
While it runs without error, the data from the socket is not displaying in the text view :(

```

# -*- Mode: Python; coding: utf-8; indent-tabs-mode: nil; tab-width: 4 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

import gettext
from gettext import gettext as _
gettext.textdomain('jotty')
import os
import socket
import gobject
from gi.repository import GLib # pylint: disable=E0611
from gi.repository import Gtk # pylint: disable=E0611
import logging
logger = logging.getLogger('jotty')
from jotty.SaveDialog import SaveDialog
from jotty.OpenDialog import OpenDialog
from jotty_lib import Window
from jotty.AboutJottyDialog import AboutJottyDialog
from jotty.PreferencesJottyDialog import PreferencesJottyDialog


# See jotty_lib.Window.py for more details about how this class works

class JottyWindow(Window):
    __gtype_name__ = "JottyWindow"
    
    def get_data():
        """ set up the socket for reading"""
        server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        server_socket.bind(("", 8888))
        server_socket.listen(5)
        return server_socket

    def handle_data(source, condition):
        """get the data from the server socket"""
        data = source.recv(512)
        if len(data) > 0:
			return True #run forever
		else:
			print 'closed'
			print 'so get new data...'
			#sock = get_file()
			gobject.io_add_watch(server_socket, gobject.IO_IN, handle_data)
            buff = self.ui.textview1.get_buffer()
            buff.set_text(data)
			return False # stop looping

    def finish_initializing(self, builder): # pylint: disable=E1002
        """Set up the main window"""
        super(JottyWindow, self).finish_initializing(builder)

        self.AboutDialog = AboutJottyDialog
        self.PreferencesDialog = PreferencesJottyDialog

    def on_button1_clicked(self, widget, data=None):
        print "---------------------------->Button1 was Clicked"
        buff = self.ui.textview1.get_buffer()
        buff.set_text("The button was Clicked :) ")

    def on_mnu_save_activate(self, widget, data=None):
        print "save"
        saver = SaveDialog()
        result = saver.run()
        title = saver.title_text
        saver.destroy()
        if result != Gtk.ResponseType.OK:
            return
        #get the string
        buff = self.ui.textview1.get_buffer()
        start_iter = buff.get_start_iter()
        end_iter = buff.get_end_iter()
        text = buff.get_text(start_iter, end_iter, True)

        #create the filename
        data_dir = GLib.get_user_data_dir()
        jotty_dir = os.path.join(data_dir, "jotty")
        filename = os.path.join(jotty_dir, title)

        #write the data
        GLib.mkdir_with_parents(jotty_dir, 0o700)
        GLib.file_set_contents(filename, text)

    def on_mnu_open_activate(self, widget, data=None):
        print
        print "----->     Open clicked from the menu :)"
        print
        #get the name of the document to open
        opener = OpenDialog()
        result = opener.run()
        filename = opener.selected_file
        #close the dialog, and check whether to proceed
        opener.destroy()
        if result != Gtk.ResponseType.OK:
            return
        #try to get the data from the file if it exists
        try:
            success, text = GLib.file_get_contents(filename)
        except Exception:
            text = ""
        #set the UI to display the string
        buff = self.ui.textview1.get_buffer()
        buff.set_text(text)
        print "-------------------> text from file variable is :"+text

    def on_mnu_new_activate(self, widget, data=None):
        print "file -> New has been clicked on"
        self.ui.entry1.set_text("Note Title")
        buff = self.ui.textview1.get_buffer()
        buff.set_text("")

    server_socket = get_data()
    gobject.io_add_watch(server_socket, gobject.IO_IN, handle_data)

```

Im more used to writing straight-line code, so changing to GTK is a bit of leap.

Any comments, suggestions, etc., are welcome.
Regards,
UbuKunubi.

---

### Post by MG&amp;TL on 2012-06-14
Are you actually calling the Gtk mainloop at any point in that code? I'm not familiar with quickly, but you probably should.

[http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html#sec-HelloWorld](http://www.pygtk.org/pygtk2tutorial/ch-GettingStarted.html#sec-HelloWorld)

---

### Post by UbuKunubi on 2012-06-14
In the __init__.py file I have the following, and after considering your question I can see that ```
 Gtk.main() 
``` is never called because ```
 while 1:
``` never exits.

__init__.py
```

# -*- Mode: Python; coding: utf-8; indent-tabs-mode: nil; tab-width: 4 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

import optparse
import socket
from gi.repository import GObject
import gettext
from gettext import gettext as _
gettext.textdomain('jotty')

from gi.repository import Gtk # pylint: disable=E0611

from jotty import JottyWindow

from jotty_lib import set_up_logging, get_version
def get_data():
    """ set up the socket for reading"""
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind(("", 8888))
    server_socket.listen(5)
    return server_socket

def handle_data(source, condition):
    """get the data from the server socket"""
    data = source.recv(512)
    if len(data) > 0:
        print "############   Data :",data
        #sock = get_file()
		gobject.io_add_watch(server_socket, gobject.IO_IN, handle_data)
        buff = window.ui.textview1.get_buffer()
        buff.set_text(data)

def parse_options():
    """Support for command line options"""
    parser = optparse.OptionParser(version="%%prog %s" % get_version())
    parser.add_option(
        "-v", "--verbose", action="count", dest="verbose",
        help=_("Show debug messages (-vv debugs jotty_lib also)"))
    (options, args) = parser.parse_args()

    set_up_logging(options)

def main():
    'constructor for your class instances'
    parse_options()

    # Run the application.    
    window = JottyWindow.JottyWindow()
    print "window assigned to Jotty Window <---------------------------------!"
    #server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    #server_socket.bind(("", 8888))
    #server_socket.listen(5)
    print "Socket is now bound to port 8888 <--------------------------------!"
    window.show()
    buff = window.ui.textview1.get_buffer()
    buff.set_text("READY")
    server_socket = get_data()
    GObject.io_add_watch(server_socket, GObject.IO_IN, handle_data)

    while 1:
        client_socket, address = server_socket.accept()
        print "Addr=", address
        data = client_socket.recv(512)
        print "RECIEVED:" , data
    Gtk.main()

```

I am unsure how to execute the code within the while 1: block, I have asked around and have been presented with the following options:
 A) write the while out into a class and have the class return the data string.
 B) Create a separate thread and pass the data from there.
 C) Leave the while thread in a simple pure python program and run it inside a popen command, reading the terminal (stdin), and update the textview from there.
 D) Whatever else I have not looked at.

However my main obstacle is my lack of understanding on how to trigger an update from an event which is NOT a UI action.

So if anyone can provide me with pointers its hughly appreciated.


Thanks for your time,
Ubu

---

### Post by MG&amp;TL on 2012-06-14
There's a couple of solutions here, as Gtk.main *needs* to be called so the interface doesn't lock up.

Either:

-use threading. This isn't easy, as Gtk needs special treatment for threading. If you choose this route, I can offer you some limited help, but you're best off reading online.

-use this (hack) I discovered while solving a similiar problem:

In you main loop (while 1), add this:

```
while Gtk.events_pending():
  Gtk.main_iteration()
```

...this manually calls Gtk's loop.

---

### Post by UbuKunubi on 2012-06-14
Thanks for your reply :)

I want to do this properly, ideally the completed project will be available for free in the Ubuntu Software Center,so I'd like to learn more about threading please!

---

### Post by MG&amp;TL on 2012-06-14
I tell a lie, you can also use idle_add to update the GUI when the processor has time, which these days, is continuously.

[http://ubuntuforums.org/showthread.php?t=1933882]("http://ubuntuforums.org/showthread.php?t=1933882")

...looks pretty good to me.

Essentially, the GUI's in the main thread, and that spawns worker threads where required. 

Hints:
-Don't try and put the GUI in other threads, it's not a good idea. -Also, don't try and access the GUI from other threads either.

---

