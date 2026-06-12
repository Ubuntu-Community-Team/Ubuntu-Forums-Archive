---
title: "Run terminal commands in Python"
date: 2011-11-22
forum: Programming Talk
---

### Post by bluedevil678 on 2011-11-22
Hi All, I am very new to all  this however I am working on a application to automatically enable my  wifi on Mint 11 which is soft blocked at start up. Using this as a  learning experience Ive decided to code this using the application  builder quickly.  [IMG]http://python-forum.org/pythonforum/images/smilies/icon_biggrin.gif[/IMG] 

This  went smoothly and was able to make a GUI application with a button  which at the moment prints the word "Test" ... I would like to know how  would I modify my defined function to allow for the processing of  instructions normally entered into the terminal?  [IMG]http://python-forum.org/pythonforum/images/smilies/icon_question.gif[/IMG] 

Here is the code for that function:

def on button1_clicked (self, button):
	print "Test"
	return

I  would like to know how do I for an example make it so that when the  button is clicked it would do the following terminal command: "rfkill unblock 0"

Ive tried playing with the os.system but didnt get very far.

Secondly  is it possible to produce the final output which would have been  visible in the terminal in the front end application ?  [IMG]http://python-forum.org/pythonforum/images/smilies/icon_mrgreen.gif[/IMG]  [IMG]http://python-forum.org/pythonforum/images/smilies/icon_mrgreen.gif[/IMG]


Here is a copy of the code:

# -*- Mode: Python; coding: utf-8; indent-tabs-mode: nil; tab-width: 4 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

import gettext
from gettext import gettext as _
gettext.textdomain('wifi')

import gtk
import logging
logger = logging.getLogger('wifi')

from wifi_lib import Window
from wifi.AboutWifiDialog import AboutWifiDialog
from wifi.PreferencesWifiDialog import PreferencesWifiDialog

# See [wifi_lib.Window.py]("http://wifi_lib.window.py/") for more details about how this class works
class WifiWindow(Window):
    __gtype_name__ = "WifiWindow"
    
    def finish_initializing(self, builder): # pylint: disable=E1002
        """Set up the main window"""
        super(WifiWindow, self).finish_initializing(builder)

        self.AboutDialog = AboutWifiDialog
        self.PreferencesDialog = PreferencesWifiDialog

    def on_button1_clicked (self, button):
        import os
        os.system(rfkill list)

        # Code for other initialization actions should be added here.

---

### Post by 11jmb on 2011-11-22
I think this is what you want.

[http://docs.python.org/library/subprocess.html#module-subprocess](http://docs.python.org/library/subprocess.html#module-subprocess)

Is there a specific reason you are using Python for this? It sounds more like a shell script problem to me.

---

### Post by bluedevil678 on 2011-11-23
Hi there, Thank you for your reply! 

I have this already in a Bash script and it works, but would like to code this function to a button. 

Ive tried this code and the application runs without error but this code seems to do nothing when I click the button its assigned to, am I not using this subsystem correctly ?

def on_button1_clicked (self, button):
    first = "rfkill list"
    import os
    os.system(first)
return

---

### Post by nvteighen on 2011-11-23
Yeah, it also looks like something more appropriate for bash...

Anyway, be aware that in languages that allow you to interface with non-executable code, i.e. modules or libraries, you should always first look for a library before using os.system... A library allows you to control the order and the data structures you're using in a much better way than using strings through an ad-hoc shell (which is what os.system does... it opens a shell just for the command given... and then shell exits without allowing you to recover any information from it).

---

### Post by bluedevil678 on 2011-11-24
Thank you for your reply... Learning I am ! 

I do see the use of a bash script here and have that down like a fat kid on a scone however I do wish to use the os.system can you help me by showing me an example for its usage running a command used in the terminal ?? :popcorn:

---

### Post by ziekfiguur on 2011-11-26
Like nvteighen said, os.system opens a shell for you, so any line you can put in a shell script would work when passed to os.system. The only difference would be that you can't get the output back from os.system.

Instead of os.system you should use the subprocess module that 11jmb pointed out to you, it's much more flexible and powerful than os.system, and because it doesn't open a seperate shell for every command you execute it's also more efficient. The url to the python docs 11jmb posted provides plenty of examples.

---

### Post by epicoder on 2011-11-27
Use [FONT=Courier New]subprocess.call()[FONT=Verdana].[/FONT][/FONT]
```

>>> subprocess.call(["ls", "-l"])
0

>>> subprocess.call("exit 1", shell=True)
1

subprocess.call(["rfkill", "list"])
```Passing the argument [FONT=Courier New]shell=True[FONT=Verdana] runs the command in the equivalent of an sh shell.[/FONT][/FONT] Don't use it with unprocessed user input, as it is vulnerable to shell injection.

The example is something you'd never use anyway. Instead of ls, use [FONT=Courier New]os.listdir(os.getcwd())[FONT=Verdana].[/FONT][/FONT]

---

