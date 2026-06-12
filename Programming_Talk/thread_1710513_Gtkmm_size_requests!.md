---
title: "Gtkmm size requests!"
date: 2011-03-20
forum: Programming Talk
---

### Post by roadkillguy on 2011-03-20
Not sure if you've all used gtkmm, but sometimes it's auto resizes can be pretty annoying.  I've been creating combo boxes, and they look absolutely ridiculous because they fill up their entire container widget.  They're much, much, fatter than the text itself.  Set_size_request() does next to nothing if it doesn't pertain to the window itself.

Has anybody ever made a decent-looking combo box?  Is there a workaround to this?  Maybe I should use a different library.

---

### Post by SledgeHammer_999 on 2011-03-20
You probably haven't learned how to use the Gtk+ containers properly. I admit that in the begining, the containers are difficult to understand, but once you understand them you don't have to worry about handling the resizing of your widgets. It is done automatically by your containers.

First of all, do you have some example code to show us, so we can help?

Secondly, you should reade this section of the Gtk+ tutorial. [link](http://library.gnome.org/devel/gtk-tutorial/stable/c354.html). It instructions work for Gtkmm too. The equivalent Gtkmm tutorial section is this [one](http://library.gnome.org/devel/gtkmm-tutorial/unstable/chapter-container-widgets.html). The Gtkmm one doesn't explain things as nicely/verbosely as the Gtk does.

---

### Post by roadkillguy on 2011-03-20
Probably not.. but this is what I have so far.

```

+------+------------+
|OR1   |            |
|OR2   |[BIG CB]    |
|OR3   |            |
|OR4   +------------+
|OR5   |[CB2 & BUT.]|
|OR6   |            |
+------+------------+
```

That's how I pack it.  There's a left and right VBox, and the right one has a couple Frames containing HBoxes, which contain buttons.  I would like to make it so that the combo box and buttons don't completely fill up their containers.

```

mapSizeBox.pack_start(*sizesComboBox);  //mapSizeBox is the hbox
mapSize->add(mapSizeBox);  //mapSize is the frame

modOptionsBox.pack_start(*modsComboBox);  //modOptionsBox is the hBox
modOptionsBox.pack_start(refreshModsButton);
modOptions->add(modOptionsBox);  //modOptions is the frame

optionsRightBox.pack_start(*mapSize);  //optionsRightBox is the right column (vbox)
optionsRightBox.pack_start(*modOptions);



```

---

### Post by Tony Flury on 2011-03-20
I have not used gtkmm - but i think you need to look at the packing options : 

[http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-multi-item-containers.html.en#sec-boxes](http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-multi-item-containers.html.en#sec-boxes)

---

### Post by SledgeHammer_999 on 2011-03-20
> **roadkillguy said:**
> Probably not.. but this is what I have so far.

```

+------+------------+
|OR1   |            |
|OR2   |[BIG CB]    |
|OR3   |            |
|OR4   +------------+
|OR5   |[CB2 & BUT.]|
|OR6   |            |
+------+------------+
```

That's how I pack it.  There's a left and right VBox, and the right one has a couple Frames containing HBoxes, which contain buttons.  I would like to make it so that the combo box and buttons don't completely fill up their containers.

```

mapSizeBox.pack_start(*sizesComboBox);  //mapSizeBox is the hbox
mapSize->add(mapSizeBox);  //mapSize is the frame

modOptionsBox.pack_start(*modsComboBox);  //modOptionsBox is the hBox
modOptionsBox.pack_start(refreshModsButton);
modOptions->add(modOptionsBox);  //modOptions is the frame

optionsRightBox.pack_start(*mapSize);  //optionsRightBox is the right column (vbox)
optionsRightBox.pack_start(*modOptions);



```

I suppose that **sizesComboBox** is a Gtk::ComboBox*.

Instead of **mapSizeBox.pack_start(*sizesComboBox);** try
```
mapSizeBox.pack_start(*sizesComboBox, Gtk::PACK_EXPAND_PADDING);
```
or
```
mapSizeBox.pack_start(*sizesComboBox, Gtk::PACK_SHRINK);
```

Does one of these do what you want? I suppose the second one will do. If not, please explain what is missing...

---

### Post by roadkillguy on 2011-03-20
> **SledgeHammer_999 said:**
> I suppose that **sizesComboBox** is a Gtk::ComboBox*.

Instead of **mapSizeBox.pack_start(*sizesComboBox);** try
```
mapSizeBox.pack_start(*sizesComboBox, Gtk::PACK_EXPAND_PADDING);
```
or
```
mapSizeBox.pack_start(*sizesComboBox, Gtk::PACK_SHRINK);
```

Does one of these do what you want? I suppose the second one will do. If not, please explain what is missing...

Ahhh, I didn't know pack_start took in multiple arguments.  It resizes only in the direction of the box (H or V), so I solved that by adding it when they are packed as well.

Thanks!

---

### Post by SledgeHammer_999 on 2011-03-20
> **roadkillguy said:**
> Ahhh, I didn't know pack_start took in multiple arguments.  It resizes only in the direction of the box (H or V), so I solved that by adding it when they are packed as well.

Thanks!

No problem.
By the way, ALWAYS look at the API. Many methods are overloaded. And some of them have default parameter values too.
For instance Gtk::Box::pack_start() is overloaded with 2 methods. Both of them use default values for some parameters:

[http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Box.html](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Box.html)

---

