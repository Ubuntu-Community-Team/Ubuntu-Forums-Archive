---
title: "Python / Glade Signal Query"
date: 2012-06-22
forum: Programming Talk
---

### Post by s.fox on 2012-06-22
Hello everyone,

I am starting to build an application using python and glade and have a query about signals.

I have a button with the id mybutton,  which when pressed I can display "Button Pressed" in terminal. Here is an extract from my python script:

```

self.mybutton = self.builder.get_object("mybutton")
def on_mybutton_clicked(self, widget):
    print 'Button Pressed'

```The code above works fine,  but now I am trying to figure out how to do the same sort of thing with an image.   

After some research it appears that I have to use the button-press-event signal instead of clicked, which looks like it requires 3 parameters. My image has the the id myimage

```

self.myimage = self.builder.get_object("myimage")
def on_myimage_button-press-event(self,?,widget):
    print 'Image Clicked'

```I am not sure what I need to put as the middle parameter, I thought it might be GDK_BUTTON_PRESS but that returns an error.  I was hoping someone would be able to show a simple working example. 

Apologies if I have any of my terminology incorrect, I am on a steep learning curve but feel tantalisingly close to having it working.

Thank you for any help :)

---

### Post by r-senior on 2012-06-23
Are you using GObject introspection here?

If I can't figure out the correct arguments to a handler, I just print them out and refer to the GTK3 documentation for the signal to see how they have been mapped.

So I'd do something like:

```
self.myimage = self.builder.get_object("myimage")
def on_myimage_button-press-event(self, a, b):
    print a, b

```

(It will tell you if the number of arguments is incorrect).

Then look at DevHelp and cross-reference a and b. I'd guess the first parameter is going to be the widget and the second the event.

```
gboolean user_function(GtkWidget *[COLOR="Red"]widget[/COLOR], GdkEvent  *[COLOR="Red"]event[/COLOR], gpointer user_data)

The ::button-press-event signal will be emitted when a button (typically from a mouse) is pressed.

To receive this signal, the GdkWindow associated to the widget needs to enable the GDK_BUTTON_PRESS_MASK mask.

This signal will be sent to the grab widget if there is one.

widget : the object which received the signal.
event : the GdkEventButton which triggered this signal. [type Gdk.EventButton]
user_data : user data set when the signal handler was connected.
Returns : TRUE to stop other handlers from being invoked for the event. FALSE to propagate the event further.

```

There *should* be a better way. If there is, I don't know about it. ;)

---

### Post by s.fox on 2012-06-23
Hi again,

After more reading and some help on IRC I got it working.  I didn't have my image in an eventbox.

This is how I got it working:

```

    def handler(widget,event):
        print "Image pressed"  
    self.eventbox = self.builder.get_object("eventbox")
    self.eventbox.connect("button-press-event",handler)

```

Thank you also for your advice r-senior :)

---

