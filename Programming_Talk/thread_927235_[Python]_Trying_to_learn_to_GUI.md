---
title: "[Python] Trying to learn to GUI"
date: 2008-09-22
forum: Programming Talk
---

### Post by dodle on 2008-09-22
Does anybody know of a good tutorial for glade and pygtk.  I've seen a few but none that I found to be all that great.  I'll show you my scripts in case anybody wants to help me out here.[PHP]#!/usr/bin/env python

import sys
try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
except:
	sys.exit(1)

class MyGame:


	def __init__(self):
		
		#Set the Glade file
		self.gladefile = "MyGame.glade"  
	        self.wTree = gtk.glade.XML(self.gladefile) 
		
		#Create our dictionay and connect it
		dic = { "on_button_north_clicked" : self.button_north_clicked,
            "on_button_east_clicked" : self.button_east_clicked,
            "on_button_west_clicked" : self.button_west_clicked,
            "on_button_south_clicked" : self.button_south_clicked,
            "on_window_destroy" : gtk.main_quit }
		self.wTree.signal_autoconnect(dic)

	def button_north_clicked(self, widget):
		print "North"
        
	def button_east_clicked(self, widget):
		print "East"

	def button_west_clicked(self, widget):
		print "West"

	def button_south_clicked(self, widget):
		print "South"
print "what would you like to do?"



if __name__ == "__main__":
	hwg = MyGame()
	gtk.main()[/PHP]Here is the Glade file:```
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.3 on Mon Sep 22 16:18:39 2008 -->
<glade-interface>
  <widget class="GtkWindow" id="window">
    <property name="width_request">253</property>
    <property name="height_request">215</property>
    <property name="visible">True</property>
    <property name="resizable">False</property>
    <property name="default_width">494</property>
    <signal name="destroy" handler="on_window_destroy"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkImage" id="image">
            <property name="visible">True</property>
            <signal name="button_press_event" handler="on_image_button_press_event"/>
          </widget>
        </child>
        <child>
          <widget class="GtkVBox" id="vbox2">
            <property name="visible">True</property>
            <child>
              <widget class="GtkHBox" id="hbox2">
                <property name="visible">True</property>
                <property name="homogeneous">True</property>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <widget class="GtkButton" id="button_north">
                    <property name="width_request">40</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="label" translatable="yes">North</property>
                    <property name="response_id">0</property>
                    <signal name="clicked" handler="on_button_north_clicked"/>
                  </widget>
                  <packing>
                    <property name="expand">False</property>
                    <property name="fill">False</property>
                    <property name="position">1</property>
                  </packing>
                </child>
                <child>
                  <placeholder/>
                </child>
              </widget>
            </child>
            <child>
              <widget class="GtkHBox" id="hbox1">
                <property name="visible">True</property>
                <child>
                  <widget class="GtkButton" id="button_west">
                    <property name="width_request">40</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="label" translatable="yes">West</property>
                    <property name="response_id">0</property>
                    <signal name="clicked" handler="on_button_west_clicked"/>
                  </widget>
                  <packing>
                    <property name="fill">False</property>
                  </packing>
                </child>
                <child>
                  <widget class="GtkButton" id="button_east">
                    <property name="width_request">40</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="label" translatable="yes">East</property>
                    <property name="response_id">0</property>
                    <signal name="clicked" handler="on_button_east_clicked"/>
                  </widget>
                  <packing>
                    <property name="fill">False</property>
                    <property name="position">1</property>
                  </packing>
                </child>
              </widget>
              <packing>
                <property name="padding">3</property>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <widget class="GtkHBox" id="hbox3">
                <property name="visible">True</property>
                <property name="homogeneous">True</property>
                <child>
                  <placeholder/>
                </child>
                <child>
                  <widget class="GtkButton" id="button_south">
                    <property name="width_request">40</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <property name="label" translatable="yes">South</property>
                    <property name="response_id">0</property>
                    <signal name="clicked" handler="on_button_south_clicked"/>
                  </widget>
                  <packing>
                    <property name="fill">False</property>
                    <property name="position">1</property>
                  </packing>
                </child>
                <child>
                  <placeholder/>
                </child>
              </widget>
              <packing>
                <property name="expand">False</property>
                <property name="position">2</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="position">1</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```What I would like to do, instead of having each button print to the command line, is have a graphical representation in the upper portion of the gui,  Maybe just a little square that moves one space in the direction of the button pushed.

---

### Post by gomputor on 2008-09-22
First of all, watch your identation: :)
```

try:
     import pygtk
      pygtk.require("2.0")   <----------- here
except:
      pass
try:
    import gtk
      import gtk.glade       <----------- here
except:

        #Set the Glade file
        self.gladefile = "MyGame.glade"  
            self.wTree = gtk.glade.XML(self.gladefile)  <-------and here 

```

Second: If you wanna make your window none-resizable, then you don't have to drop any container box in the window.
Just drop a fixed widget inside the window and make both width and hight request (on the common tab) the same for both the window and the fixed widget. Then position and resize your buttons where you want to, after clicking first the Drag Resize button on the glade toolbar.

See this glade file to figure out what's going on. Use it with your .py file, you don't have to change anything in your code:
```

<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Tue Sep 23 03:26:28 2008 -->
<glade-interface>
  <widget class="GtkWindow" id="window">
    <property name="width_request">300</property>
    <property name="height_request">250</property>
    <property name="visible">True</property>
    <property name="resizable">False</property>
    <property name="window_position">GTK_WIN_POS_CENTER</property>
    <signal name="destroy" handler="on_window_destroy"/>
    <child>
      <widget class="GtkFixed" id="fixed1">
        <property name="width_request">300</property>
        <property name="height_request">250</property>
        <property name="visible">True</property>
        <child>
          <widget class="GtkButton" id="button_north">
            <property name="width_request">60</property>
            <property name="height_request">40</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="label" translatable="yes">North</property>
            <property name="response_id">0</property>
            <signal name="clicked" handler="on_button_north_clicked"/>
          </widget>
          <packing>
            <property name="x">118</property>
            <property name="y">129</property>
          </packing>
        </child>
        <child>
          <widget class="GtkButton" id="button_west">
            <property name="width_request">60</property>
            <property name="height_request">40</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="label" translatable="yes">West</property>
            <property name="response_id">0</property>
            <signal name="clicked" handler="on_button_west_clicked"/>
          </widget>
          <packing>
            <property name="x">42</property>
            <property name="y">168</property>
          </packing>
        </child>
        <child>
          <widget class="GtkButton" id="button_east">
            <property name="width_request">60</property>
            <property name="height_request">40</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="label" translatable="yes">East</property>
            <property name="response_id">0</property>
            <signal name="clicked" handler="on_button_east_clicked"/>
          </widget>
          <packing>
            <property name="x">194</property>
            <property name="y">167</property>
          </packing>
        </child>
        <child>
          <widget class="GtkButton" id="button_south">
            <property name="width_request">60</property>
            <property name="height_request">40</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="receives_default">True</property>
            <property name="label" translatable="yes">South</property>
            <property name="response_id">0</property>
            <signal name="clicked" handler="on_button_south_clicked"/>
          </widget>
          <packing>
            <property name="x">118</property>
            <property name="y">205</property>
          </packing>
        </child>
        <child>
          <widget class="GtkImage" id="image">
            <property name="width_request">33</property>
            <property name="height_request">30</property>
            <property name="visible">True</property>
            <property name="stock">gtk-media-record</property>
          </widget>
          <packing>
            <property name="x">131</property>
            <property name="y">55</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>

```

Now as for moving any widget in a new position, this might be a little bit complicated because you'll need redrawing and things like that. I'm no expert, I'm just a beginner myself, so don't take my words for granted about this.
See this article here [http://www.learningpython.com/2006/07/25/writing-a-custom-widget-using-pygtk/]("http://www.learningpython.com/2006/07/25/writing-a-custom-widget-using-pygtk/") if it can help you.

But I think after all that if you wanna dive into gaming with python, then why not try Pygame? [http://www.pygame.org/news.html]("http://www.pygame.org/news.html")

:)

---

### Post by dodle on 2008-09-24
Okay, how about this:  Instead of the upper area displaying a graphic, use a text area and have the words print out in the text area when the button is pressed, instead of the console.  If I can just get past this step, I think I will start progressing a little faster.

---

### Post by gomputor on 2008-09-24
> **dodle said:**
> Okay, how about this:  Instead of the upper area displaying a graphic, use a text area and have the words print out in the text area when the button is pressed, instead of the console.  If I can just get past this step, I think I will start progressing a little faster.

Put a TextEntry in your window and name it like 'textentry1'.
Then define it in your __init__ method like this:
[PHP]self.textentry1 = self.wTree.get_widget("textentry1")[/PHP]
(put it below the [COLOR="DimGray"]self.wTree.signal_autoconnect(dic)[/COLOR])

And change your buttons functions accordingly:
[PHP]def button_north_clicked(self, widget):
    self.textentry1.set_text('Go North')
[/PHP]
and the rest...

---

### Post by dodle on 2008-09-24
Edit: I don't know why it's showing those extra indents, when I copy and paste from the source file they aren't there.  

[PHP]import sys
try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
except:
	sys.exit(1)


class ButtonText:
    def __init__(self):
        self.gladefile = "button-text.glade"
        self.wTree  = gtk.glade.XML(self.gladefile)
        
        dic = {"on_button_clicked" : self.button_clicked,
        "on_window_destroy" : gtk.main_quit}
        self.wTree.signal_autoconnect(dic)
        self.text = self.wTree.get_widget('text')
        
    def button_clicked(self, widget):
        self.text.set_text('Yay! It printed')

if __name__ == "__main__":
    hwg = ButtonText()
    gtk.main()[/PHP]

I get the following error:
```
AttributeError:  'gtk.TextView' object has no attribute 'set_text'
```

---

### Post by ankursethi on 2008-09-24
There's a full PyGTK tutorial at their official website ([http://pygtk.org](http://pygtk.org)). Direct link : [http://pygtk.org/pygtk2tutorial/index.html](http://pygtk.org/pygtk2tutorial/index.html)

No idea about the Glade tutorial, though. Even I've been looking for one.

---

### Post by gomputor on 2008-09-24
> **dodle said:**
> Edit: I don't know why it's showing those extra indents, when I copy and paste from the source file they aren't there.  

Because with the copy-paste you have now in your file a mixture of Tabs and Spaces. Either convert them all to Tabs or to Spaces (the best.)

> **dodle said:**
> 
I get the following error:
```
AttributeError:  'gtk.TextView' object has no attribute 'set_text'
```

You get the AttributeError because you are using a gtk.TextView and not a gtk.Entry as I wrote (but maybe it's my mistake, 'cause I wrote TextEntry. But that's what it is, a Text Entry.)
gtk.TextView and gtk.Entry have different methods for getting and setting text. You use the TextView mostly if you want let's say to make a text editor or something like that. For now use a gtk.Entry and play with that.
And read the pyGtk docs and the tutorial.
Reference here:
[http://www.pygtk.org/docs/pygtk/index.html]("http://www.pygtk.org/docs/pygtk/index.html")
Tutorial here:
[http://www.pygtk.org/pygtk2tutorial/index.html]("http://www.pygtk.org/pygtk2tutorial/index.html")
See also here for a tutorial with glade and gtkBuilder:
[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---

