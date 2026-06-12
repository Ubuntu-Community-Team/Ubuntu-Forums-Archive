---
title: "Python GTK apps, how to structure?"
date: 2011-05-21
forum: Programming Talk
---

### Post by r-senior on 2011-05-21
I'm sick of tired of people on this forum banging on about how good Python is and how it can do everything ...

... so I've decided to try it. ;)

Here's a question:

What's the best idiom for structuring a Python GTK app? I've done GTK programming with C, which is obviously procedural, and also Swing with Java, which is object-oriented. But Python can lean either way. So which of the three approaches below is preferred and why?

```
#/usr/bin/env python

# 1. Procedural version (similar to a C/GTK app)

import gtk, pygtk

def on_window_destroy(widget):
	gtk.main_quit()

def main():
	window = gtk.Window(gtk.WINDOW_TOPLEVEL)
	window.set_size_request(400, 300)
	window.connect("destroy", on_window_destroy)
	window.show_all()

if __name__ == "__main__":
	main()
	gtk.main()

```

```

#/usr/bin/env python

# 2. Using a class with no inheritance (as seen in Python GTK tutorial)

import gtk, pygtk

class Application:

	def on_window_destroy(self, widget):
		gtk.main_quit()

	def __init__(self):
		window = gtk.Window(gtk.WINDOW_TOPLEVEL)
		window.set_size_request(400, 300)
		window.connect("destroy", self.on_window_destroy)
		window.show_all()

if __name__ == "__main__":
	application = Application()
	gtk.main()

```

```

#/usr/bin/env python

# 3. Using a class with inheritance (the Java/Swing way)

import gtk, pygtk

class Application(gtk.Window):

	def on_window_destroy(self, widget):
		gtk.main_quit()

	def __init__(self):
		gtk.Window.__init__(self, gtk.WINDOW_TOPLEVEL)
		self.set_size_request(400, 300)
		self.connect("destroy", self.on_window_destroy)
		self.show_all()

if __name__ == "__main__":
	application = Application()
	gtk.main()

```

---

### Post by Tony Flury on 2011-05-21
I would use the 2nd method.

Although I would create an GUI class - and not an Application class : The GUI class should expose the GUI functionality, not the widgets - so for instance if your application Gui has a set of widgets dedicated to changing colour for example : Your GUI class should expose methods for setting and getting the colour (and maybe an event when the colour changes) - the complexity of the various buttons and widgets should be hiddden within the class

You should all have the application logic (i.e. what happens with the new colour) separated from the GUI class.

See : [http://en.wikipedia.org/wiki/Model-View-Controller](http://en.wikipedia.org/wiki/Model-View-Controller) for the general idea.

---

### Post by simeon87 on 2011-05-21
I must say have structured my program as the third way (Java-inspired) but the second or third method would be my recommendation. The first way is going to be a mess because you'll be passing the window around constantly.
It happens frequently that you need access to the window object to do something (e.g., redraw something, show something somewhere, etc).

 It's better to have a GUI object from which everything follows. For example, the user presses a button which then interacts with the rest of your code.

I think the second method is also defendable: if you're going to *use* a window, why would you subclass it (Java / 3rd approach)? So the second approach makes more sense, although the GUI object isn't really anything and merely serves to contain all GUI-related code.

---

### Post by cgroza on 2011-05-21
I would use the third method, that is how we do it in wxPython.

---

### Post by StephenF on 2011-05-21
The PyGTK tutorial teaches the second and since a complex window can require a lot of code and be responsible for wide aspects of a program's function writing a big program this way results in a [blob class]("http://sourcemaking.com/antipatterns/the-blob") where callback after callback are stacked on top of one another and the init method constructs all the widgets in the entire window and assembles the interconnections. Throw in some factory functions written as methods because putting them elsewhere would make for some odd external references and it just gets bigger and bigger. [The run on sentence was put there on purpose to reflect what could be called run on programming.]

Classes ideally often encompass the quantity of code that goes to make up the visible contents of a gtk.Frame. This makes it probably one of the most subclassed of the GTK widgets. The inter-coupling of widgets can go on inside this smaller class and you can just as easily patch in from outside in order to drive it and respond to it. The third design method establishes a code hierarchy.

To see how the program structure might result from using method three:
[LIST]
[*]First take a pen and draw concentric circles from the outside in but inside some circles draw two, three, or more equal size circles. Keep drawing inside those. Now draw multiple arrows from the outside circles pointing at the ones on the next level in. Imagine each circle is an instance of a class and each arrow is a method access of one of the public interface methods of the inner client class.

[*]Second make another circle and just draw arcs coming from and into itself. This is what intra class access looks like and in the blob class it's almost all of what's happening.
[/list]

This does not mean that I think all classes ought to be be subclasses of widgets. It often makes sense to subclass from dbus.service.Object in order to add D-Bus functionality to your program. The multiple inheritance route in this particular case is messy.

---

### Post by juancarlospaco on 2011-05-21
I recently posted a *Procedural version* of some code and people keep trolling on me,
if its so terrible-bad-apocaliptic, i think the *Procedural version* needs to be Forbidden from the language.

---

### Post by StephenF on 2011-05-21
> **juancarlospaco said:**
> I recently posted a *Procedural version* of some code and people keep trolling on me,
if its so terrible-bad-apocaliptic, i think the *Procedural version* needs to be Forbidden from the language.
Writing bad code needs to be forbidden from the language. :D

---

### Post by juancarlospaco on 2011-05-21
> **StephenF said:**
> Writing bad code needs to be forbidden from the language. :D

Procedural version == bad code ???

---

### Post by StephenF on 2011-05-21
> **juancarlospaco said:**
> Procedural version == bad code ???
For GUI apps OOP is the way to go. Widgets are natural objects and should be modelled as such (playing with words here). 

C lets you create pseudoclasses by writing your code in modules and by having an init function that creates a namespace using malloc() for that pseudoclass with internals mapped to a structure often defined in the module's header file. This is fine because the C language supports this type of programming.

In Python you create namespaces by creating either a namespace class or by instantiating one so if you need to make a class in order to have a namespace you might as well put your methods inside it too, otherwise you have just made an inside-out class using free functions and classes anyway.

---

### Post by Tony Flury on 2011-05-22
> **juancarlospaco said:**
> I recently posted a *Procedural version* of some code and people keep trolling on me,
if its so terrible-bad-apocaliptic, i think the *Procedural version* needs to be Forbidden from the language.

As one of the people who responded to your other thread - I object to my comments being classed as Trolling.  The people who commented on your code were not being malicious, they were trying to help. It is a fact (which i can bear out with 20+ years in the s/w industry) that well structured code, with well defined and stable interfaces between the code units (be those functions, classes etc) is always easier to understand, maintain and develop. When you are working with a powerful language such as Python, it is always best to try to learn how to use all the powerful features, which are there to make your code simple and better

---

### Post by Tony Flury on 2011-05-22
> **juancarlospaco said:**
> Procedural version == bad code ???

No - in some cases Procedural is the only thing you can do (if your language does not support anything else) but you still should write code with well defined, stable interfaces, and some OOP type design pattern allows you to do that (it is not the only way - but in languages like python, it is very easy to do OOP).

---

### Post by r-senior on 2011-05-22
Interesting comments and some useful insights. Obviously it's more complex than the examples I posted, the question of subclassing not being so much with the main window but it's contents. I take it this is the key idea:

> Classes ideally often encompass the quantity of code that goes to make up the visible contents of a gtk.Frame.

I can see that structure working well with Glade too. I've had problems with Glade in the past but I'm going to give it another try.

---

### Post by r-senior on 2011-05-25
OK, I'm making progress but Glade is doing its best to stop me ...

I'm trying to create a dialog that allows the entry of some data that is converted into an Order object. The details of that object aren't important.

So I have an action (linked to UI elements) and an event handler:

```
    
    def on_action_add_activate(self, widget, data=None):
        dialog = OrderDialog(self.window)
        response = dialog.run()
        if response == RESPONSE_ADD:
            self.orders.add(dialog.get_order());
        dialog.destroy()

```

Which is OK. I'm happy with that. It's the OrderDialog class that I haven't got right and it's Glade that's blocking me:

```

class OrderDialog():

    def __init__(self, parent, order=None):
        builder = gtk.Builder()
        builder.add_from_file("orderdialog.glade")
        self.dialog = builder.get_object("dialog_order")
        self.entry_description = builder.get_object("entry_description")
        self.textview_address = builder.get_object("textview_address")

        self.dialog.set_transient_for(parent)

        if order == None:
            self.entry_description.set_text("")
            self.textview_address.get_buffer().set_text("")

    def get_order(self):
        buf = self.textview_address.get_buffer()
        address_text = buf.get_text(buf.get_start_iter(), buf.get_end_iter())
        address = Address(address_text)
        description = self.entry_description.get_text()
        order = Order(description=description, address=address)
        return order

    def run(self):
        return self.dialog.run()

    def destroy(self):
        self.dialog.destroy()

```

Ideally I want OrderDialog to be a subclass of gtk.Dialog but my inexperience with Python means I can't see a way. Is it possible to have the constructor return the instance that I get from Glade and avoid that messy delegation of the run and destroy methods?

Or do I need to go a level down in the Glade tree, construct a dialog in code and add the contents of the Glade dialog? I'd prefer just to use the whole dialog as designed in Glade really.

---

### Post by StephenF on 2011-05-25
> **r-senior said:**
> Or do I need to go a level down in the Glade tree, construct a dialog in code and add the contents of the Glade dialog? I'd prefer just to use the whole dialog as designed in Glade really.
Two ideas: 1, Construct the dialog in code and the contents of the two areas in glade. These can be gtk.HBox objects to be placed in similar boxes of the dialog is not a problem.

2, better delegation with __getattr__ and __setattr__
```

class Delegate(object):
    def __init__(self, inner):
        self.__inner = inner

    def __getattr__(self, name):
        return getattr(self.__inner, name)

```
Use it as a mix-in class. Init establishes the inner object. Edit: Untested.

---

### Post by r-senior on 2011-05-26
Thanks for those suggestions.

I tried a few things yesterday without any real success and I ended up following your sugegstion 1, i.e. using Glade to lay out the dialog content and building the dialog in code. This has the additional advantage of working round a deficiency in Glade in terms of specifying return IDs from dialogs.

For reference:

```

class OrderDialog(gtk.Dialog):

    def __init__(self, parent, order=None):
        gtk.Dialog.__init__(
            self
        ,   "Order"
        ,   parent
        ,   gtk.DIALOG_MODAL | gtk.DIALOG_DESTROY_WITH_PARENT
        ,   (   gtk.STOCK_CANCEL, gtk.RESPONSE_REJECT
            ,   gtk.STOCK_OK, gtk.RESPONSE_ACCEPT
            )
        )
        builder = gtk.Builder()
        builder.add_from_file("orderdialog.glade")
        content = builder.get_object("content")
        self.get_content_area().add(content)

        self.entry_description = builder.get_object("entry_description")
        self.textview_address = builder.get_object("textview_address")

        if order != None:
            self.entry_description.set_text(order.description)
            self.textview_address.get_buffer().set_text(str(order.address))

    def get_order(self):
        buf = self.textview_address.get_buffer()
        address_text = buf.get_text(buf.get_start_iter(), buf.get_end_iter())
        address = Address(address_text)
        description = self.entry_description.get_text()

        return Order(description=description, address=address)
```

But the technique in your suggestion 2 is useful.

I suppose ideally Glade would allow a dialog to specify a subclass of gtk.Dialog (in my case OrderDialog) that should be created. But it doesn't as far as I can see, so your suggestion 1 appears to me to be the best solution.

---

### Post by StephenF on 2011-05-26
Ideally gtk.Builder would present the top-level widgets not as instances but as subclasses so you would get a class with a custom init method that could be subclassed further.

IIRC QT went this route some years ago causing a rewrite of KDE 2 codebase to version 3.

---

