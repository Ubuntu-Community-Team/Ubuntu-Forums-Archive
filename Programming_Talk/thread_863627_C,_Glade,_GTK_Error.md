---
title: "C, Glade, GTK Error"
date: 2008-07-18
forum: Programming Talk
---

### Post by b3n87 on 2008-07-18
Hey,

Im getting into the whole programming world, my back ground was Visual Basic 6 so I coming from a different angle.

I found a really useful tutorial online on how to make your first GUI. I keep getting the same error though and Im a bit stuck, I have googled it but can't find an answer; im guessing its a dependency issue?

```
(tutorial:8489): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
```

Any ideas?

Oh and the tutorial is [here]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html"). Its really useful and informative. If you have any others spread the love :D

Thanks in advance!

---

### Post by days_of_ruin on 2008-07-18
> **b3n87 said:**
> Hey,

Im getting into the whole programming world, my back ground was Visual Basic 6 so I coming from a different angle.

I found a really useful tutorial online on how to make your first GUI. I keep getting the same error though and Im a bit stuck, I have googled it but can't find an answer; im guessing its a dependency issue?

```
(tutorial:8489): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed
```

Any ideas?

Oh and the tutorial is [here]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html"). Its really useful and informative. If you have any others spread the love :D

Thanks in advance!

Did you read the part about the menubar?You have to edit something in it
or else gtk-builder doesn't like it.Not sure if thats not what your 
error is.Try removing the menu bar and see if it works;D

---

### Post by b3n87 on 2008-07-20
Hey, thanks for the reply! I have been away this weekend so just got the post. Im having a look now at the menubar bit, thanks for pointing that out i must of missed that.

Thanks for that

---

### Post by m0ns00n on 2008-10-09
I'm still experiencing the problems. I'm using a minimal xml, with only one button. Tried everything, and I still have this exact error.

Anywhere I can turn?

My XML:

```

<?xml version="1.0"?>
<!--Generated with glade3 3.4.5 on Wed Oct  8 22:01:17 2008 -->
<interface>
  <object class="GtkWindow" id="window1">
    <child>
      <object class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <object class="GtkButton" id="button1">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="label" translatable="yes">button</property>
          </object>
        </child>
      </object>
    </child>
  </object>
</interface>

```

Code:

```

gtk_init ( &argc, &argv );

builder = gtk_builder_new ();
gtk_builder_add_from_file ( builder, "toolbox.xml", NULL );

tbxWindow = GTK_WIDGET ( gtk_builder_get_object ( builder, "tbxWindow" ) );
gtk_builder_connect_signals ( builder, NULL );
g_object_unref ( G_OBJECT ( builder ) );

gtk_widget_show ( tbxWindow );    

gtk_main ( );

```

---

### Post by arloth on 2008-10-09
I'm assuming your error is coming from this line?

```
tbxWindow = GTK_WIDGET ( gtk_builder_get_object ( builder, "tbxWindow" ) );

```

I'm not a big fan of learning a new toolkit while using the UI designer, you miss out on a good bit of understanding. What it would look like is your gtk_builder_get_object call is failing, and returning null, thus causing the GTK_WIDGET cast/check to fail.  I'm not too good with Glade myself yet, but I would say, change "tbxWindow" to "window1", it's looking for tbxWindow object in the XML and not finding it.

Check out the gtk_builder_get_object() API reference page, 
[http://library.gnome.org/devel/gtk/2.11/GtkBuilder.html#gtk-builder-get-object](http://library.gnome.org/devel/gtk/2.11/GtkBuilder.html#gtk-builder-get-object)

As far as a GTK reference and examples. You may want to check out "Foundations of GTK+ development" by Andrew Krause.  It's a pretty good book, and reasonably current.

---

