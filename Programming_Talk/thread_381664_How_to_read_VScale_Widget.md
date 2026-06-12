---
title: "How to read VScale Widget?"
date: 2007-03-11
forum: Programming Talk
---

### Post by ZDemon on 2007-03-11
Hi guys.

I know this is a silly question, but i just cant figure it out. How do you read a GtkVScale Widget to get its value? Ive looked through DevHelp and i cant find anything. I use libglade with cairo. I dont really understand the GTK long-winded examples. They are too difficult for my level of GUI programming.

Thanks for any help.

---

### Post by lnostdal on 2007-03-11
widgets have properties .. so we take a look here [http://developer.gnome.org/doc/API/2.0/gtk/GtkVScale.html](http://developer.gnome.org/doc/API/2.0/gtk/GtkVScale.html) to see if there are any properties for this widget

(looking at the top) there are no properties for this widget, but maybe there are properties in the superclasses of GtkVScale we can use .. [http://developer.gnome.org/doc/API/2.0/gtk/GtkVScale.html#id2927505](http://developer.gnome.org/doc/API/2.0/gtk/GtkVScale.html#id2927505) .. further .. [http://developer.gnome.org/doc/API/2.0/gtk/GtkScale.html](http://developer.gnome.org/doc/API/2.0/gtk/GtkScale.html) .. which leads to [http://developer.gnome.org/doc/API/2.0/gtk/GtkScale.html#id3659180](http://developer.gnome.org/doc/API/2.0/gtk/GtkScale.html#id3659180) ..  clicking on any of those we conclude that none of them are what you're after .. so we navigate further up the OO hierarchy via [http://developer.gnome.org/doc/API/2.0/gtk/GtkScale.html#id3659089](http://developer.gnome.org/doc/API/2.0/gtk/GtkScale.html#id3659089) to [http://developer.gnome.org/doc/API/2.0/gtk/GtkRange.html](http://developer.gnome.org/doc/API/2.0/gtk/GtkRange.html) and its properties: [http://developer.gnome.org/doc/API/2.0/gtk/GtkRange.html#id3650082](http://developer.gnome.org/doc/API/2.0/gtk/GtkRange.html#id3650082) .. "adjustment" is the property your after [http://developer.gnome.org/doc/API/2.0/gtk/GtkRange.html#GtkRange--adjustment](http://developer.gnome.org/doc/API/2.0/gtk/GtkRange.html#GtkRange--adjustment)

[http://developer.gnome.org/doc/API/2.0/gtk/GtkAdjustment.html](http://developer.gnome.org/doc/API/2.0/gtk/GtkAdjustment.html) and more specifically: [http://developer.gnome.org/doc/API/2.0/gtk/GtkAdjustment.html#GtkAdjustment--value](http://developer.gnome.org/doc/API/2.0/gtk/GtkAdjustment.html#GtkAdjustment--value)

to get the properties you use `g_object_get' ( [http://developer.gnome.org/doc/API/2.0/gobject/gobject-The-Base-Object-Type.html#g-object-get](http://developer.gnome.org/doc/API/2.0/gobject/gobject-The-Base-Object-Type.html#g-object-get) )

```

GtkAdjustment* adjustment;
g_object_get(vscale, "adjustment", &adjustment);
gdouble value;
g_object_get(adjustment, "value", &value);
printf("The value is: %f\n", value);
g_object_unref(adjustment);

```

..or, you can do:
```

printf("The value is: %f\n", gtk_adjustment_get_value(gtk_range_get_adjustment(vscale)));

```
or
```

printf("The value is: %f\n", gtk_range_get_adjustment(vscale)->value);

```

(edit: this post was written in about 30 seconds .. might contain errors .. lol edit2: %d should have been %f)

---

### Post by ZDemon on 2007-03-11
Well, i tried all the examples you gave, but they all return a value of 0. Maybe there is a mistake on my part? Im pretty sure I'm using a GtkVScale widget.

By the way Inostdal, cairo rocks.

EDIT : Hey hey, it works. There is an error. The printf function must be %f, not %d !! But a warning "warning: passing argument 1 of &#8216;gtk_range_get_adjustment&#8217; from incompatible pointer type" still shows up though. Here's the fixed code :

```
printf("The value is: %f\n", gtk_range_get_adjustment(vscale)->value);
```

Thanks Inostdal.

---

### Post by lnostdal on 2007-03-11
ah, yes .. a double is returned . .not an int :)

edit:
try some casting to avoid the warning:
gtk_range_get_adjustment((GtkRange*)vscale)->value

---

### Post by ZDemon on 2007-03-11
Yes, the warning is gone now.

Thanks. :)

---

