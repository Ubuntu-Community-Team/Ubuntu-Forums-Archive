---
title: "PyGTk"
date: 2008-12-27
forum: Programming Talk
---

### Post by 7raTEYdCql on 2008-12-27
I am trying to build a program with a GUI interface.

For that i am seperately learning PyGTk. This from the pygtk tutorial that is available in the repositories.

As i am going through the tutorial there are certain things that i begin thinking about.

How do i link my program with the GUI that i am building. I mean they haven't given any example where there is input information and the program will manipulate the information to give an output result. All that i am doing is building GUI's with buttons here and there. Menus here and there, and that is kind of ticking me off.

Then i come accross this thing called Glade. I download this tool Glade Interface Designer and start building my GUI's using it. It is easier i must admit, but am facing the same problem. 

I still have this basic question. When does the GUI that i build meet the program that i am writing?

---

### Post by 7raTEYdCql on 2008-12-27
Please can someone help me with an online tutorial which can solve this for me, or a sample program with PyGTk.

---

### Post by cmat on 2008-12-28
If you use glade I think you have to load up the XML resource file and connect the events to your program. I moved to wxPython ages ago so I cant remember the details. 

Here is an extremely useful few pages I used to get started. 
[http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/](http://www.learningpython.com/2006/05/07/creating-a-gui-using-pygtk-and-glade/)
[http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/](http://www.learningpython.com/2006/05/30/building-an-application-with-pygtk-and-glade/)

---

### Post by Tony Flury on 2008-12-28
if you are using pyGTK directly you have two methods of getting information from the GUI that you build - and I would agree that the tutorial does not fully explain this.

1) a number of the GUI elements (buttons mainly but some others too) primarily use signals as their main method of interaction with your program - look at the "connect" method. Your Application will need to connect a function or method to a signal (for instance the "clicked" signal on a button), and when that function is activated you know that the user has clicked your button.

2) other GUI elements (such as Text boxes, image panels) etc, have attributes on the widgets that you can use to extract the data from the widget - so you can see what data has been typed.

As promised - a short example - the meat of this is in the button clicked function. You will see in line 30 where this function is "connected" to the clicked signal on the Button widget. In the button clicked function itself it extracts the string from the Entry Widget (using the get_text method), and sets the Label (using the set_text method).

Usage - type something into the text entry (above the button) and then click the button.

Clearly this example is not particularly useful but hopefully it illustrates the principles.

```

"""
"""
import pygtk
pygtk.require('2.0')
import gtk

def delete_event(event, data=None):
    """ Only called when the user closes the window
    """
    gtk.main_quit()

def button_clicked(event, data=None):
    """Called when the user clicks the button
    """
    # Retrieve the text from the entry widget
    # Use the get_text method defined on the gtk.Entry Widget
    text = entry.get_text()

    # Set the text from the lebel widget
    # Use the set_text method defined on the gtk.Label Widget
    label.set_text(text[::-1])

if __name__ == "__main__":
    window = gtk.Window(gtk.WINDOW_TOPLEVEL)
    window.set_title("Example of GUI Interaction")
    window.connect("delete_event", delete_event)
    VBox = gtk.VBox(False, 5)
    entry = gtk.Entry(max=30)
    button = gtk.Button(label="Reverse")
    button.connect("clicked",button_clicked)
    label = gtk.Label()
    VBox.pack_start(entry, True, True, 5)
    VBox.pack_start(button, False, False,5)
    VBox.pack_start(label,True,True,5)
    window.add(VBox)
    window.show_all()

    gtk.main()

```

---

### Post by nvteighen on 2008-12-28
GTK+ works on the basis of signals and a main loop that checks what signals have been fired. So, each object's event is a signal and you connect an action to that signal. Therefore, when the main loop gets it, it will know what to do.

I guess the main loop is optimized to check only those signals that may be relevant to check, otherwise the performance penalty would be really huge...

---

### Post by slavik on 2008-12-28
as far as connecting, the nice thing about GTK in Perl, Python, Ruby is that there are autoconnect functions that given a class/package will automagically connect functions to the defined handlers (if you defined the handlers in the glade XML files for the widget).

---

### Post by 7raTEYdCql on 2008-12-28
In the program mentioned above why in the arguments of the callback function there is not mentioning of widget.

Wouldnt the callback functions be

def button_clicked(self, widget, data=None)
def delete_event(self, widget, event, data=None)

---

### Post by 7raTEYdCql on 2008-12-28
Sorry when you are not mentioning any classes you dont mention self.

Anyway i am confused about class,def. Can someone draw a line between the two.

---

### Post by nvteighen on 2008-12-29
> **i.mehrzad said:**
> Sorry when you are not mentioning any classes you dont mention self.

Anyway i am confused about class,def. Can someone draw a line between the two.
Yuck...

A "class" is just that: a class of objects... you could call it a "concept", "species", etc. For example, a "table" is a class, a "computer" is a class, a "binary tree" may be also a class. A class is something that both **has some attributes** and **does some actions**. These actions ("methods") and attributes are conveniently declared as the fundamental and defining elements of some class.

The objects are then just instances of that class. So, you have the class "dog" and any dog of yours is just a particular instance of it; it shares the fact with my dog (if it existed :)) that both are "dogs", but they are different individuals.

A function, instead, is just an action that is "floating there without any peculiar association" (excuse my absolutely unscientific definition). It's just a procedure on how to do something given some parameters.

---

### Post by Tony Flury on 2008-12-29
re you question about the widget etc 

wouldn't the functions be : 
```

def button_clicked(self, widget, data=None)
def delete_event(self, widget, event, data=None) 

```
Yes - but since the parameters are named - and  I am guessing that pyGTK calls them using names, so you can omit them - it might be bad practice though - and i apologise for any confusion.

---

