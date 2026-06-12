---
title: "create widget from dbus signals"
date: 2009-03-12
forum: Programming Talk
---

### Post by G|N| on 2009-03-12
Hello,

I am writing a service with plugins and these plugins could have different widgets for the options from the plugin.

The user interface is a different application that should ask the service what widgets it needs to set the options.

So what is the best way to send widgets over dbus?

Note: The widgets should be toolkit independent...

I thought something like this: [['label', 'widget'], ['label', 'widget']]
example: [['test', 'Entry']]

The string 'Entry' will be executed like a class in the user interface...

Does this seem a good solution?

And how about passing extra arguments?
For example for a checkbox if it should be checked or not by default?

Greetings

---

### Post by SeanHodges on 2009-03-13
> **G|N| said:**
> Hello,

I am writing a service with plugins and these plugins could have different widgets for the options from the plugin.

The user interface is a different application that should ask the service what widgets it needs to set the options.

Sounds pretty cool... and ambitious :)

Which language is this for?


> So what is the best way to send widgets over dbus?

Note: The widgets should be toolkit independent...

I thought something like this: [['label', 'widget'], ['label', 'widget']]
example: [['test', 'Entry']]

The string 'Entry' will be executed like a class in the user interface...

Does this seem a good solution?

I'm not familiar with any support for rich object transport in DBUS, as far as I'm aware it is primarily a message broker, and is limited to a set of primitive data types and collections.

One solution would be to write a widget factory for your UI that both abstracts the toolkit from your code, and describes each widget that you want the service to be able to create. You can then pass messages via DBUS containing the parameters required to build each widget.

Something along the lines of:

*DBUS signals:*

["textbox", 10, 20, "Please enter your name", ""]
["listbox", 10, 20, "Please select your age", "18-21;22-29;30+"]

*Factory method:*

```
function getWidget(type, x, y, caption, defaultValue)
{
    if type is "textbox" then
        return TextBox(caption, x, y, defaultValue);

     otherwise if type is "menubar" then
        return ListBox(caption, x, y, defaultValue);
    ...
}
```

---

### Post by G|N| on 2009-03-13
I'm writing the code in python :)

And indeed what you describe is what i mean!

Today i thought about a new solution:
I will create a file with different "widget" classes.
The plugin can use this class like this:
```

widget = widget.Entry("this is the label")

```

the Entry class will return something like this:
{'Entry': {'label': 'this is the label'} }

and this will be send by dbus...


The user interface will use a class that parses this dictionary back to a widget :)

This seems to be the best solution....but it will not be easy :)

I also don't want to use the "if widget == 'Entry'" method...it should be more dynamically and execute the key from the dictionary as a class, not a string

---

### Post by SeanHodges on 2009-03-14
> **G|N| said:**
> I'm writing the code in python :)

And indeed what you describe is what i mean!

Today i thought about a new solution:
I will create a file with different "widget" classes.
The plugin can use this class like this:
```

widget = widget.Entry("this is the label")

```

the Entry class will return something like this:
{'Entry': {'label': 'this is the label'} }

and this will be send by dbus...


The user interface will use a class that parses this dictionary back to a widget :)

This seems to be the best solution....but it will not be easy :)

I also don't want to use the "if widget == 'Entry'" method...it should be more dynamically and execute the key from the dictionary as a class, not a string

That seems viable, as far as implementation detail goes. One thing your design doesn't explain is how you will make the widgets toolkit independent (as you stated in the original post). So additionally I would suggest taking a look at the [Abstract Factory pattern]("http://en.wikipedia.org/wiki/Abstract_factory_pattern"), which should work well alongside what you are proposing to do.

I agree this might be quite a complicated approach. Are you familiar with Glade? Glade allows you to draw a UI in XML, and use a helper library to turn it into code. It is designed for GTK, but the theory is you can take the XML and map it to any toolkit later on (which is something you will have to do anyway with your current design).

The advantages: 
- You simplify your design dramatically.
- It will be much easier to debug everything later, for instance you can save the output XML to a file, and open it using the Glade UI tool to get a visual representation of the UI the plugin is trying to build. 
- XML is an easy format to glue together, you can simply inject each widget into a "parent" Glade XML.
- You get support for GTK straight away, with very little work.

The disadvantages: 
- You may not want to start with GTK support, which will mean you will have to start mapping the XML to a new toolkit straight away (check out QTDesigner if QT is your flavour of choice). 
- If you start passing particularly complex widgets over DBUS, the XML could get quite big.
- You will need to parse the XML before you can access the information about the widgets, which is fine for building them, but would cause a big overhead if you want to inspect just parts of the widget data for whatever reason.

DBUS signal:

```
["
<widget class="GtkHBox" id="textbox">
    <child>
          <widget class="GtkLabel" id="label1">
            <property name="label" translatable="yes">
                Please enter your name
            </property>
        </widget>
    </child>
    <child>
        <widget class="GtkEntry" id="entry1" />
    </child>
</widget>
"]
```

Python code in UI (GTK implementation, use abstract factory pattern to abstract this for other toolkits):

```
import gtk

data = gtk.glade.XML(xmlFromDbusSignal)
component = data.get_widget('textbox')
self.windowFrame.pack_end(component)
```

---

### Post by G|N| on 2009-03-20
This is how i fixed it in my code.

It may not be the cleanest solution but it is the easiest for creating new UI in the plugin.

**Service**

config.py
```

class Widget_():

    def entry(self, label, text=""):
        return {'Entry': ({'label': label}, {'text': text})}


    def password(self, label, text=""):
        return {'Password': ({'label': label}, {'text': text})}    

    
Widget = Widget_()

```

plugin.py
```

import config

def get_watch_ui():
    return [("username", config.Widget.entry(_("Username"))),
            ("password", config.Widget.password(_("Password")))]

```
Here you use the widget class to create a widget from a function.
A dictionary with the values is returned and this dictionary can be send over dbus


**Client**

gtkconfig.py
```

import gtk

class Entry():

    def __init__(self,values):
        for option, value in values:
            setattr(self, option, value)
        self.table = gtk.Table(rows=1, columns=2, homogeneous=True)
        self.gtkLabel = gtk.Label((self.label + ":"))
        self.gtkLabel.set_alignment(xalign=0.0, yalign=0.5)
        self.gtkLabel.show()
        self.table.attach(self.gtkLabel, 0, 1, 0, 1)

        self.entry = gtk.Entry()
        if self.text != None:
            self.entry.set_text(self.text)
        self.entry.show()
        self.table.attach(self.entry, 1, 2, 0, 1)
        self.table.show()

    def set_value(self, value):
        self.entry.set_text(value)

    def get_value(self):
        return self.entry.get_text()

    def get_widget(self):
        return self.table, self.entry

    def set_color(self, red, blue, green):
        self.entry.modify_base(gtk.STATE_NORMAL, \
            gtk.gdk.Color(red, blue, green))

    def grab_focus(self):
        self.entry.grab_focus()


class Password():

    def __init__(self, values):
        for option, value in values:
            setattr(self, option, value)        
        self.table = gtk.Table(rows=1, columns=2, homogeneous=True)
        self.gtkLabel = gtk.Label((self.label + ":"))
        self.gtkLabel.set_alignment(xalign=0.0, yalign=0.5)
        self.gtkLabel.show()
        self.table.attach(self.gtkLabel, 0, 1, 0, 1)

        self.entry = gtk.Entry()
        self.entry.set_visibility(False)
        if self.text != None:
            self.entry.set_text(self.text)
        self.entry.show()
        self.table.attach(self.entry, 1, 2, 0, 1)
        self.table.show()

    def set_value(self, value):
        self.entry.set_text(value)

    def get_value(self):
        return self.entry.get_text()

    def get_widget(self):
        return self.table, self.entry

    def set_color(self, red, blue, green):
        self.entry.modify_base(gtk.STATE_NORMAL, \
            gtk.gdk.Color(red, blue, green))

    def grab_focus(self):
        self.entry.grab_focus()

```

widgetparser.py
```

import gtkconfig

def parse(widgets):
    values = []
    widget = ""
    variable = ""
    for variable_, widget_ in widgets:
        variable = variable_
        widget = widget_.keys()[0]
        options_ = widget_.values()[0]
        obj = getattr(gtkconfig, widget)
        o = []
        for options in options_:
            for option in options.keys():
                o.append((option, options[option]))
        
        w = obj(o)
        values.append((variable, w))
    return values

```
The dictionary will be parsed by the parse function and it will automatically create the correct class using getattr :)

---

### Post by SeanHodges on 2009-03-22
Looks good to me :)

---

