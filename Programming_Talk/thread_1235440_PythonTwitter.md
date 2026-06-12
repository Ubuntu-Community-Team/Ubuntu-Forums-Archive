---
title: "Python/Twitter"
date: 2009-08-09
forum: Programming Talk
---

### Post by matmatmat on 2009-08-09
Below is the twitter client I am trying to make, but when you click the button in the third tab it says:
```

Traceback (most recent call last):
  File "mtweet.py", line 34, in public
    textbuffer.insert_at_cursor(name.user.name + '\n' + name.user.text + '\n\n')
AttributeError: 'User' object has no attribute 'text'

```
I how could I get the status?


python file:
```

# -*- coding: utf-8 -*-

import sys
import gtk
import twitter, subprocess, time
  
class mTweet:
 
    def destroy(self, widget, data=None):
        gtk.main_quit()
	sys.exit()

    def redo(self, text):
	self.st.set_text(" " + text)

    def post(self, widget, data=None):        
	textbuffer = self.textview.get_buffer()
	t = textbuffer.get_text(textbuffer.get_start_iter(), textbuffer.get_end_iter())
	self.client.PostUpdate(t)
	self.redo(t)

    def update(self, widget, data=None):        
	textbuffer = self.textview2.get_buffer()
	lists = self.client.GetFriends()
	textbuffer.set_text("")
	for name in lists:
		textbuffer.insert_at_cursor(name.name + '\n' + name.status.text + '\n\n')

    def public(self, widget, data=None):        
	textbuffer = self.textview2.get_buffer()
	lists = self.client.GetPublicTimeline()
	textbuffer.set_text("")
	for name in lists:
		textbuffer.insert_at_cursor(name.user.name + '\n' + name.user.text + '\n\n')
     
    def __init__(self):
	self.client = twitter.Api("pymatio", "######")    
        builder = gtk.Builder()
        builder.add_from_file("mtweet.glade")         
        self.window = builder.get_object("window1")
	self.textview = builder.get_object("text")
	self.textview2 = builder.get_object("text2")
	self.st = builder.get_object("st")
	self.user = self.client.GetUser("pymatio")
	self.st.set_text(" " + self.user.status.text)
        builder.connect_signals(self)       
    
if __name__ == "__main__":
    m = mTweet()
    m.window.show()
    gtk.main()

```

glade file:
```

<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkWindow" id="window1">
    <property name="default_width">300</property>
    <property name="default_height">300</property>
    <signal name="destroy_event" handler="destroy"/>
    <child>
      <object class="GtkNotebook" id="notebook1">
        <property name="visible">True</property>
        <property name="can_focus">True</property>
        <child>
          <object class="GtkVBox" id="vbox1">
            <property name="visible">True</property>
            <property name="orientation">vertical</property>
            <child>
              <object class="GtkHBox" id="hbox1">
                <property name="visible">True</property>
                <child>
                  <object class="GtkLabel" id="label2">
                    <property name="visible">True</property>
                    <property name="label" translatable="yes">Current Status:</property>
                  </object>
                  <packing>
                    <property name="position">0</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkLabel" id="st">
                    <property name="visible">True</property>
                  </object>
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
              </object>
              <packing>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkTextView" id="text">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
            <child>
              <object class="GtkHBox" id="hbox2">
                <property name="visible">True</property>
                <child>
                  <object class="GtkButton" id="button1">
                    <property name="label" translatable="yes">Post</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <signal name="clicked" handler="post"/>
                  </object>
                  <packing>
                    <property name="position">0</property>
                  </packing>
                </child>
                <child>
                  <object class="GtkButton" id="button2">
                    <property name="label" translatable="yes">Quit</property>
                    <property name="visible">True</property>
                    <property name="can_focus">True</property>
                    <property name="receives_default">True</property>
                    <signal name="clicked" handler="destroy"/>
                  </object>
                  <packing>
                    <property name="position">1</property>
                  </packing>
                </child>
              </object>
              <packing>
                <property name="position">2</property>
              </packing>
            </child>
          </object>
        </child>
        <child type="tab">
          <object class="GtkLabel" id="label1">
            <property name="visible">True</property>
            <property name="label" translatable="yes">You</property>
          </object>
          <packing>
            <property name="tab_fill">False</property>
          </packing>
        </child>
        <child>
          <object class="GtkVBox" id="vbox2">
            <property name="visible">True</property>
            <property name="orientation">vertical</property>
            <child>
              <object class="GtkTextView" id="text2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </object>
              <packing>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="button3">
                <property name="label" translatable="yes">Update</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <signal name="clicked" handler="update"/>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child type="tab">
          <object class="GtkLabel" id="Friends">
            <property name="visible">True</property>
            <property name="label" translatable="yes">Friends</property>
          </object>
          <packing>
            <property name="position">1</property>
            <property name="tab_fill">False</property>
          </packing>
        </child>
        <child>
          <object class="GtkVBox" id="vbox3">
            <property name="visible">True</property>
            <property name="orientation">vertical</property>
            <child>
              <object class="GtkTextView" id="textview1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </object>
              <packing>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="button4">
                <property name="label" translatable="yes">Update</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <signal name="clicked" handler="public"/>
              </object>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
        <child type="tab">
          <object class="GtkLabel" id="label3">
            <property name="visible">True</property>
            <property name="label" translatable="yes">Public</property>
          </object>
          <packing>
            <property name="position">2</property>
            <property name="tab_fill">False</property>
          </packing>
        </child>
      </object>
    </child>
  </object>
</interface>

```

---

### Post by Martin Witte on 2009-08-09
The [documentation ]("http://static.unto.net/python-twitter/0.6/doc/twitter.html#User") for the Python twitter module doesn't specify a method text for a User object, when you use it you get an error like you have.

See as example:

```
martin@sony:~$ cat test.py
#!/usr/bin/env python
class A(object):
    def __init__(self):
        self.attribute = "A value"

a = A()
print a.attribute
print a.not_existing_attribute
martin@sony:~$ ./test.py
A value
Traceback (most recent call last):
  File "./test.py", line 8, in <module>
    print a.not_existing_attribute
AttributeError: 'A' object has no attribute 'not_existing_attribute'
martin@sony:~$ 

```

---

### Post by matmatmat on 2009-08-09
I ended up fixing it

---

