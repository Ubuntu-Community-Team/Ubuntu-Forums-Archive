---
title: "Python pyGTK 'finish_initalizing' error - what am I doing wrong?"
date: 2010-07-05
forum: Programming Talk
---

### Post by Admiral Yi on 2010-07-05
Hello,
I'm building an address book in python using quickly. I have created a new window, and copied the code for it from another window. I changed everything so it was correct for the new window, but there's a problem: 

This is the (applicable) code for the preferences window(which I copied)
```
# -*- coding: utf-8 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

from desktopcouch.records.server import CouchDatabase
from desktopcouch.records.record import Record
import gtk

from pyaddressbook.helpers import get_builder

import gettext
from gettext import gettext as _
gettext.textdomain('pyaddressbook')

class PreferencesPyaddressbookDialog(gtk.Dialog):
    __gtype_name__ = "PreferencesPyaddressbookDialog"
    preferences = {}

    def __new__(cls):
        """Special static method that's automatically called by Python when 
        constructing a new instance of this class.
        
        Returns a fully instantiated PreferencesPyaddressbookDialog object.
        """
        builder = get_builder('PreferencesPyaddressbookDialog')
        new_object = builder.get_object("preferences_pyaddressbook_dialog")
        new_object.finish_initializing(builder)
        return new_object

    def finish_initializing(self, builder):
        """Called while initializing this instance in __new__

        finish_initalizing should be called after parsing the ui definition
        and creating a PreferencesPyaddressbookDialog object with it in order to
        finish initializing the start of the new PerferencesPyaddressbookDialog
        instance.
        
        Put your initialization code in here and leave __init__ undefined.
        """

        # Get a reference to the builder and set up the signals.
        self.builder = builder
        self.builder.connect_signals(self)

        # Set up couchdb and the preference info.
        self._db_name = "pyaddressbook"
        self._database = CouchDatabase(self._db_name, create=True)
        self._preferences = None
        self._key = None

        # Set the record type and then initalize the preferences.
        self._record_type = (
            "http://wiki.ubuntu.com/Quickly/RecordTypes/Pyaddressbook/"
            "Preferences")
        self._preferences = self.get_preferences()
        # TODO: code for other initialization actions should be added here

```

And this is the code for the new window  (again, only the applicable bits):

```
# -*- coding: utf-8 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

import gtk

from pyaddressbook.helpers import get_builder

import gettext
from gettext import gettext as _
gettext.textdomain('pyaddressbook')

class NameAlreadyInAddressbookError(ValueError): pass

class AddNewDialog(gtk.Dialog):
    __gtype_name__ = "AddNewDialog"

    def __new__(cls):
        """Special static method that's automatically called by Python when 
        constructing a new instance of this class.
        
        Returns a fully instantiated AboutPyaddressbookDialog object.
        """
        builder = get_builder('AddNewDialog')
        new_object = builder.get_object("add_new_address")
        new_object.finish_initializing(builder)
        return new_object

    def finish_initializing(self, builder):
        """Called while initializing this instance in __new__

        finish_initalizing should be called after parsing the ui definition
        and creating a AboutPyaddressbookDialog object with it in order to
        finish initializing the start of the new AboutPyaddressbookDialog
        instance.
        
        Put your initialization code in here and leave __init__ undefined.
        """
        # Get a reference to the builder and set up the signals.
        self.builder = builder
        self.builder.connect_signals(self)
```

But when I try to run it I get this error:

```
  File "/home/joseph/pyaddressbook/pyaddressbook/AddNewDialog.py", line 27, in __new__
    new_object.finish_initializing(builder)
AttributeError: 'gtk.Dialog' object has no attribute 'finish_initializing'

```

I don't understand this. As far as I can tell, both the preferences window and the addnew window are gtk.Dialog windows, so why does one have this attribute and the other doesn't. In glade, both windows are the same type (Dialog windows). The code I removed after I copied it shouldn't effect this (I pasted it back in to check, but no joy). I tried commenting out the offending line. The code runs and the window appears when I click the right button, but nothing in it works and clicking the save button just quits the window, it doesn't run the code I have set it to run. Commenting out the same line in the preferences window code has the same effect on that window. I can't see what is wrong. I'm sure it's something obvious and simple. Any ideas?

---

### Post by diesch on 2010-07-05
It looks like that in the firt case *builder.get_object(...)* returns a PreferencesPyaddressbookDialog insdtance while in the second case it returns a gtk.Dialog instance (but you want a AddNewDialog instance).

I don't know about Quicky but I guess you need some additional magic somewhere instead of just copying the source code.

---

### Post by Admiral Yi on 2010-07-05
Possible, but isn't it the class line that defines the object type? It has gtk.Dialog as the argument. 

```
class AddNewDialog(gtk.Dialog):
```

Means create a new class of type gtk.Dialog. Or so I thought anyway.

---

### Post by diesch on 2010-07-05
The error is raised in AddNewDialog.__new__() at the lines

```

new_object = builder.get_object("add_new_address")
new_object.finish_initializing(builder)

```If *builder.get_object("add_new_address")* returns a instance of 
gtk.Dialog you can't call *finish_initializing(...)* on it. That has nothing to do with 
the class declaration

---

### Post by StephenF on 2010-07-05
Please post your .ui user interface definition file.

---

### Post by Admiral Yi on 2010-07-06
I'm not sure what file you mean, but I think this one:

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

import sys
import os
import gtk

import gettext
from gettext import gettext as _
gettext.textdomain('pyaddressbook')

# optional Launchpad integration
# this shouldn't crash if not found as it is simply used for bug reporting
try:
    import LaunchpadIntegration
    launchpad_available = True
except:
    launchpad_available = False

# Add project root directory (enable symlink, and trunk execution).
PROJECT_ROOT_DIRECTORY = os.path.abspath(
    os.path.dirname(os.path.dirname(os.path.realpath(sys.argv[0]))))

if (os.path.exists(os.path.join(PROJECT_ROOT_DIRECTORY, 'pyaddressbook'))
    and PROJECT_ROOT_DIRECTORY not in sys.path):
    sys.path.insert(0, PROJECT_ROOT_DIRECTORY)
    os.putenv('PYTHONPATH', PROJECT_ROOT_DIRECTORY) # for subprocesses

from pyaddressbook import (
    AboutPyaddressbookDialog, PreferencesPyaddressbookDialog, AddNewDialog, RemoveDialog)
from pyaddressbook.helpers import get_builder

class PyaddressbookWindow(gtk.Window):
    __gtype_name__ = "PyaddressbookWindow"
    
    # To construct a new instance of this method, the following notable 
    # methods are called in this order:
    # __new__(cls)
    # __init__(self)
    # finish_initializing(self, builder)
    # __init__(self)
    #
    # For this reason, it's recommended you leave __init__ empty and put
    # your inialization code in finish_intializing
    
    def __new__(cls):
        """Special static method that's automatically called by Python when 
        constructing a new instance of this class.
        
        Returns a fully instantiated PyaddressbookWindow object.
        """
        builder = get_builder('PyaddressbookWindow')
        new_object = builder.get_object("pyaddressbook_window")
        new_object.finish_initializing(builder)
        return new_object

    def finish_initializing(self, builder):
        """Called while initializing this instance in __new__

        finish_initalizing should be called after parsing the UI definition
        and creating a PyaddressbookWindow object with it in order to finish
        initializing the start of the new PyaddressbookWindow instance.
        
        Put your initilization code in here and leave __init__ undefined.
        """
        # Get a reference to the builder and set up the signals.
        self.builder = builder
        self.builder.connect_signals(self)

        global launchpad_available
        if launchpad_available:
            # see https://wiki.ubuntu.com/UbuntuDevelopment/Internationalisation/Coding for more information
            # about LaunchpadIntegration
            helpmenu = self.builder.get_object('helpMenu')
            if helpmenu:
                LaunchpadIntegration.set_sourcepackagename('pyaddressbook')
                LaunchpadIntegration.add_items(helpmenu, 0, False, True)
            else:
                launchpad_available = False

        # Uncomment the following code to read in preferences at start up.
        #dlg = PreferencesPyaddressbookDialog.NewPreferencesPyaddressbookDialog()
        #self.preferences = dlg.get_preferences()

        # Code for other initialization actions should be added here.


    def about(self, widget, data=None):
        """Display the about box for pyaddressbook."""
        about = AboutPyaddressbookDialog.AboutPyaddressbookDialog()
        response = about.run()
        about.destroy()

    def preferences(self, widget, data=None):
        """Display the preferences window for pyaddressbook."""
        prefs = PreferencesPyaddressbookDialog.PreferencesPyaddressbookDialog()
        response = prefs.run()
        if response == gtk.RESPONSE_OK:
            # Make any updates based on changed preferences here.
            pass
        prefs.destroy()

    def addnew(self, widget, data=None):
        """Display the new address dialog for pyaddressbook."""
        addnew = AddNewDialog.AddNewDialog()
        response = addnew.run()
        addnew.destroy()

    def remove(self, widget, data=None):
        """Display the about box for pyaddressbook."""
        remove = RemoveDialog.RemoveDialog()
        response = remove.run()
        remove.destroy()

    def search(self, widget, data=None):
        """Search the database for keywords"""
        #UNFINISHED
        class NoTextError(ValueError): pass

        Searchbar = self.builder.get_object('Searchbar')
        keyword = Searchbar.get_text()
        if keyword:
            print keyword
        else:
            raise NoTextError('No Text!')


    def quit(self, widget, data=None):
        """Signal handler for closing the PyaddressbookWindow."""
        self.destroy()

    def on_destroy(self, widget, data=None):
        """Called when the PyaddressbookWindow is closed."""
        # Clean up code for saving application state should be added here.
        gtk.main_quit()


if __name__ == "__main__":
    # Support for command line options.
    import logging
    import optparse
    parser = optparse.OptionParser(version="%prog %ver")
    parser.add_option(
        "-v", "--verbose", action="store_true", dest="verbose",
        help=_("Show debug messages"))
    (options, args) = parser.parse_args()

    # Set the logging level to show debug messages.
    if options.verbose:
        logging.basicConfig(level=logging.DEBUG)
        logging.debug('logging enabled')

    # Run the application.
    window = PyaddressbookWindow()
    window.show()
    gtk.main()
```

It's also possible this could help: 

```
# -*- coding: utf-8 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

"""Helpers for an Ubuntu application."""

__all__ = [
    'make_window',
    ]

import os
import gtk

from pyaddressbook.pyaddressbookconfig import get_data_file

import gettext
from gettext import gettext as _
gettext.textdomain('pyaddressbook')

def get_builder(builder_file_name):
    """Return a fully-instantiated gtk.Builder instance from specified ui 
    file
    
    :param builder_file_name: The name of the builder file, without extension.
        Assumed to be in the 'ui' directory under the data path.
    """
    # Look for the ui file that describes the user interface.
    ui_filename = get_data_file('ui', '%s.ui' % (builder_file_name,))
    if not os.path.exists(ui_filename):
        ui_filename = None

    builder = gtk.Builder()
    builder.set_translation_domain('pyaddressbook')
    builder.add_from_file(ui_filename)
    return builder
```

---

### Post by Admiral Yi on 2010-07-06
Ah, just realised you probably meant this:

```
<?xml version="1.0"?>
<interface>
  <requires lib="gtk+" version="2.16"/>
  <!-- interface-naming-policy project-wide -->
  <object class="GtkDialog" id="add_new_address">
    <property name="border_width">5</property>
    <property name="type_hint">normal</property>
    <property name="has_separator">False</property>
    <child internal-child="vbox">
      <object class="GtkVBox" id="vbox">
        <property name="visible">True</property>
        <property name="spacing">2</property>
        <child>
          <object class="GtkTable" id="table1">
            <property name="visible">True</property>
            <property name="n_rows">10</property>
            <property name="n_columns">2</property>
            <property name="row_spacing">2</property>
            <child>
              <object class="GtkEntry" id="Name">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="max_length">2</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="Add1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="Add2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">2</property>
                <property name="bottom_attach">3</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="Add3">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">3</property>
                <property name="bottom_attach">4</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="City">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">4</property>
                <property name="bottom_attach">5</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="County">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">5</property>
                <property name="bottom_attach">6</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="Postcode">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">6</property>
                <property name="bottom_attach">7</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="Tel1">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">7</property>
                <property name="bottom_attach">8</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="Tel2">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">8</property>
                <property name="bottom_attach">9</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label1">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Name</property>
              </object>
            </child>
            <child>
              <object class="GtkLabel" id="label2">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Address</property>
              </object>
              <packing>
                <property name="top_attach">1</property>
                <property name="bottom_attach">2</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label3">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Address</property>
              </object>
              <packing>
                <property name="top_attach">2</property>
                <property name="bottom_attach">3</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label4">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Address</property>
              </object>
              <packing>
                <property name="top_attach">3</property>
                <property name="bottom_attach">4</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label5">
                <property name="visible">True</property>
                <property name="label" translatable="yes">City</property>
              </object>
              <packing>
                <property name="top_attach">4</property>
                <property name="bottom_attach">5</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label6">
                <property name="visible">True</property>
                <property name="label" translatable="yes">County</property>
              </object>
              <packing>
                <property name="top_attach">5</property>
                <property name="bottom_attach">6</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label7">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Postcode</property>
              </object>
              <packing>
                <property name="top_attach">6</property>
                <property name="bottom_attach">7</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label8">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Tel no. 1</property>
              </object>
              <packing>
                <property name="top_attach">7</property>
                <property name="bottom_attach">8</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label9">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Tel no. 2</property>
              </object>
              <packing>
                <property name="top_attach">8</property>
                <property name="bottom_attach">9</property>
              </packing>
            </child>
            <child>
              <object class="GtkLabel" id="label10">
                <property name="visible">True</property>
                <property name="label" translatable="yes">Email</property>
              </object>
              <packing>
                <property name="top_attach">9</property>
                <property name="bottom_attach">10</property>
              </packing>
            </child>
            <child>
              <object class="GtkEntry" id="Email">
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="invisible_char">&#x25CF;</property>
              </object>
              <packing>
                <property name="left_attach">1</property>
                <property name="right_attach">2</property>
                <property name="top_attach">9</property>
                <property name="bottom_attach">10</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="position">1</property>
          </packing>
        </child>
        <child internal-child="action_area">
          <object class="GtkHButtonBox" id="dialog-action_area1">
            <property name="visible">True</property>
            <property name="layout_style">end</property>
            <child>
              <object class="GtkButton" id="Cancel">
                <property name="label">gtk-cancel</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <property name="use_stock">True</property>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="position">0</property>
              </packing>
            </child>
            <child>
              <object class="GtkButton" id="Save">
                <property name="label">Save</property>
                <property name="visible">True</property>
                <property name="can_focus">True</property>
                <property name="receives_default">True</property>
                <signal name="clicked" handler="saved"/>
              </object>
              <packing>
                <property name="expand">False</property>
                <property name="fill">False</property>
                <property name="position">1</property>
              </packing>
            </child>
          </object>
          <packing>
            <property name="expand">False</property>
            <property name="pack_type">end</property>
            <property name="position">0</property>
          </packing>
        </child>
      </object>
    </child>
    <action-widgets>
      <action-widget response="0">Cancel</action-widget>
      <action-widget response="-4">Save</action-widget>
    </action-widgets>
  </object>
</interface>
```


I have tried replacing the finish_initialising bit with the code from that function:

```
class AddNewDialog(gtk.Dialog):
    __gtype_name__ = "AddNewDialog"

    def save():

        Namebar, Add1, Add2, Add3, City, Country, Postcode, Tel1, Tel2, Email = self.builder.get_object('Name'), self.builder.get_object('Add1'), self.builder.get_object('Add2'), self.builder.get_object('Add3'), self.builder.get_object('City'), self.builder.get_object('Country'), self.builder.get_object('Postcode'), self.builder.get_object('Tel1'), self.builder.get_object('Tel2'), self.builder.get_object('Email'),
        
        name, val0, val1, val2, val3, val4, val5, val6, val7, val8 = Namebar.get_text(), Add1.get_text(), Add2.get_text(), Add3.get_text(), City.get_text(), Country.get_text(), Postcode.get_text(), Tel1.get_text(), Tel2.get_text(), Email.get_text()

        if not addressbook[name]:
            addressbook[name]=[val0, val1, val2, val3, val4, val5, val6, val7, val8]
        else:
            raise NameAlreadyInAddressbookError('This name is already in the address book. To change the data, delete the entry and re-enter it')
        
        addressbook.keys()


    def __new__(cls):
        """Special static method that's automatically called by Python when 
        constructing a new instance of this class.
        
        Returns a fully instantiated AboutPyaddressbookDialog object.
        """
        builder = get_builder('AddNewDialog')
        new_object = builder.get_object("add_new_address")
        #new_object.finish_initializing(builder)
        self = new_object
        self.builder = builder
        self.builder.connect_signals(self)

        return new_object
```

This gets me further, but I get a new error:
```
/home/joseph/pyaddressbook/pyaddressbook/AddNewDialog.py:44: RuntimeWarning: missing handler 'save'
  self.builder.connect_signals(self)

```

As you can see, the 'save' function is defined. It's not finished, but that shouldn't prevent it from seeing that it's there. There must be an easy fix for all this.

---

### Post by StephenF on 2010-07-06
I can't find any reference to this in the user interface definition you posted, which means either the file is wrong or you posted the wrong file.

```

new_object = builder.get_object("**preferences_pyaddressbook_dialog**")

```

---

### Post by Admiral Yi on 2010-07-06
Well, I may have posted the wrong file. What is the user interface definition? If it's the one with the preferences class in, that's the first file I posted.

---

### Post by srk9 on 2011-03-09
Did you ever find a solution to this issue? I'm having the same problem here in 2011! I agree with your approach in copying and rewriting the preferences file, as there is just not enough documentation available to try and write from scratch.

---

### Post by loneowais on 2011-05-26
This is because quickly PreferencesDialog is a custom pygtk widget that inherits the GtkDialog. It has a custom widget defined in preferences_*.xml file.

The name of the python class is also the same as the class of the custom widget, that's how it works. 

You'll need to edit the .glade file and set class to the custom widget class from GtkDialog.

---

