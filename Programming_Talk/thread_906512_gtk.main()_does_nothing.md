---
title: "gtk.main() does nothing?"
date: 2008-08-31
forum: Programming Talk
---

### Post by Martje_001 on 2008-08-31
Hello,
I've build a glade file and a python one, but when I run the python file, nothing happens!

**pyhelloworld.glade:**
```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Sun Aug 31 20:28:23 2008 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <signal name="destroy" handler="on_window1_destroy"/>
    <child>
      <widget class="GtkLabel" id="label1">
        <property name="visible">True</property>
        <property name="label" translatable="yes">Hello world!</property>
        <property name="justify">GTK_JUSTIFY_CENTER</property>
      </widget>
    </child>
  </widget>
</glade-interface>
```

**PyHelloWorld.py:**
```
#!/usr/bin/python
import gtk
import gtk.glade
import gnome.ui

def DestroyFunction(obj):
	gtk.main_quit()

widgetTree = gtk.glade.XML("pyhelloworld.glade")

dic = { "on_window1_destroy" : DestroyFunction }

widgetTree.signal_autoconnect (dic)

gtk.main()

```
Anyone, please?

---

### Post by kknd on 2008-08-31
You need to get a ref to the window, and show it (window.showAll() to show the children too)

---

### Post by Martje_001 on 2008-08-31
I'm a complete newbie. Could you tell me how to do this?

---

### Post by kknd on 2008-08-31
In pseudocode:

Glade xml = Glade.load("file")
Window w = xml:getWidget("yourwidgetname")
w:showAll()

---

### Post by Martje_001 on 2008-09-01
Thank you, but the problem was:

**<property name="visible">True</property>**

---

### Post by kknd on 2008-09-01
> **Martje_001 said:**
> Thank you, but the problem was:

**<property name="visible">True</property>**

Nice. The show method would set the property visible to TRUE too =).

---

