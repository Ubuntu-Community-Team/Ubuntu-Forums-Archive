---
title: "Exploring GObject"
date: 2010-09-24
forum: Programming Talk
---

### Post by worksofcraft on 2010-09-24
At the heart of lots of computer language bindings and gnome libraries is the GObject hierarchy so I thought it would be well worth learning about. Exploring the objects instantiated by GtkBuilder, I'm now wondering how can I find out what type each one is? Well here is my code so far, compile as it says in first comment and I'll also include a sample .glade file.
```

// g++ main.cc `pkg-config --cflags --libs gtk+-2.0`
#include <gtk/gtk.h>
#include <stdio.h> // printf

int main(int Argc, char *Argv[]) {
	gtk_init (&Argc, &Argv);

	const char * Ui = "builder.glade"; // default file name
	if (Argc > 1) Ui = *++Argv; // can override on commande line
// interim diagnostic messages for development are not indented
printf("glade file is %s\n", Ui);

	GtkBuilder *Bob = gtk_builder_new(); // Bob the builder

	GError *Bad; // for error status
	guint Good; // for return status;
	Good = gtk_builder_add_from_file(Bob, Ui, &Bad);
printf("gtk_builder_add_from_file = %d\n", Good);
	if (!Good) {
		printf("GError = %s\n", Bad->message);
	}

	// get a singly linked list of all the objects
	GSList *ObjectList = gtk_builder_get_objects(Bob);
	GSList *It = ObjectList; // iterator for the list
	unsigned Count = 0;
	while (It) {
		++Count; // count entries in list
		**// TODO: identify the type of each object in the list**
		It = It->next;
	}
printf("List has %u objects\n", Count);
	if (ObjectList) g_slist_free(ObjectList);

	return 0;
}

```
builder.glade
```

<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window1">
    <child>
      <object class="GtkComboBoxEntry" id="comboboxentry1">
        <property name="visible">True</property>
        <property name="model">liststore1</property>
      </object>
    </child>
  </object>
  <object class="GtkListStore" id="liststore1">
    <columns>
      <!-- column-name gchararray1 -->
      <column type="gchararray"/>
    </columns>
    <data>
      <row>
        <col id="0" translatable="yes">row1</col>
      </row>
      <row>
        <col id="0" translatable="yes">row2</col>
      </row>
      <row>
        <col id="0" translatable="yes">3rd row</col>
      </row>
    </data>
  </object>
</interface>

```
 All constructive input appreciated, TIA :)

---

### Post by worksofcraft on 2010-09-24
Oh lol, it took a bit of searching but is actually very easy:
```

		GType Type = G_TYPE_FROM_INSTANCE(It->data);
		const gchar *Name = g_type_name(Type);
printf("Type=%lu=%s\n", Type, Name);

```
Next step is I want to find the unique names of each instance.

p.s. For those who might be wondering. Eventually I want to use these Gtk gui containers as items for my container formatting library. Then I can use formats to manipulate values in the GUI widgets and combine it with the other kinds of containers like environment and config files etc...

---

### Post by worksofcraft on 2010-09-25
So I'm not having as much luck getting to the object instance names. First we have to make sure that it's a widget:
```

bool is_GtkWidget(GType Type) {
	// TODO: check if there is a #define for this?
	static GType GtkWidgetType = g_type_from_name("GtkWidget");
	while (Type) {
		if (Type == GtkWidgetType) return true;
		Type = g_type_parent(Type);
	}
	return false;
}

```
...and then when we know it is one of these GtkWidget thingys call gtk_widget_get_name()
```

		if (is_GtkWidget(Type)) {
			const gchar *WidgetName =  gtk_widget_get_name((GtkWidget*) It->data);
printf("WidgetName=%s\n", WidgetName);
		}
		else {
printf("is not a GtkWidget\n");
		}

```

However that gtk_widget_get_name seems to be returning the very same string I was getting from g_type_name. :confused: Perhaps it isn't the instance name after all, or perhaps I'm using it the wrong way?!

There is just so much documentation out there and all relating to different versions, I'm beginning to think the sensible way to get to the bottom of it is by deciphering GtkBuilder source code :shock:

---

### Post by nvteighen on 2010-09-25
Hm... I recommend you to try coding GObject/GTK+ by hand if you want to understand how it works internally. GtkBuilder is hiding stuff for you.

What do you mean by "instance name"? If you want to get the type of some object, you're quite lost because in "real" GTK+ what you do is to declare **everything** as GtkWidget *. It's a technique based on the C++ pointer-to-base-class, because it's the only way to get class inheritance in C.

(BTW: I highly recommend you to read this. It's the specification of how GtkWidget works: [http://library.gnome.org/devel/gtk-tutorial/stable/x2184.html](http://library.gnome.org/devel/gtk-tutorial/stable/x2184.html))

If you want to get the object's name, then you're wasting time: you either use the variable's name or you can't... unless you extend the classes to have a "name" attribute and set that.

Also, if you're working with C++... you better use gtkmm (the official GTK+ C++ binding)...

---

### Post by worseisworser on 2010-09-25
> **nvteighen said:**
> Hm... I recommend you to try coding GObject/GTK+ by hand if you want to understand how it works internally. GtkBuilder is hiding stuff for you.

What do you mean by "instance name"? If you want to get the type of some object, you're quite lost because in "real" GTK+ what you do is to declare **everything** as GtkWidget *. It's a technique based on the C++ pointer-to-base-class, because it's the only way to get class inheritance in C.

(BTW: I highly recommend you to read this. It's the specification of how GtkWidget works: [http://library.gnome.org/devel/gtk-tutorial/stable/x2184.html](http://library.gnome.org/devel/gtk-tutorial/stable/x2184.html))

If you want to get the object's name, then you're wasting time: you either use the variable's name or you can't... unless you extend the classes to have a "name" attribute and set that.

Also, if you're working with C++... you better use gtkmm (the official GTK+ C++ binding)...

It's been a few years since I messed around with GObject and Gtk+ (so I don't think I feel like digging through this stuff again and actually help the OP with details...), but using GObject "means" that C (or his software) has a real (run-time) object/type system via this; each item really does have a type *via* GObject.

edit:
One might think of GObject as an interpreted type/object system.

---

### Post by worksofcraft on 2010-09-25
> **nvteighen said:**
> Hm... I recommend you to try coding GObject/GTK+ by hand if you want to understand how it works internally. GtkBuilder is hiding stuff for you.

What do you mean by "instance name"? If you want to get the type of some object, you're quite lost because in "real" GTK+ what you do is to declare **everything** as GtkWidget *. It's a technique based on the C++ pointer-to-base-class, because it's the only way to get class inheritance in C.


I haven't thought of anything I want to code yet, so instead I have a go at decoding what the builder is building.

Thus .glade file says:

     <object class="GtkComboBoxEntry" id="comboboxentry1">

GType name would be "GtkComboBoxEntry" and this particular instance name I'm kind of expecting to be "comboboxentry1"

> **nvteighen said:**
> 
(BTW: I highly recommend you to read this. It's the specification of how GtkWidget works: [http://library.gnome.org/devel/gtk-tutorial/stable/x2184.html](http://library.gnome.org/devel/gtk-tutorial/stable/x2184.html))


TYVM... I be reading that forth with :)

> **nvteighen said:**
> 
If you want to get the object's name, then you're wasting time: you either use the variable's name or you can't... unless you extend the classes to have a "name" attribute and set that.


Hum... I can get objects by name from the builder (whom I shall hence-forth name "Bob" because everyone knows about Bob the builder).
```

GObject* gtk_builder_get_object(GtkBuilder *builder, const gchar *name);

```
... so I don't see any reason Bob shouldn't tell me what name have the objects that I get from him.

> **nvteighen said:**
> 
Also, if you're working with C++... you better use gtkmm (the official GTK+ C++ binding)...
True, but the bindings to other languages like Python are based on Gtk not gtkmm and I want to learn how bindings to other languages are done as well.

---

### Post by SledgeHammer_999 on 2010-09-25
I think you need to do a [gtk_widget_get_name()](http://library.gnome.org/devel/gtk/stable/GtkWidget.html#gtk-widget-get-name) to get "comboboxentry1".

---

### Post by worksofcraft on 2010-09-25
> **SledgeHammer_999 said:**
> I think you need to do a [gtk_widget_get_name()](http://library.gnome.org/devel/gtk/stable/GtkWidget.html#gtk-widget-get-name) to get "comboboxentry1".

Yes that's what I thought too (see post #3).

Then I discovered not everything in the list is a GtkWidget and so it "assertion failed" on GtkListStore. I added code to check things were widgets first and then discovered that I'm just getting the object type name again :confused:

---

### Post by worksofcraft on 2010-09-25
Ah at last... apparently it's part of a recent update:


Release notes for 2.20
======================

* GtkBuilder no longer sets the "name" property of widgets to the ID
  attribute of the <object>. Use gtk_buildable_get_name() instead of
  gtk_widget_get_name() to obtain the ID.

... and it is much better now, because ALL the things that GtkBuilder builds will be GtkBuildable and I don't have to do that Widget type checking anymore :) On the one hand it may seem bad when a compatability issue has been created, but on the other hand it's good that it made me aware of the new and improved way of getting an instance name.

So now I suppose I can move on to look at how reference counting affects the scope of GObjects and how to access the values that user put in to their Widgets and Whatnots.

---

### Post by worksofcraft on 2010-09-25
... given the name of an interactive widget my prospective application simply wants to get the current value as entered by the user and here is where it gets tricky: Each and every Gtk Widget class has it's own method(s) to get the value e.g.

[LIST]
[*]gchar *gtk_combo_box_get_active_text(GtkComboBox *combo_box);

[*]gdouble gtk_scale_button_get_value(GtkScaleButton *button);

[*]gint gtk_spin_button_get_value_as_int(GtkSpinButton *spin_button);
[/LIST]

It's not polymorph and neither are the results! To make it even more complicated some need to be disposed of with g_free() when we're done with them and others don't :shock:

So when my app says: "gimme the value of widget named thingyadjuster" then my code has to find the GtkBuildable of that name, work out what GType it is and then call whatever method is available for that type.

Thus initially it appears the problems to solve are:
[LIST]
[*]Identify the GTypes for named Widget classes that have known get_value methods.
[*]Identify the GType of the nominated widget.
[*]Scan the class hierarchy of said Widget to see if it or any of it's parent classes provide one of those get_value methods.
[*]Call the method to get the value.
[*]g_free disposal on completion for some
[/LIST]
Note: luckily I do know when I want an int, a double or a string and it is perfectly acceptable to report errors like "Widget thingyadjuster cannot provide a text string result".

Hum... I think I try scanning the list of Widgets produced by Bob and wrap the interactive ones with a base class that has virtual get_value method(s). These wrapper objects I enter in an STL map to associate each with it's identifier. It can be done once rather than on every request for a value and by being polymorph they can also handle g_free calls where necessary. Oh well it's all good fun ;)

---

### Post by SledgeHammer_999 on 2010-09-26
wow did you just mention STL? That means you're using C++ right? Then leave gobject behind and go use [www.gtkmm.org](www.gtkmm.org)

---

### Post by worksofcraft on 2010-09-26
> **SledgeHammer_999 said:**
> wow did you just mention STL? That means you're using C++ right? Then leave gobject behind and go use [www.gtkmm.org](www.gtkmm.org)

Lol no I use C++ because I like it much more than C, but I still want to learn all about the the GObject hierarchy at the low level because that's what all the other language bindings are based on.

Also gtkmm is a just a C++ wrapper and it hasn't wrapped the Widgets quite the right way for what I want: I want to index them by name and get the value that user entered without having to hard code what kind of Widget it is.

I got it working now so I suppose I can mark this as solved...
Thanks for the input anyway :)

---

### Post by nvteighen on 2010-09-26
Hm... I'm not sure but wanting to list widgets by name sounds a bit weird. GUIs are static: you know each element at compile-time (unless you start creating something like a GUI builder, I guess), so sorting stuff by name sounds a bit... uh... extreme? I mean, at compile-time you've got each element's variable name or some API to access it.

So, gtk_builder_get_object does that: you have a "variable" name which is the id string and you get your object from something we could consider to be like a hash. Why would you want to know the name of the returned object if you used that name to get it?

Or maybe I don't get your point?

---

### Post by worksofcraft on 2010-09-26
> **nvteighen said:**
> Hm... I'm not sure but wanting to list widgets by name sounds a bit weird. GUIs are static: you know each element at compile-time (unless you start creating something like a GUI builder, I guess), so sorting stuff by name sounds a bit... uh... extreme? I mean, at compile-time you've got each element's variable name or some API to access it.

So, gtk_builder_get_object does that: you have a "variable" name which is the id string and you get your object from something we could consider to be like a hash. Why would you want to know the name of the returned object if you used that name to get it?

Or maybe I don't get your point?

That is a very valid question and not easy to explain. I must point to Python's ability to identify parameters by name, typically used for enhanced formatted output. What I'm actually doing is to access user input in widgets of the gui directly from format strings: so like say I want the value of my spinbutton1 and combobox2 formatted in a string and the particular collection of gui widgets where they reside is a thing built by GtkBuilder that I named Gui, then I can write something like:
```

string Msg = Gui.gettext("Now creating %spinbutton1$d entries for %combobox2$s!");
// or even simply:
Gui["statusbar"].settext("creating entries!");

```
It avoids having to know what type of widgets they are at compile time and avoids having to create a structure with pointers to them all as people currently do. Basically you just plug in whatever .glade file you want and as long as the widgets have corresponding names the gui works with the program.

It's a proto-type experiment in internationalization and localization.

p.s. regarding gtk_builder_get_object, it could be done that way, but current practice is to ask for each widget by name and create a rigid structure containing widget pointers to work with. Then disposing of the builder. Instead I'm just creating an STL container to work with.

---

### Post by nvteighen on 2010-09-27
> **worksofcraft said:**
> That is a very valid question and not easy to explain. I must point to Python's ability to identify parameters by name, typically used for enhanced formatted output. What I'm actually doing is to access user input in widgets of the gui directly from format strings: so like say I want the value of my spinbutton1 and combobox2 formatted in a string and the particular collection of gui widgets where they reside is a thing built by GtkBuilder that I named Gui, then I can write something like:
```

string Msg = Gui.gettext("Now creating %spinbutton1$d entries for %combobox2$s!");
// or even simply:
Gui["statusbar"].settext("creating entries!");

```
It avoids having to know what type of widgets they are at compile time and avoids having to create a structure with pointers to them all as people currently do. Basically you just plug in whatever .glade file you want and as long as the widgets have corresponding names the gui works with the program.

It's a proto-type experiment in internationalization and localization.

p.s. regarding gtk_builder_get_object, it could be done that way, but current practice is to ask for each widget by name and create a rigid structure containing widget pointers to work with. Then disposing of the builder. Instead I'm just creating an STL container to work with.

Ah, ok, now I understand the context... 

Hm... I'm not sure of this, and I'm not sure why, because the idea seems really interesting... maybe it's just that this is a bit of an unusual approach... So, I better wait for your code; it'll be way more practical then :) Good luck!

---

