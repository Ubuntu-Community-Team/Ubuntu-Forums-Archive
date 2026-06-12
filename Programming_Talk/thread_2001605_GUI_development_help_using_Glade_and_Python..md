---
title: "GUI development help using Glade and Python."
date: 2012-06-11
forum: Programming Talk
---

### Post by kkantnaik on 2012-06-11
I am developing a GUI for a client server program. The client connects to the server and the server sends some strings to the server. Now I want to print those messages at screen. How can this be achieved using Glade???

](*,)

---

### Post by kkantnaik on 2012-06-11
By messages I mean the strings the server sends to the client. ](*,)

---

### Post by MG&amp;TL on 2012-06-11
Well, I suggest making a window and a Textview, or possibly a Label, then just using python's socket library to receive strings from the server. When that happens, updatee the widget.

Which particular part are you struggling with?

---

### Post by kkantnaik on 2012-06-12
First of all, thanks for replying . I know that I have to use TextView but not sure about how to handle signals, and how to get the messages. 

For instance, suppose I have a string then how do I put that on the text view. I learnt after a bit of googling that buffer is used to store the text. So is it possible to get the strings and copy them by some way into the buffer and then print it on text view??

Sorry if I'm being silly but I'm really new to GUI programming. ;)

---

### Post by kkantnaik on 2012-06-12
Finally I figured it out. I just had to get the strings and put them into text view using set_text() method.

:guitar:

This post helped [http://ubuntuforums.org/showthread.php?t=426671](http://ubuntuforums.org/showthread.php?t=426671)

---

### Post by UbuKunubi on 2012-06-12
Could you please be so kind as to post the code that is working for you, as I am stuck with getting strings from a socket to display into a textview.

---

### Post by kkantnaik on 2012-06-13
The Client side code is like this:
```
from gi.repository import Gtk
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
srv_address = "127.0.0.1"
PORT = 7234            

class Handler:

    def onDeleteWindow(self, *args):

        Gtk.main_quit(*args)

    def onSendButtonClicked(self, button):
        global srv_address
        global PORT

        MSG = builder.get_object("entry1").get_text()

        s.sendto (MSG, (srv_address, PORT))

    def onConnectButtonClicked(self, button):
        global srv_address
        global PORT

        srv_address = builder.get_object("entry2").get_text()

        srv_port = builder.get_object("entry3").get_text()

        PORT = int(srv_port)

        s.connect ((srv_address, PORT))

    def onReceiveButtonClicked(self, button):

        data = s.recvfrom (65535)
        builder.get_object("textview1").get_buffer().set_text(repr(data))


builder = Gtk.Builder()

builder.add_from_file("client.glade")

builder.connect_signals(Handler())

window = builder.get_object("window1")

window.show_all()

Gtk.main()


```I have used a onReceiveButtonClicked as a handler. When the receive button is clicked this code is executed

```

def onReceiveButtonClicked(self, button):
        data = s.recvfrom (65535)
        builder.get_object("textview1").get_buffer().set_text(repr(data))

```Hope this helps ;)

---

### Post by UbuKunubi on 2012-06-13
Thank you, I highly appreciated that :)

Kind regards,
Ubu

---

