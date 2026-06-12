---
title: "Help with Python"
date: 2010-10-22
forum: Programming Talk
---

### Post by frt975 on 2010-10-22
I'm trying to learn python by using this tutorial but no errors or windows appear.
pygtkmozembed.glade
```
<?xml version="1.0" encoding="UTF-8"?>
<glade-interface>
  <!-- interface-requires gtk+ 2.16 -->
  <!-- interface-naming-policy project-wide -->
  <widget class="GtkWindow" id="window1">
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkToolbar" id="toolbar1">
            <property name="visible">True</property>
            <child>
              <widget class="GtkToolButton" id="_Back">
                <property name="visible">True</property>
                <property name="label" translatable="yes">_Back</property>
                <property name="use_underline">True</property>
                <property name="stock_id">gtk-go-back</property>
              </widget>
              <packing>
                <property name="expand">True</property>
              </packing>
            </child>
            <child>
              <widget class="GtkToolButton" id=" _Foward">
                <property name="visible">True</property>
                <property name="label" translatable="yes"> Foward</property>
                <property name="use_underline">True</property>
                <property name="stock_id">gtk-go-forward</property>
              </widget>
              <packing>
                <property name="expand">True</property>
              </packing>
            </child>
            <child>
              <widget class="GtkToolItem" id=" ">
                <property name="visible">True</property>
                <child>
                  <widget class="GtkEntry" id="entry1">
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="invisible_char">•</property>
                  </widget>
                </child>
              </widget>
              <packing>
                <property name="expand">True</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="padding">1</property>
            <property name="position">0</property>
          </packing>
        </child>
        <child>
          <widget class="GtkFrame" id="frame1">
            <property name="visible">True</property>
            <property name="label_xalign">0</property>
            <property name="shadow_type">none</property>
            <child>
              <placeholder/>
            </child>
            <child>
              <placeholder/>
              <packing>
                <property name="type">label_item</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>
```
pygtkmozembed.py
```
#!/usr/bin/env python

import gtk
import gnome.ui
import gtk.glade
import gtkmozembed

APPNAME="PyGtkMozEmbed"
APPVERSION="0.1"

class WidgetsWrapper:
    def __init__(self):
        gnome.init(APPNAME, APPVERSION)
        self.widgets = gtk.glade.XML("pygtkmozembed.glade")
        self.mozillaWidget = gtkmozembed.MozEmbed()
        self.widgets.get_widget("frame1").add(self.mozillaWidget)
        self.mozillaWidget.set_size_request(800,600)
        self.mozillaWidget.show()
        self.mozillaWidget.load_url("http://www.mozilla.org/")

        signalDic = { "on_entry1_activate" : self.on_entry1_activate,
                      "on_quit1_activate" : self.on_quit1_activate}
        self.widgets.signal_autoconnect(signalDic)
        
    def on_entry1_activate(self, widget):
        self.mozillaWidget.load_url(widget.get_text())
        
    def on_quit1_activate(self, widget):
        gtk.main_quit()
        
if __name__ == "__main__":
    widgets = WidgetsWrapper()
    gtk.main()
```

---

### Post by frt975 on 2010-10-24
[SIZE="6"][color="white"]bump[/color][/SIZE]

---

### Post by StephenF on 2010-10-24
I think you need to pull the window1 widget out and do a show_all() on it in the same manner as has been done with frame1.

---

### Post by frt975 on 2010-10-24
Could you say that so i can understand it? I don't understand anything you said because I'm just learning.

---

### Post by frt975 on 2010-10-26
never mind. After a bunch of googling this helped out: [http://ubuntuforums.org/showthread.php?t=389801](http://ubuntuforums.org/showthread.php?t=389801)

---

### Post by oldfred on 2010-10-26
What version of glade? Recent versions of glade save in the builder format which is different than the older glade format. File may still be glade.

How old is example?

builder
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)


Nevermind I now see you found some anwsers.

---

