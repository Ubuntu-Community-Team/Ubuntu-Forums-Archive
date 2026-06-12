---
title: "Python Icon problem"
date: 2010-08-22
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-22
```

 ./clockgui.py:9: GtkWarning: gtk_image_set_from_icon_name: assertion `GTK_IS_IMAGE (image)' failed
  self.wTree.add_from_file("clockgui.glade")

```

I'm trying to add a volume control to the Glade GUI of my Python speaking clock app. It seems to all be working but it just won't show the icon :(
I get above error message and can't work out how to include the icons. If anyone wants to have a look here is my glade file and a stripped down version of my Python script...
```

#!/usr/bin/python
import pygtk
import gtk
import gtk.glade

class ClockGUI:
	def __init__(self):
		self.wTree = gtk.Builder()
		self.wTree.add_from_file("clockgui.glade")

		self.window = self.wTree.get_object("window1")
		# terminate the loop when main window is destroyed
		self.window.connect("destroy", gtk.main_quit)

gui = ClockGUI()
gtk.main()

```
clockgui.glade:
```

<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window1">
    <property name="visible">True</property>
    <child>
      <object class="GtkVolumeButton" id="volumebutton1">
        <property name="label">gnome-stock-volume</property>
        <property name="visible">True</property>
        <property name="can_focus">True</property>
        <property name="receives_default">True</property>
        <property name="has_tooltip">True</property>
        <property name="relief">none</property>
        <property name="use_stock">True</property>
        <property name="focus_on_click">False</property>
        <property name="orientation">vertical</property>
        <property name="size">large-toolbar</property>
        <property name="icons">audio-volume-muted
audio-volume-high
audio-volume-low
audio-volume-medium</property>
      </object>
    </child>
  </object>
  <object class="GtkAdjustment" id="adjustment1">
    <property name="upper">59</property>
    <property name="step_increment">1</property>
  </object>
</interface>

```

Thanks in advance for any feedback :)

p.s. also thanks for pointing out my typo... the above file was not clock.glade, but clockgui.glade

---

### Post by surfer on 2010-08-22
did you save the file as clock.glade (as you have titled the xml in your post) or clockgui.glade (the file you read in with python)?

---

### Post by StephenF on 2010-08-22
I commented out the label line in the XML file and it works.

In glade I chose Add Custom Button Content for the same effect.

---

### Post by worksofcraft on 2010-08-22
> **StephenF said:**
> I commented out the label line in the XML file and it works.

In glade I chose Add Custom Button Content for the same effect.

Thanks for that :)
It does leave me wondering how is one supposed to use any of the stock buttons though? :confused:

---

### Post by StephenF on 2010-08-22
You use the more regular buttons exactly the way you think you do. The volume button is special since it manages it's own icons unless you go and override them (which you did).

The reason no icon appeared is due to a recent style change (can't be bothered researching which version) where icon+text is now just text. If you want a stock icon you'll have to select it as stock for an image and embed that.

---

### Post by juancarlospaco on 2010-08-22
i allways embebed the icons on the .py file using base64 :)
*good luckz*

---

