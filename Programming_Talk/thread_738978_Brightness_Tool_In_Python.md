---
title: "Brightness Tool In Python"
date: 2008-03-29
forum: Programming Talk
---

### Post by joshdudeha on 2008-03-29
After experiencing trouble adjusting the brightness on my CRT screen with ubuntu - I found the command to change the gamma
```
xgamma -gamma x.x
```

this changes the gamma with X
And the "x.x" is where you put the number of gamma.

I'd like to learn a bit of python so I can build a graphical tool to change the brightness using this command.
It would be for end-users, not knowing the command (like me until finding it in some forum). It would ask you to enter a number e.g. 1.5 (my settingof gamma). And set the gamma level to that, it would also have a checkbox asking if you want it to be permanant; adding the command to the start-up sessions.

I just want a little help maybe with this. Implementing the command into a small program.
Could anyone possibly help me?
And also, I have chosen Python, because it is apparently the code to use in Ubuntu.
Thank you.

---

### Post by joshdudeha on 2008-03-29
Well where could I learn Python, and what tools can I use?

Especially if I want to build a simple GUI, are there any RAD tools for python?

---

### Post by pmasiar on 2008-03-29
see wiki in my sig to start with Python. EasyGUI is the simplest GUI builder (no events, no problems :-) ). I do web apps and not desktop apps, but I heard Glade is decent GUI builder. See sticky FAQ; if not enough start new thread with title more related to your question :-)

---

### Post by Can+~ on 2008-03-29
Question: Does the gnome brightness applet work for you? The one in Panel > "Add to Panel" > Brightness.

Anyway, if it works, it's still an exercise  to learn a new language

---

### Post by alexforcefive on 2008-03-29
> **joshdudeha said:**
> I just want a little help maybe with this. Implementing the command into a small program.

I'm actually learning python right now, so this was a good challenge for me! Thanks! I haven't learned how to make GUIs yet (well, I could have done it with pygame... ), but this should run ok from the terminal.

Here is the script I wrote. Just save it into a file called gammachanger.py and then go to a terminal and run:

```
python gammachanger.py
```

I added a bunch of comments, but if you get stuck just let me know

```
# import the python functions we're going to use

from os import system
from sys import exit
from string import lower

#initialise some variables

x = 1
gammaprogramcall = "xgamma -gamma 1.0" # variable for the xgamma program - i.e. what you'd type in the terminal

while True: # loops everything until you quit

	print system(gammaprogramcall) #runs the program

	gammachange = raw_input("Type U to increase brightness, D to decrease. Type X to quit: ")
	gammachange = lower(gammachange) #gets some input then converts it to lowercase

	if gammachange[:1] == "u": #take the first letter of the input
		x += 0.25 # this is the same as x = (x + 0.25)
		gammaparameters = "xgamma -gamma " + str(x) #updates the command we're going to run
	elif gammachange[:1] == "d":
		x -= 0.25
		gammaparameters = "xgamma -gamma " + str(x)
	elif gammachange[:1] == "x":
		exit()

	gammaprogramcall = str(gammaparameters) #run the program with the new gamma 
```

BTW I'd love to know what the more experienced guys think of my script. Have I made any atrocious mistakes anywhere? Thanks!

---

### Post by Can+~ on 2008-03-29
**1.** When using strings, you don't need to cut it this way *mystring[:1]*. Strings are arrays like any other, so you could use *mystring[0]*

**2.** Do you notice something here?

[PHP]	if gammachange[:1] == "u": #take the first letter of the input
		x += 0.25 # this is the same as x = (x + 0.25)
		gammaparameters = "xgamma -gamma " + str(x) #updates the command we're going to run
	elif gammachange[:1] == "d":
		x -= 0.25
		gammaparameters = "xgamma -gamma " + str(x)[/PHP]

The line *gammaparameters = "xgamma -gamma " + str(x)* is used 2 times equally, this is pretty much as in math when you have

(a + 2ab) = a(1+2b)

So you can take that element outside of both .

**3.** When building applications, it's always a good idea to work with a more OOP model, to have small functional blocks, like, for instance, the line that adds the string and the gammaparameters together, could be a spearate function, etc.

**4.** Use shorter variable names. gammaparemeters is too long. "gparms" could make it less typing.

*edit*
**5** Instead of the while True, you could use gammachange[:1] != "x".

---

### Post by pmasiar on 2008-03-30
> **Can+~ said:**
> 
**4.** Use shorter variable names. gammaparemeters is too long. "gparms" could make it less typing.

If you go that way, **be consistent with abbreviations** - create your own shortcuts dictionary. And don't skip vowels, gparams is OK if g always gamma and single item is param. **The bigger variable scope is, the longer variable name should be** (with less abbreviations). For  local variable in small function (5 lines), enough might be

[php]
gp = set(...) # gamma parameter
[/php]

Don't shortcut argument name, it goes to help: good meaningful name helps self-documenting code.

Don't be lazy for full name in bigger scope: you can always copy-paste it. Good full name with delimiters to make reading easier (**gamma_parameter**) is better than documentation: **it is guaranteed to be correct** in working code.

Remember, you will type name only once, but read it many times. If you need to look somewhere else to recall what name means, you waste more time than typing it right first time. net result will be wasted time and chances to bugs.

---

### Post by joshdudeha on 2008-03-30
Thanks To Everyone
and AlexForceFive - it's a great program.
More user-friendly than the normal terminal program.

Maybe we could work together in building a gui?
Because again, it would be even easier for people to change their brightness.

And I have tried the Gnome Brightness Applet, but it apparently only works on laptop screens or LCD's w/e.
Thanks. I'm gonna have a look at the Python.
Thanks everyone=]

---

### Post by alexforcefive on 2008-03-30
Thanks for the tips, Can+~ :) I do agree with pmasiar about variable names though. I like to keep them on the long side so I don't forget what they are :D

I still can't wrap my head around calling classes and stuff, that's why I kept it simple in this script. I'll get there eventually though :)

joshdude - add me on msn or something, I just updated my profile

---

### Post by bobbocanfly on 2008-03-30
I wrote a little tool for this in PyGTK with Glade. It does its job. The only set back is i couldnt workout how to get os.system() output into a variable so i couldnt parse its output and adjust the slider accordingly on startup. So i jsut set it to 1,0 when the app starts.

Edit: The Reset button just sets it back to 1, which should be usable for everyone.

pygamma.glade
```
<?xml version="1.0" standalone="no"?> <!--*- mode: xml -*-->
<!DOCTYPE glade-interface SYSTEM "http://glade.gnome.org/glade-2.0.dtd">

<glade-interface>

<widget class="GtkWindow" id="main_window">
  <property name="visible">True</property>
  <property name="title" translatable="yes">PyGamma</property>
  <property name="type">GTK_WINDOW_TOPLEVEL</property>
  <property name="window_position">GTK_WIN_POS_NONE</property>
  <property name="modal">False</property>
  <property name="default_height">300</property>
  <property name="resizable">False</property>
  <property name="destroy_with_parent">False</property>
  <property name="decorated">True</property>
  <property name="skip_taskbar_hint">False</property>
  <property name="skip_pager_hint">False</property>
  <property name="type_hint">GDK_WINDOW_TYPE_HINT_NORMAL</property>
  <property name="gravity">GDK_GRAVITY_NORTH_WEST</property>
  <property name="focus_on_map">True</property>
  <property name="urgency_hint">False</property>
  <signal name="destroy_event" handler="main_destroy" last_modification_time="Sat, 29 Mar 2008 14:59:35 GMT"/>
  <signal name="destroy" handler="main_destroy" last_modification_time="Sat, 29 Mar 2008 15:02:39 GMT"/>

  <child>
    <widget class="GtkVBox" id="vbox1">
      <property name="visible">True</property>
      <property name="homogeneous">False</property>
      <property name="spacing">0</property>

      <child>
	<widget class="GtkLabel" id="label1">
	  <property name="visible">True</property>
	  <property name="label" translatable="yes">Gamma</property>
	  <property name="use_underline">False</property>
	  <property name="use_markup">False</property>
	  <property name="justify">GTK_JUSTIFY_LEFT</property>
	  <property name="wrap">False</property>
	  <property name="selectable">False</property>
	  <property name="xalign">0.5</property>
	  <property name="yalign">0.5</property>
	  <property name="xpad">0</property>
	  <property name="ypad">0</property>
	  <property name="ellipsize">PANGO_ELLIPSIZE_NONE</property>
	  <property name="width_chars">-1</property>
	  <property name="single_line_mode">False</property>
	  <property name="angle">0</property>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">False</property>
	  <property name="fill">False</property>
	</packing>
      </child>

      <child>
	<widget class="GtkAlignment" id="alignment1">
	  <property name="visible">True</property>
	  <property name="xalign">0.5</property>
	  <property name="yalign">0.5</property>
	  <property name="xscale">1</property>
	  <property name="yscale">1</property>
	  <property name="top_padding">0</property>
	  <property name="bottom_padding">0</property>
	  <property name="left_padding">0</property>
	  <property name="right_padding">0</property>

	  <child>
	    <widget class="GtkHBox" id="hbox1">
	      <property name="visible">True</property>
	      <property name="homogeneous">False</property>
	      <property name="spacing">0</property>

	      <child>
		<widget class="GtkVScale" id="gamma_slider">
		  <property name="height_request">156</property>
		  <property name="visible">True</property>
		  <property name="can_focus">True</property>
		  <property name="draw_value">True</property>
		  <property name="value_pos">GTK_POS_BOTTOM</property>
		  <property name="digits">3</property>
		  <property name="update_policy">GTK_UPDATE_CONTINUOUS</property>
		  <property name="inverted">True</property>
		  <property name="adjustment">0 0 5 0.10000000149 0 0</property>
		  <signal name="value_changed" handler="slider_changed" last_modification_time="Sat, 29 Mar 2008 14:51:00 GMT"/>
		</widget>
		<packing>
		  <property name="padding">0</property>
		  <property name="expand">True</property>
		  <property name="fill">True</property>
		</packing>
	      </child>
	    </widget>
	  </child>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">True</property>
	  <property name="fill">True</property>
	</packing>
      </child>

      <child>
	<widget class="GtkHBox" id="hbox2">
	  <property name="visible">True</property>
	  <property name="homogeneous">False</property>
	  <property name="spacing">0</property>

	  <child>
	    <widget class="GtkButton" id="reset_button">
	      <property name="width_request">62</property>
	      <property name="height_request">27</property>
	      <property name="visible">True</property>
	      <property name="can_focus">True</property>
	      <property name="label" translatable="yes">Reset</property>
	      <property name="use_underline">True</property>
	      <property name="relief">GTK_RELIEF_NORMAL</property>
	      <property name="focus_on_click">True</property>
	      <signal name="clicked" handler="reset_clicked" last_modification_time="Sun, 30 Mar 2008 17:00:55 GMT"/>
	    </widget>
	    <packing>
	      <property name="padding">0</property>
	      <property name="expand">False</property>
	      <property name="fill">False</property>
	    </packing>
	  </child>

	  <child>
	    <widget class="GtkButton" id="exit_button">
	      <property name="width_request">62</property>
	      <property name="height_request">27</property>
	      <property name="visible">True</property>
	      <property name="can_focus">True</property>
	      <property name="label" translatable="yes">Exit</property>
	      <property name="use_underline">True</property>
	      <property name="relief">GTK_RELIEF_NORMAL</property>
	      <property name="focus_on_click">True</property>
	      <signal name="clicked" handler="exit_clicked" last_modification_time="Sun, 30 Mar 2008 17:03:57 GMT"/>
	    </widget>
	    <packing>
	      <property name="padding">0</property>
	      <property name="expand">False</property>
	      <property name="fill">False</property>
	    </packing>
	  </child>
	</widget>
	<packing>
	  <property name="padding">0</property>
	  <property name="expand">True</property>
	  <property name="fill">True</property>
	</packing>
      </child>
    </widget>
  </child>
</widget>

</glade-interface>
```



pygamma.py
```
#!/usr/bin/env python

import os, sys

try:
 	import pygtk
  	pygtk.require("2.0")
except:
  	pass
try:
	import gtk
  	import gtk.glade
except:
        print "Couldnt load GTK/Glade libraries"
	sys.exit(1)

__title__ = "pygamma"
__version__ = "0.1.0"
__authors__ = ["David Futcher ('bobbo') <bobbocanfly@gmail.com>"]

class gtkGUI:

    #Set Up The GUI
    def __init__(self):	
        #Set the Glade file
        self.gladefile = "pygamma.glade"  
        self.wTree = gtk.glade.XML(self.gladefile) 

        #Create our dictionay and connect it
        dic = {
  	    "slider_changed" : self.changeGamma,
            "main_destroy" : gtk.main_quit,
            "reset_clicked" : self.resetGamma,
            "exit_clicked" : gtk.main_quit
              }
        self.wTree.signal_autoconnect(dic)

        self.wTree.get_widget("gamma_slider").set_value(1.0) #Set it to 1 to start with. Ideally we would parse the
                                                             #output of xgamma but this is just a simple wrapper


    def resetGamma(self, widget):
        self.wTree.get_widget("gamma_slider").set_value(1.0)

    def changeGamma(self, widget):
        gamma = str(self.wTree.get_widget("gamma_slider").get_value())
        os.system("xgamma -gamma " + gamma)

if __name__ == "__main__":
	gui = gtkGUI()
	gtk.main()
```

---

### Post by joshdudeha on 2008-03-31
That is a great example of what I wanted to build
Thank you Bobbocanfly.

I love it.
I'm gonna use it as an example and try to code up something a little bit differentx

---

