---
title: "PyGTK Asynchronous I/O?"
date: 2009-05-29
forum: Programming Talk
---

### Post by R0xx1t on 2009-05-29
Hello there!

I am developing a python telnet chat client for use with my python async_chat server. After some searching, I chose PyGTK+ as my GUI Toolkit.  I have my window working and the layout is the way I would like it but I am having problems. The problem is that the text from the server is not showing up until I press my "Send" button multiple times.

I have narrowed the problem down to a matter of the TextView widget (What I am using to display the chat messages) not refreshing data from the TextBuffer until I press the button. As far as I can tell, the gtk.main() loop is waits on the button press during each loop. Waiting for button input blocks the TextView from refreshing and so data written to the TextBuffer from the server does not show.

Somehow I have to get I/O Asynchronous, such that the TextView updates without the gtk.main() hanging up on the button press. I've attached the client's code below.
```

import sys
import pygtk
import gtk
from telnetlib import Telnet
from threading import Thread

window = gtk.Dialog("", None, 0, None)
window.set_default_size(300, 200)

class Reader(Thread):
    def __init__(self, telnet):
        self.buffer = gtk.TextBuffer(table = None)
        
        self.textview = gtk.TextView(self.buffer)
        self.textview.set_editable(False)
        self.textview.set_wrap_mode(True)
        
        self.scrolled_window = gtk.ScrolledWindow(hadjustment = None)
        self.scrolled_window.set_policy(gtk.POLICY_NEVER, gtk.POLICY_ALWAYS)
        self.scrolled_window.add_with_viewport(self.textview)
        
        window.vbox.pack_start(self.scrolled_window, True, True, 0)
        
        self.scrolled_window.show()
        self.textview.show()
        window.show()
        
        self.tel = telnet
        Thread.__init__(self)
        
    def run(self):
        while 1:
            data = self.tel.read_some()
            if not data == '':
                self.buffer.insert_at_cursor(data)

class Client():
    def __init__(self, HOST, PORT, usr):
        self.button = gtk.Button("Send")
        self.button.connect("clicked", self.clear_and_send, None)
        
        self.entry_box = gtk.Entry(max = 0)
        
        window.vbox.pack_end(self.button, False, True, 0)
        window.vbox.pack_end(self.entry_box, False, True, 0)
        
        self.entry_box.show()
        self.button.show()
        window.present()

        self.user_name = usr
        
        self.tel = Telnet()
        self.tel.open(HOST, PORT)
        
    def clear_and_send(self, widget, data = None):
        self.entry = self.entry_box.get_text()
        self.tel.write(self.user_name + ": " + self.entry + "\r\n")
        self.entry_box.set_text("")
        
print "Chat"
server = raw_input("Server: ")
port = int(raw_input("Port: "))
alias = str(raw_input("Alias: "))

runnable = Client(server, port, alias)
reader = Reader(runnable.tel)
reader.start()
gtk.main()
```

Any help would be greatly appreciated!

---

### Post by crdlb on 2009-05-29
There's no reason to use threads here. It should be possible to use ```
gobject.io_add_watch (telnet.fileno(), gobject.IO_IN, self.on_telnet_io)
``` and call telnet.read_very_eager() in the callback. You could also just poll with gobject.timeout_add, but io_add_watch would be better if you can make it work.

---

### Post by R0xx1t on 2009-06-01
What the problem appears to be is that I cannot get the TextView to asynchronously refresh from the buffer. All of the data from the server gets to the buffer but the textbox cannot refresh until the button is pressed.

Is there anyway for the button to wait for input without interrupting the TextView's refreshing? Alternatively, is there any way to force the TextView to refresh?

---

### Post by crdlb on 2009-06-01
Just don't ever block the mainloop and the app will remain responsive. Did you try my suggestion? If it works, it should notify you when there's data on the socket that can be read so that you don't block waiting for it.

---

### Post by imdano on 2009-06-01
You have to do a few things for threading in a gtk app to work correctly.  See here: [http://faq.pygtk.org/index.py?file=faq20.006.htp&req=show](http://faq.pygtk.org/index.py?file=faq20.006.htp&req=show)

Also, you really don't need threads for this.  The telnet lib has a read_eager() method that is non-blocking.  You could use that instead of read_some(), remove the "while 1" from the current run() method, and then call run() using gobject.idle_add(), being sure to always return True so it keeps getting called.  I tried it that way on my machine and it seemed to be working normally.

---

### Post by crdlb on 2009-06-01
> **imdano said:**
> and then call run() using gobject.idle_add(), being sure to always return True so it keeps getting called.

An idle function always returning True would peg the CPU, wouldn't it? The idle function will be called the moment there are no other higher-priority events to process. That's why I suggested using a timeout instead (or only reading when there's data to be read by using io_add_watch)

---

### Post by R0xx1t on 2009-06-01
Thanks guys, works great!


I ended up using idle_add. I want to take a look at io_watch_add some time later but I just need it to work for now :D


Thank you both for your help!!!

---

### Post by imdano on 2009-06-01
> **crdlb said:**
> An idle function always returning True would peg the CPU, wouldn't it? The idle function will be called the moment there are no other higher-priority events to process. That's why I suggested using a timeout instead (or only reading when there's data to be read by using io_add_watch)Could be, I didn't check when I tested it.  It wouldn't be any worse than the "while 1:" one loop he was using.  Like you said,  if it does hog too many cycles it could easily be replaced with gobject.timeout_add().

---

