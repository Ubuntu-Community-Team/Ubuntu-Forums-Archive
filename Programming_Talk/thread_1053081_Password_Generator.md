---
title: "Password Generator"
date: 2009-01-28
forum: Programming Talk
---

### Post by matmatmat on 2009-01-28
I've made a passwrd generator in python & pygtk:
[PHP]
#! /usr/bin/env python
# -*- coding: utf8 -*-
import sys
import gtk
from random import choice

class Passwrd_generator:
    def on_window1_destroy(self, widget, data=None):
        gtk.main_quit()
    
    def on_quit_clicked(self, widget, data=None):
		gtk.main_quit()
	
    def on_generate_clicked(self, widget, data=None):
		self.spin_value = int(self.spin.get_value())
		self.num = False
		self.letter = False
		self.sym = False
		self.random_str = ""
		self.passwrd = ""
		
		self.entry.set_text(self.passwrd)
		if self.spin_value == 0:
			self.entry.set_text("Please enter the length & additional info.")
			
		if self.numbers.get_active():
			self.num = True	
			self.random_str = self.random_str + "1234567890"
		
		if self.lett.get_active():
			self.letter = True
			self.random_str = self.random_str + "qwertyuiopasdfghjklzxcvbnm"
		
		if self.symbol.get_active():
			self.sym = True		
			self.random_str = self.random_str + "!$%^&*@#~"
		
		for i in range(0, self.spin_value):
			self.choice = choice(self.random_str.rstrip('\n'))
			self.passwrd = self.passwrd + self.choice
			self.entry.set_text(self.passwrd)
				
    def __init__(self):
    
        builder = gtk.Builder()
        builder.add_from_file("passwrd_ui.xml") 
        
        self.window = builder.get_object("window1")
        self.spin = builder.get_object("spin")
        self.numbers = builder.get_object("num")
        self.lett = builder.get_object("letters")
        self.symbol = builder.get_object("symbols")
        self.entry = builder.get_object("entry")
        builder.connect_signals(self)       
    
if __name__ == "__main__":
    generator = Passwrd_generator()
    generator.window.show()
    gtk.main()
[/PHP]
Glade file:
[PHP]
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Sat Jan 10 16:36:17 2009 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Password Generator</property>
    <signal name="destroy" handler="on_window1_destroy"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="label">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Password</property>
              </widget>
            </child>
            <child>
              <widget class="GtkEntry" id="entry">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
        </child>
        <child>
          <widget class="GtkSpinButton" id="spin">
            <property name="width_request">1</property>
            <property name="height_request">25</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="adjustment">0 0 100 1 10 10</property>
          </widget>
          <packing>
            <property name="expand">False</property>
            <property name="fill">False</property>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkCheckButton" id="num">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="label" translatable="yes">Numbers</property>
            <property name="response_id">0</property>
            <property name="draw_indicator">True</property>
          </widget>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
        <child>
          <widget class="GtkCheckButton" id="letters">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="label" translatable="yes">Letters</property>
            <property name="response_id">0</property>
            <property name="draw_indicator">True</property>
          </widget>
          <packing>
            <property name="position">3</property>
          </packing>
        </child>
        <child>
          <widget class="GtkCheckButton" id="symbols">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="label" translatable="yes">Symbols</property>
            <property name="response_id">0</property>
            <property name="draw_indicator">True</property>
          </widget>
          <packing>
            <property name="position">4</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox2">
            <property name="visible">True</property>
            <child>
              <widget class="GtkButton" id="generate">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Generate</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_generate_clicked"/>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="quit">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Quit</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_quit_clicked"/>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">5</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>
[/PHP]

and converting it to xml with:
[PHP]
gtk-builder-convert passwrd_ui.glade passwrd_ui.xml
[/PHP]

Any feedback would be appreciated (eg what features to add, cleaner code).

---

### Post by Sorivenul on 2009-01-28
I did something similar a while ago involving hashes, ciphers, and random passwords in Python with Tkinter.

It's a clean interface. And it serves its purpose. 

IMO, you should add a few labels to specify that the spinbutton sets the length of the generated password, and that the selections made will be the character sets used to generate the password. I, and I'm sure the other Pythonistas, will understand this from the code itself. However, as an end user, I would be a little confused. Overall, nice work.

---

### Post by matmatmat on 2009-01-28
Here's the new .glade file
[PHP]
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">
<!--Generated with glade3 3.4.5 on Wed Jan 28 17:42:00 2009 -->
<glade-interface>
  <widget class="GtkWindow" id="window1">
    <property name="visible">True</property>
    <property name="title" translatable="yes">Password Generator</property>
    <signal name="destroy" handler="on_window1_destroy"/>
    <child>
      <widget class="GtkVBox" id="vbox1">
        <property name="visible">True</property>
        <child>
          <widget class="GtkHBox" id="hbox1">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="label">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Password</property>
              </widget>
            </child>
            <child>
              <widget class="GtkEntry" id="entry">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox3">
            <property name="visible">True</property>
            <child>
              <widget class="GtkLabel" id="label1">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Length</property>
              </widget>
            </child>
            <child>
              <widget class="GtkSpinButton" id="spin">
                <property name="width_request">146</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="adjustment">0 0 100 1 10 10</property>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child>
          <widget class="GtkCheckButton" id="num">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="label" translatable="yes">Numbers</property>
            <property name="response_id">0</property>
            <property name="draw_indicator">True</property>
          </widget>
          <packing>
            <property name="position">2</property>
          </packing>
        </child>
        <child>
          <widget class="GtkCheckButton" id="letters">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="label" translatable="yes">Letters</property>
            <property name="response_id">0</property>
            <property name="draw_indicator">True</property>
          </widget>
          <packing>
            <property name="position">3</property>
          </packing>
        </child>
        <child>
          <widget class="GtkCheckButton" id="symbols">
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="label" translatable="yes">Symbols</property>
            <property name="response_id">0</property>
            <property name="draw_indicator">True</property>
          </widget>
          <packing>
            <property name="position">4</property>
          </packing>
        </child>
        <child>
          <widget class="GtkHBox" id="hbox2">
            <property name="visible">True</property>
            <child>
              <widget class="GtkButton" id="generate">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Generate</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_generate_clicked"/>
              </widget>
            </child>
            <child>
              <widget class="GtkButton" id="quit">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="label" translatable="yes">Quit</property>
                <property name="response_id">0</property>
                <signal name="clicked" handler="on_quit_clicked"/>
              </widget>
              <packing>
                <property name="position">1</property>
              </packing>
            </child>
          </widget>
          <packing>
            <property name="position">5</property>
          </packing>
        </child>
      </widget>
    </child>
  </widget>
</glade-interface>
[/PHP]

Thanks for the post, once again any feedback would be great!

---

### Post by Sorivenul on 2009-01-28
Good, simple addition. Maybe a "Password contents:" label somewhere near the list of possible password contents?

---

### Post by matmatmat on 2009-01-28
Anything else?

---

### Post by matmatmat on 2009-01-29
bump

---

### Post by matmatmat on 2009-01-29
I've created a launchpad site [here]("https://code.launchpad.net/passwrdgenerator"), mainly to try out launchpad! Please look & participate in the project (it's also a learning exercise - it would be good if beginners were able to learn, play & participate with the code & project)!

---

### Post by matmatmat on 2009-01-29
Is there a way I could extend this?

---

### Post by sujoy on 2009-01-29
whoa, thanks dude, first time i have been able to comprehend someone else's code somewhat atleast :)

on running it i get this,
```

pass.py:46: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  builder.add_from_file("passwrd_ui.xml")
```

just change 

```
<property name="adjustment">0 0 100 1 10 10</property>
```
to 
```
<property name="adjustment">0 0 100 1 0 0</property>
```

in line 55 of the glade file

---

### Post by matmatmat on 2009-01-29
Thanks!

---

### Post by sujoy on 2009-01-29
> **matmatmat said:**
> Thanks!

err sorry dude, you just need to change 

<property name="page_size">0</property>

page_increment is fine.

---

### Post by sujoy on 2009-02-01
since i couldn't figure out how to work with bazaar and launchpad yet, i will add it here ...

```

if self.spin_value == 0:
    self.entry.set_text("Please enter the length & additional info.")
```

if this test holds, then its pointless to continue since pass of length 0 is essentially no pass at all. so you ought to add an else clause and add the rest of the code to the else part imo

---

