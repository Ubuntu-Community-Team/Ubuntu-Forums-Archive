---
title: "Python: Driving me crazy!"
date: 2011-08-23
forum: Programming Talk
---

### Post by Legend1222 on 2011-08-23
I'm revisiting an old Python program. I am not an expert by any means. Slightly above novice. This program uses GTK Builder, but I don't think thats my issue (entire program below).

This program works fine on Jaunty (9.04), which is what it was originally written on. It does not work on 10.04 (haven't tried later versions). I can pin down the problem, but I don't understand it. Hopefully someone can explain it to me.

Jauntys version of python is 2.6.2, Lucids is 2.6.5.

The line of the code that describes the problem is in the __init__ section, where it says "print w.name" (line 86 below). Thats solely in there for debugging purposes. Nothing else has been changed. When the program runs on Jaunty, you get a list of the objects in the glade file: window1, vbox1, eventbox1, label1, and entry1. On Lucid you get: None, None, None, None and None. With w.name coming out as None, the exec line of the code (line 87) fails and therefore no GUI.

I've checked dependencies, I really don't think i'm missing anything. I doubt python changed that much in 0.0.3 releases, but i'm starting to wonder. name is stilled listed as an attribute, but I don't get why its not being populated.

Any ideas and help would be greatly appreciated. This is driving me nuts.

```
[LIST=1]
[*]#! /usr/bin/env python
[*]# -*- coding: utf-8 -*-

[*]import sys

[*]try:
[*]    import gtk
[*]except:
[*]    print "GTK missing or cannot be found"
[*]    sys.exit(1)
[*]    
[*]class colorsplash:
[*]    gui=''
[*]    
[*]    def editlabel(self):
[*]        label=self.entry1.get_text().upper()
[*]        if label == "MONKEY":
[*]            label="Stuffed Monkey"
[*]            color="GRAY"
[*]        elif label == "QUIT": gtk.main_quit()
[*]        else: 
[*]            label = "RE-SCAN"
[*]            color="BLUE"
[*]        self.label1.set_text(label)
[*]        self.eventbox1.modify_bg(gtk.STATE_NORMAL, gtk.gdk.color_parse(color))
[*]        self.entry1.set_text('')
[*]        
[*]    def load_gui(self): 
[*]        self.gui='''
[*]<?xml version="1.0"?>
[*]<interface>
[*]  <requires lib="gtk+" version="2.16"/>
[*]  <!-- interface-naming-policy project-wide -->
[*]  <object class="GtkWindow" id="window1">
[*]    <property name="window_position">center</property>
[*]    <signal name="destroy" handler="on_window1_destroy"/>
[*]    <child>
[*]      <object class="GtkVBox" id="vbox1">
[*]        <property name="visible">True</property>
[*]        <property name="orientation">vertical</property>
[*]        <child>
[*]          <object class="GtkEventBox" id="eventbox1">
[*]            <property name="visible">True</property>
[*]            <child>
[*]              <object class="GtkLabel" id="label1">
[*]                <property name="visible">True</property>
[*]                <property name="label" translatable="yes">CAT</property>
[*]                <attributes>
[*]                  <attribute name="weight" value="ultraheavy"/>
[*]                  <attribute name="scale" value="5.000000"/>
[*]                </attributes>
[*]              </object>
[*]            </child>
[*]          </object>
[*]          <packing>
[*]            <property name="position">0</property>
[*]          </packing>
[*]        </child>
[*]        <child>
[*]          <object class="GtkEntry" id="entry1">
[*]            <property name="visible">True</property>
[*]            <property name="can_focus">True</property>
[*]            <property name="has_focus">True</property>
[*]            <property name="can_default">True</property>
[*]            <property name="has_default">True</property>
[*]            <property name="receives_default">True</property>
[*]            <property name="max_length">16</property>
[*]            <property name="invisible_char">&#x2022;</property>
[*]            <property name="width_chars">16</property>
[*]            <property name="overwrite_mode">True</property>
[*]            <property name="caps_lock_warning">False</property>
[*]            <signal name="activate" handler="on_entry1_activate" after="yes"/>
[*]          </object>
[*]          <packing>
[*]            <property name="expand">False</property>
[*]            <property name="fill">False</property>
[*]            <property name="position">1</property>
[*]          </packing>
[*]        </child>
[*]      </object>
[*]    </child>
[*]  </object>
[*]</interface>
[*]'''
[*]        
[*]    def __init__(self):
[*]        self.builder=gtk.Builder()
[*]        self.load_gui()
[*]        self.builder.add_from_string(self.gui)

[*]        for w in self.builder.get_objects():
[*]            try:
[*]	        print w.name
[*]                exec "%s = %s" % ("self."+w.name,"self.builder.get_object(\""+w.name+"\")")
[*]            except:
[*]                pass

[*]        self.builder.connect_signals(self)
[*]        self.window1.fullscreen()
[*]    
[*]    def on_entry1_activate(self,widget): self.editlabel()
[*]    def on_window1_destroy(self,widget): gtk.main_quit()
[*]        
[*]if __name__ == "__main__":         
[*]    CS = colorsplash()
[*]    CS.window1.show()
[*]    gtk.main()
[/LIST]
```

---

### Post by ziekfiguur on 2011-08-24
Are you using different versions of PyGTK? if ubuntu 10.04 has a significantly newer version your code might use functions that don't work anymore.

---

### Post by Arndt on 2011-08-24
> **Legend1222 said:**
> I'm revisiting an old Python program. I am not an expert by any means. Slightly above novice. This program uses GTK Builder, but I don't think thats my issue (entire program below).

This program works fine on Jaunty (9.04), which is what it was originally written on. It does not work on 10.04 (haven't tried later versions). I can pin down the problem, but I don't understand it. Hopefully someone can explain it to me.

Jauntys version of python is 2.6.2, Lucids is 2.6.5.

The line of the code that describes the problem is in the __init__ section, where it says "print w.name" (line 86 below). Thats solely in there for debugging purposes. Nothing else has been changed. When the program runs on Jaunty, you get a list of the objects in the glade file: window1, vbox1, eventbox1, label1, and entry1. On Lucid you get: None, None, None, None and None. With w.name coming out as None, the exec line of the code (line 87) fails and therefore no GUI.

I've checked dependencies, I really don't think i'm missing anything. I doubt python changed that much in 0.0.3 releases, but i'm starting to wonder. name is stilled listed as an attribute, but I don't get why its not being populated.

Any ideas and help would be greatly appreciated. This is driving me nuts.

```
[LIST=1]
[*]#! /usr/bin/env python
[*]# -*- coding: utf-8 -*-

[*]import sys

[*]try:
[*]    import gtk
[*]except:
[*]    print "GTK missing or cannot be found"
[*]    sys.exit(1)
[*]    
[*]class colorsplash:
[*]    gui=''
[*]    
[*]    def editlabel(self):
[*]        label=self.entry1.get_text().upper()
[*]        if label == "MONKEY":
[*]            label="Stuffed Monkey"
[*]            color="GRAY"
[*]        elif label == "QUIT": gtk.main_quit()
[*]        else: 
[*]            label = "RE-SCAN"
[*]            color="BLUE"
[*]        self.label1.set_text(label)
[*]        self.eventbox1.modify_bg(gtk.STATE_NORMAL, gtk.gdk.color_parse(color))
[*]        self.entry1.set_text('')
[*]        
[*]    def load_gui(self): 
[*]        self.gui='''
[*]<?xml version="1.0"?>
[*]<interface>
[*]  <requires lib="gtk+" version="2.16"/>
[*]  <!-- interface-naming-policy project-wide -->
[*]  <object class="GtkWindow" id="window1">
[*]    <property name="window_position">center</property>
[*]    <signal name="destroy" handler="on_window1_destroy"/>
[*]    <child>
[*]      <object class="GtkVBox" id="vbox1">
[*]        <property name="visible">True</property>
[*]        <property name="orientation">vertical</property>
[*]        <child>
[*]          <object class="GtkEventBox" id="eventbox1">
[*]            <property name="visible">True</property>
[*]            <child>
[*]              <object class="GtkLabel" id="label1">
[*]                <property name="visible">True</property>
[*]                <property name="label" translatable="yes">CAT</property>
[*]                <attributes>
[*]                  <attribute name="weight" value="ultraheavy"/>
[*]                  <attribute name="scale" value="5.000000"/>
[*]                </attributes>
[*]              </object>
[*]            </child>
[*]          </object>
[*]          <packing>
[*]            <property name="position">0</property>
[*]          </packing>
[*]        </child>
[*]        <child>
[*]          <object class="GtkEntry" id="entry1">
[*]            <property name="visible">True</property>
[*]            <property name="can_focus">True</property>
[*]            <property name="has_focus">True</property>
[*]            <property name="can_default">True</property>
[*]            <property name="has_default">True</property>
[*]            <property name="receives_default">True</property>
[*]            <property name="max_length">16</property>
[*]            <property name="invisible_char">&#x2022;</property>
[*]            <property name="width_chars">16</property>
[*]            <property name="overwrite_mode">True</property>
[*]            <property name="caps_lock_warning">False</property>
[*]            <signal name="activate" handler="on_entry1_activate" after="yes"/>
[*]          </object>
[*]          <packing>
[*]            <property name="expand">False</property>
[*]            <property name="fill">False</property>
[*]            <property name="position">1</property>
[*]          </packing>
[*]        </child>
[*]      </object>
[*]    </child>
[*]  </object>
[*]</interface>
[*]'''
[*]        
[*]    def __init__(self):
[*]        self.builder=gtk.Builder()
[*]        self.load_gui()
[*]        self.builder.add_from_string(self.gui)

[*]        for w in self.builder.get_objects():
[*]            try:
[*]	        print w.name
[*]                exec "%s = %s" % ("self."+w.name,"self.builder.get_object(\""+w.name+"\")")
[*]            except:
[*]                pass

[*]        self.builder.connect_signals(self)
[*]        self.window1.fullscreen()
[*]    
[*]    def on_entry1_activate(self,widget): self.editlabel()
[*]    def on_window1_destroy(self,widget): gtk.main_quit()
[*]        
[*]if __name__ == "__main__":         
[*]    CS = colorsplash()
[*]    CS.window1.show()
[*]    gtk.main()
[/LIST]
```

A wild guess - I haven't used this GUI builder - could it be that the XML document needs a namespace, and previous versions were more lenient and didn't insist on one?

---

### Post by Legend1222 on 2011-08-30
> **ziekfiguur said:**
> Are you using different versions of PyGTK? if ubuntu 10.04 has a significantly newer version your code might use functions that don't work anymore.

The PyGTK versions were not the same, but minor version changes as well. I appreciate the suggestion. 

Arndt, I appreciate your suggestion as well. I haven't had a chance to experiment with it. This clients customer upped the priority and  felt that this was something that needed to be in place almost immediately. I didn't have time to screw around and figure out what the issue was like I thought I would, so I just gave up and rewrote it in Gambas (Visual Basic). Down and dirty, but it kept my clients customer happy.

Thanks again. If I ever get the time to revisit it, i'll try to post a follow up for the curious.

---

### Post by gmargo on 2011-08-30
Please don't post code with embedded line numbers like that.  Or is it a list?  It was impossible to copy without losing all the indentation.

Prominent in the [gtk.Builder]("http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html") documentation is this bit:
> 
Prior to GTK+ 2.20, [gtk.Builder]("http://www.pygtk.org/docs/pygtk/class-gtkbuilder.html")                 was setting the "name" property of constructed widgets to the "id" attribute. In GTK+ 2.20 or newer, you                 have to use [gtk.Buildable.get_name]("http://www.pygtk.org/docs/pygtk/class-gtkbuildable.html#method-gtkbuildable--set-name")()                 instead of [gtk.Widget.get_name]("http://www.pygtk.org/docs/pygtk/class-gtkwidget.html#method-gtkwidget--get-name")()                 to obtain the "id", or set the "name" property in your UI definition.             
So instead of **w.name** you must use **gtk.Buildable.get_name(w)**.

---

### Post by Arndt on 2011-08-30
> **gmargo said:**
> Please don't post code with embedded line numbers like that.  Or is it a list?  It was impossible to copy without losing all the indentation.


Maybe a little awkward, but not impossible. Start to post a reply to the original post, and you'll see that all lines start with [*]. Simply remove that string.

---

