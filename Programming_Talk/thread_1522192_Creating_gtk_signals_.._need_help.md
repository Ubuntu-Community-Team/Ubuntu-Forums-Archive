---
title: "Creating gtk signals .. need help"
date: 2010-07-01
forum: Programming Talk
---

### Post by xoros on 2010-07-01
How could I monitor and create a g_signal_connect whenever a new window is opened?  Is that possible?
Anyone have an example / sample code containing this... 
thanks in advance

---

### Post by xoros on 2010-07-02
I found below info from another forum:
> 
The notify::visible signal will be emitted whenever the visibility state changes, i.e. the window is shown or hidden. The show signal isn't documented but from the source it appears that it is an action signal; you can call it yourself using

dialog.emit('show')

and the widget will show itself, apparently without triggering the notify::visible signal.

---

### Post by xoros on 2010-07-02
In my program, I'm trying to make a method to monitor when default widgets are shown; when a checkbox is "checked"... so far I have this: 
```
static void toggle_monitor ( GtkWidget *checkbutton,
                             GtkDialog *dialog )
{
    g_signal_connect ( dialog, "show",
	              G_CALLBACK (monitor_defwidget), (checkbutton)->active );
}
```
When compiling I get this... 
```
error: ‘GtkWidget’ has no member named ‘active’
```
Any workaround for this?

---

### Post by nvteighen on 2010-07-02
> **xoros said:**
> bump .. 

how do I declare dialog first like this?  

```
 GtkWidget *dialog.emit 
``` 

i'm getting a compile error saying dialog is undeclared.

Is this C?

If you want to create a dialog, you should do something like this:

```

#include <stdio.h>
#include <gtk/gtk.h>

void button_click(GtkWidget *widget, gpointer parent_window)
{
    /* The signature is the one needed by the "clicked" signal */

    GtkWidget *the_dialog = 
        gtk_dialog_new_with_buttons("Dialog!", parent_window,
                                    GTK_DIALOG_DESTROY_WITH_PARENT,
                                    GTK_STOCK_OK, GTK_RESPONSE_OK, NULL);

    if(gtk_dialog_run(GTK_DIALOG(the_dialog)) == GTK_RESPONSE_OK)
    {
        printf("Ok!");
        gtk_widget_destroy(parent_window);
    }
}

int main(int argc, char **argv)
{
    /* Conforming to ISO C99: No declarations mixed with code! */
    GtkWidget *window = NULL;
    GtkWidget *button = NULL;

    gtk_init(&argc, &argv);

    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    g_signal_connect(G_OBJECT(window), "destroy", G_CALLBACK(gtk_main_quit),
                     NULL);

    button = gtk_button_new_with_label("Press!");
    g_signal_connect(G_OBJECT(button), "clicked", G_CALLBACK(button_click),
                     window);
    gtk_container_add(GTK_CONTAINER(window), button);

    gtk_widget_show_all(window);
    gtk_main();

    return 0;
}

```

It's not the perfect piece of GTK+ code... but it works. Anyone wanting to do some GTK+ development should have DevHelp and the offline GTK+ API docs right next to the code he's working on.

---

### Post by xoros on 2010-07-02
@nvteighen 
I had edited my post.. it explains further what I am trying to do. 
(trying to make a method to monitor when default widgets are DISPLAYED & [monitor only when a checkbox is "checked"])

I'm thinking I need to look into notify::visible instead?

---

### Post by nvteighen on 2010-07-02
I have the feeling that you don't fully understand how GTK+ works. First, you usually can't access a widget's internals because GTK+ heavily relies on the "opaque pointer technique" in order to get some encapsulation. So, whenever you want to access some widget's data, you usually use an accessor named like "gtk_whatever_set_something()". There are very scarce cases of widgets that are directly manipulable by using the C . or -> operators.

Now, an "opened" window can be understood in various ways. Usually, what you do is to prebuild widgets and play using gtk_widget_show(). So, the signal you're looking for is "show". You could connect each window's "show" signal to a callback that +1 to some variable; "hide" would decrement that counter. Of course, wrap this around an if-block that checks whether monitoring is on or not. (What should be checked is whether "destroy" implies hiding or not)

But, if you considered "opened" as "allocated", what you'll need is to create a new constructor ("gtk_*_new()") that does that incrementing for you when allocating.

Of course, this all requires the use of a global variable or using a lot of pointers.

---

### Post by xoros on 2010-07-02
@nvteighen 
Thank you for the informative reply. 

So without doing what you've stated, there is not way to use **gtk_window_get_default_widget** whenever new windows are displayed?? 

It seems like it should be a very simple task.

---

### Post by xoros on 2010-07-02
> It's important to understand that gtk_widget_show()  has no immediate effect, it merely schedules the widget to be shown. This means you don't have to worry about showing widgets in any particular order; it also means that you can't immediately access the  GdkWindow of a widget. **Sometimes you need to access the GdkWindow**; in those cases you'll want to manually call gtk_widget_realize()  to create it. gtk_widget_realize() **will also realize a widget's parents**, if appropriate. 

I guess the above quote helps me understand better... but would there be a way to make a constant widget child so the parent widgets would be continually realized??

---

### Post by nvteighen on 2010-07-03
Could you please elaborate on what's your program's goal and what's the design idea for your GUI? I feel like I'm answering partial issues but never fully understanding where this is supposed to go; I can't help you like that.

If you can post some GUI code, it'd be very helpful.

---

### Post by xoros on 2010-07-03
Gtk is not going to do what I want.  Is there any framework that accesses the gnome desktop / gdm / gui on a global level? 

Should I be looking into using xlib or just trying to change things in gnome's gdm source code and recompiling :(   

I'm trying to do things which will ultimately affect the **global user interface** rather than just doing things on a gtk "single
application level". 

Thank you again for any advice on this

---

### Post by nvteighen on 2010-07-04
> **xoros said:**
> Gtk is not going to do what I want.  Is there any framework that accesses the gnome desktop / gdm / gui on a global level? 

Should I be looking into using xlib or just trying to change things in gnome's gdm source code and recompiling :(   

I'm trying to do things which will ultimately affect the **global user interface** rather than just doing things on a gtk "single
application level". 

Thank you again for any advice on this

Maybe the GNOME API? Though I still don't get what your project is about... if you want to control anything that's on the desktop, no matter where it comes from, you'll need to do a huge amount of communication between processes, due to the highly modular architecture of GNOME (and anything in GNU/Linux)...

---

### Post by xoros on 2010-07-06
**EDIT: Trying to work with this as a solution .. somehow.**

Is there a way to get a listing of dbus objects already existing on the dbus?
I'm thinking yes:
[http://manpages.ubuntu.com/manpages/lucid/man1/DBusViewer.1.html]("http://manpages.ubuntu.com/manpages/lucid/man1/DBusViewer.1.html")



**dbus-ping-send.py**
```
#! /usr/bin/env python

import gtk
import dbus

# Connect to the bus
bus = dbus.Bus()

# Create a service on the bus
service = dbus.Service("com.burtonini.dbus.SignalService", bus)

# Define a D-BUS object
class SignalObject(dbus.Object):
    def __init__(self, service):
        dbus.Object.__init__(self, "/", [], service)

# Create an instance of the object, which is part of the service
signal_object = SignalObject(service)

def send_ping():
    signal_object.broadcast_signal("com.burtonini.dbus.Signal", "Ping")
    print "Ping!"
    return gtk.TRUE

# Call send_ping every second to send the signal
gtk.timeout_add(1000, send_ping)
gtk.main()
```


**dbus-ping-listen.py**
```
#! /usr/bin/env python

import gtk
import dbus

bus = dbus.Bus()

def signal_callback(interface, signal_name, service, path, message):
    print "Received signal %s from %s" % (signal_name, interface)

# Catch signals from a specific interface and object, and call signal_callback
# when they arrive.
bus.add_signal_receiver(signal_callback,
                        "com.burtonini.dbus.Signal", # Interface
                        None, # Any service
                        "/" # Path of sending object
                        )

# Enter the event loop, waiting for signals
gtk.main()

```

*Code was found [here]("http://www.ibm.com/developerworks/linux/library/l-dbus.html")

---

