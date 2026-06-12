---
title: "Python Socket Listener and the Main Loop"
date: 2009-06-18
forum: Programming Talk
---

### Post by stefanadelbert on 2009-06-18
I'm creating a simple socket listening app in Python using a Glade3 GUI. As a starting point, all I want to do is pickup messages that arrive at the socket and display them using a GtkTreeView(GtkListStore) or something similar.

I got the socket side of things working in a few minutes thanks to this tutorial: [http://www.evolt.org/node/60276]("http://www.evolt.org/node/60276").

The server code that processes the messages runs this infinite loop:
```
while 1:
	data,addr = UDPSock.recvfrom(buf)
	if not data:
		print "Client has exited!"
		break
	else:
		print "\nReceived message '", data,"'"
```
The way Python/Glade GUI apps seem to work (based on the tutorials I've been using) is that they initialise the GUI (which is wrapped in a Python class) and then control is passed to the Python main loop. The main loop then responds to events from the GUI (or elsewhere) and passes control to the relevant event handlers, if they exist.

So I suppose that I should get the socket listener loop raising events that the main loop can then handle, but I don't know the right approach to working the listener loop into the Python GUI app. As I see it, the two loops need to be running at the same time (main loop and listener loop, two threads) or is there a better approach? Can I work the socket listener loop code into the main loop somehow?

Stef

Ps. I did try creating a login at the Dev Shed Forums ([http://forums.devshed.com/](http://forums.devshed.com/)), but their registration page is not working (verification image not being displayed). Ubuntuforums was my next best bet...

---

### Post by monraaf on 2009-06-18
Maybe pass the file descriptor of the socket to gobject.io_add_watch?

[http://www.pygtk.org/docs/pygobject/gobject-functions.html#function-gobject--io-add-watch](http://www.pygtk.org/docs/pygobject/gobject-functions.html#function-gobject--io-add-watch)

---

### Post by stefanadelbert on 2009-06-18
Seems that a Python file object can be retrieved from a Python socket using,
> socket.makefile([mode[, bufsize]])

    Return a file object associated with the socket. (File objects are described in File Objects.) The file object references a dupped version of the socket file descriptor, so the file object and socket object may be closed or garbage-collected independently. The socket must be in blocking mode (it can not have a timeout). The optional mode and bufsize arguments are interpreted the same way as by the built-in file() function.
[RIGHT]*Source [http://docs.python.org/library/socket.html]("http://docs.python.org/library/socket.html")*[/RIGHT]

So it does look like the pseudo code below
```
gobject.io_add_watch(socket.makefile(), gobject.IO_IN, on_message_received)
```
could be used to raise an event when a socket listener receives a message. Assume the main loop would then pass on control to the specified event handler.

I'll give it a go when I get home and get back with the results.

Stef

---

### Post by stefanadelbert on 2009-06-19
I've tried the suggestion of using io_add_watch on the client side to listen for messages coming in from the server and I reckon I'm most of the way there, but now I'm stuck.

Here is my code so far:
```
class MessageListener:
 
    def on_window_destroy(self, widget, data=None):
        print "Exiting..."
        gtk.main_quit()

    def on_message_received(self, source, cb_condition):
        print "Got Message"
    
    def __init__(self):
    
        builder = gtk.Builder()
        builder.add_from_file("client.glade") 
        
        self.window = builder.get_object("window")
        self.treeview = builder.get_object("treeview")
        builder.connect_signals(self)

        self.liststore1 = gtk.ListStore(str, str, str)
        self.treeview.set_model(self.liststore1)

        cell = gtk.CellRendererText()        
        col = gtk.TreeViewColumn("Time", cell, text=0)
        self.treeview.append_column(col)
        cell = gtk.CellRendererText()        
        col = gtk.TreeViewColumn("Severity", cell, text=1)
        self.treeview.append_column(col)
        cell = gtk.CellRendererText()        
        col = gtk.TreeViewColumn("Message", cell, text=2)
        self.treeview.append_column(col)

if __name__ == "__main__":

    # Set the socket parameters
    host = "localhost"
    port = 21567
    buf = 1024
    addr = (host,port)

    # Create socket and bind to address
    TCPSock = socket(AF_INET,SOCK_DGRAM)
    TCPSock.bind(addr)

    listener = MessageListener()

    # Watch the socket for a message and call on_message_received when one comes in
    gobject.io_add_watch(TCPSock.makefile('r'), gobject.IO_IN, MessageListener.on_message_received, listener)

    listener.window.show()

    gtk.main()
```

The idea is that the MessageListener.on_message_received should be called when a message comes in on the listening socket. But when I try to send a message to the socket from the server, I get the following error message at the client:
> TypeError: unbound method on_message_received() must be called with MessageListener instance as first argument (got _fileobject instance instead)

I think I've got the signature of the callback function wrong, but don't know how to fix it. I've tried lots of different combinations, but I'm still new to Python and pyGtk, so I don't have the gut feel yet.

Any ideas?

Stef

---

### Post by smartbei on 2009-06-19
Change:
```

gobject.io_add_watch(TCPSock.makefile('r'), gobject.IO_IN, MessageListener.on_message_received, listener)

```
to:
```

 gobject.io_add_watch(TCPSock.makefile('r'), gobject.IO_IN, listener.on_message_received, listener)

```
The problem is that if you are calling the method from the class and not from the instance, then it is not bonded to an instance, and one must be passed (the self argument is not automatically supplied).

---

### Post by stefanadelbert on 2009-06-19
Hey smartbei, works like a charm. Thanks. It makes sense to call the callback function on an instance.

There was an error because the callback wasn't return True or False, so I've modified the callback to:

```
    def on_message_received(self, source, cb_condition):
        print "Got Message"
        self.liststore1.append(["one", "two", "three"])
        return False
```

Problem with return False is that the IO watch get cancelled and would need to be re-instated each time a message is received. If I return True however, then the callback gets called repeatedly ad infinitum. Maybe this is because there is a buffer that needs to be flushed after processing the message. Or maybe the watch does just need to be re-instated each time, but that would seem clumsy.

I'll keep hacking away...

Stef

---

