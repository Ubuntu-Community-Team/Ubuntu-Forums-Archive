---
title: "A little question about pyGTK and packing"
date: 2008-09-14
forum: Programming Talk
---

### Post by mee.six on 2008-09-14
Hello,

[INDENT]I'm new to python and I'm new to GTK and I'm trying to write my own twitter client. Python is great, it's really easy to learn, but I get a little problem with packing. That's what I'm doing:
```

		self.window.set_border_width(0)
 		self.container = gtk.ScrolledWindow(); 	
		self.container.set_policy(gtk.POLICY_AUTOMATIC, gtk.POLICY_AUTOMATIC)
		self.vbox = gtk.VBox(False,False)
		
		self.container.add_with_viewport(self.vbox)
		self.window.add(self.container)
		self.container.show()
		self.vbox.show()
		self.window.show()
```
...
and then, in code
```

for s in statuses:			
			label = gtk.Label()		
			label.set_text(s.user.name+" : "+unicode(s.text));
			hbox = gtk.HBox(True, True)
			
			image = gtk.Image()			
# Image handling stuff
			image.show()

			label.set_justify(gtk.JUSTIFY_LEFT)
			label.set_line_wrap(True)
			label.show()	
			table = gtk.HBox(False, 0)
			table.pack_start(image, False, False, 0);
			table.pack_start(label, True,True,0);		
			table.show()
			separator = gtk.HSeparator()
			separator.show()
			self.vbox.pack_start(separator)
			self.vbox.pack_start(table)
```

And here is the thing I'm getting:

[[IMG]http://4hq.org/thumb/jbl1221428717t.png[/IMG]](http://4hq.org/jbl1221428717t.png.html)

Moreover, the HBoxes width is about 400px, so, when I set window's width to,say, 300px, I get a horizontal bar, instead of panel resizing, though I do not set hboxes width anywhere.

Can anyone tell me, how to do this right?
thanks in advance :)
[/INDENT]

---

### Post by kknd on 2008-09-14
A tip is to use Glade to learn how packing works (don't need to use it in your application, just try changing the properties in it).

---

### Post by days_of_ruin on 2008-09-15
This doesn't answer your question but you should just do "self.window.show_all()".Its a whole lot simpler.

Try this to the labels:
```
label.set_alignment(0.10,0.50)
```

---

### Post by mee.six on 2008-09-15
Well, thanks, but that is actually what I was doing. Here is the Glade XML:

```

	<widget class="GtkViewport" id="viewport1">
	  <property name="visible">True</property>
	  <property name="shadow_type">GTK_SHADOW_IN</property>

	  <child>
	    <widget class="GtkVBox" id="vbox1">
	      <property name="visible">True</property>
	      <property name="homogeneous">False</property>
	      <property name="spacing">0</property>

	      <child>
		<widget class="GtkHBox" id="hbox1">
		  <property name="visible">True</property>
		  <property name="homogeneous">False</property>
		  <property name="spacing">0</property>

		  <child>
		    <widget class="GtkImage" id="image1">
		      <property name="visible">True</property>
		      <property name="pixbuf">14059952.jpg</property>
		      <property name="xalign">0.5</property>
		      <property name="yalign">0.5</property>
		      <property name="xpad">0</property>
		      <property name="ypad">0</property>
		    </widget>
		    <packing>
		      <property name="padding">0</property>
		      <property name="expand">False</property>
		      <property name="fill">False</property>
		    </packing>
		  </child>

		  <child>
		    <widget class="GtkScrolledWindow" id="scrolledwindow2">
		      <property name="visible">True</property>
		      <property name="can_focus">True</property>
		      <property name="hscrollbar_policy">GTK_POLICY_ALWAYS</property>
		      <property name="vscrollbar_policy">GTK_POLICY_ALWAYS</property>
		      <property name="shadow_type">GTK_SHADOW_IN</property>
		      <property name="window_placement">GTK_CORNER_TOP_LEFT</property>

		      <child>
			<widget class="GtkTextView" id="textview1">
			  <property name="visible">True</property>
			  <property name="can_focus">True</property>
			  <property name="editable">True</property>
			  <property name="overwrite">False</property>
			  <property name="accepts_tab">True</property>
			  <property name="justification">GTK_JUSTIFY_LEFT</property>
			  <property name="wrap_mode">GTK_WRAP_NONE</property>
			  <property name="cursor_visible">True</property>
			  <property name="pixels_above_lines">0</property>
			  <property name="pixels_below_lines">0</property>
			  <property name="pixels_inside_wrap">0</property>
			  <property name="left_margin">0</property>
			  <property name="right_margin">0</property>
			  <property name="indent">0</property>
			  <property name="text" translatable="yes"></property>
			</widget>
		      </child>
		    </widget>
		    <packing>
		      <property name="padding">0</property>
		      <property name="expand">True</property>
		      <property name="fill">True</property>
		    </packing>
		  </child>
		</widget>
		<packing>
		  <property name="padding">0</property>
		  <property name="expand">True</property>
		  <property name="fill">True</property>
		</packing>
	      </child>


```

---

### Post by mee.six on 2008-09-15
> **days_of_ruin said:**
> This doesn't answer your question but you should just do "self.window.show_all()".Its a whole lot simpler.

Try this to the labels:
```
label.set_alignment(0.10,0.50)
```

Oh...thanks! :) Yeah, that helped a lot!! Everything's Ok now, and I should read some docs about this set_alignment method :)
One more thanks :)

---

