---
title: "[Python] Strange errors - what am I doing wrong?"
date: 2009-11-19
forum: Programming Talk
---

### Post by Tahakki on 2009-11-19
Building a small program using Quickly, Python and Glade. Here's the code for the dialog:

```
# -*- coding: utf-8 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

import sys
import os
import gtk

from blether.bletherconfig import getdatapath

class NewDialog(gtk.Dialog):
    __gtype_name__ = "NewDialog"

    def __init__(self):
        """__init__ - This function is typically not called directly.
        Creation of a NewDialog requires redeading the associated ui
        file and parsing the ui definition extrenally, 
        and then calling NewDialog.finish_initializing().
    
        Use the convenience function NewNewDialog to create 
        a NewDialog object.
    
        """
        pass

    def finish_initializing(self, builder):
        """finish_initalizing should be called after parsing the ui definition
        and creating a NewDialog object with it in order to finish
        initializing the start of the new NewDialog instance.
    
        """
        #get a reference to the builder and set up the signals
        self.builder = builder
        self.builder.connect_signals(self)


    def ok(self, widget, data=None):
        """ok - The user has elected to save the changes.
        Called before the dialog returns gtk.RESONSE_OK from run().

        """
        pass

    def cancel(self, widget, data=None):
        """cancel - The user has elected cancel changes.
        Called before the dialog returns gtk.RESPONSE_CANCEL for run()

        """         
        pass

    def prename_text(self):
        return self.builder.get_object("entry1").get_text()

    def surname_text(self):
        return self.builder.get_object("entry2").get_text()

    def email_text(self):
        return self.builder.get_object("entry3").get_text()

    def phone_text(self):
        return self.builder.get_object("entry4").get_text()

    def mobile_text(self):
        return self.builder.get_object("entry5").get_text()

    def address_text(self):
        return self.builder.get_object("entry6").get_text()

    def twitter_text(self):
        return self.builder.get_object("entry7").get_text()

def NewNewDialog():
    """NewNewDialog - returns a fully instantiated
    dialog-camel_case_nameDialog object. Use this function rather than
    creating NewDialog instance directly.
    
    """

    #look for the ui file that describes the ui
    ui_filename = os.path.join(getdatapath(), 'ui', 'NewDialog.ui')
    if not os.path.exists(ui_filename):
        ui_filename = None

    builder = gtk.Builder()
    builder.add_from_file(ui_filename)    
    dialog = builder.get_object("new_dialog")
    dialog.finish_initializing(builder)
    return dialog

if __name__ == "__main__":
    dialog = NewNewDialog()
    dialog.show()
    gtk.main()

```

And here is the code for the main window:

```
#!/usr/bin/python
# -*- coding: utf-8 -*-
### BEGIN LICENSE
# This file is in the public domain
### END LICENSE

import sys
import os
import gtk
from desktopcouch.records.server import CouchDatabase
from desktopcouch.records.record import Record

# Check if we are working in the source tree or from the installed 
# package and mangle the python path accordingly
if os.path.dirname(sys.argv[0]) != ".":
    if sys.argv[0][0] == "/":
        fullPath = os.path.dirname(sys.argv[0])
    else:
        fullPath = os.getcwd() + "/" + os.path.dirname(sys.argv[0])
else:
    fullPath = os.getcwd()
sys.path.insert(0, os.path.dirname(fullPath))

from blether import AboutBletherDialog, PreferencesBletherDialog, NewDialog
from blether.bletherconfig import getdatapath

class BletherWindow(gtk.Window):
    __gtype_name__ = "BletherWindow"

    def __init__(self):
        """__init__ - This function is typically not called directly.
        Creation a BletherWindow requires redeading the associated ui
        file and parsing the ui definition extrenally,
        and then calling BletherWindow.finish_initializing().

        Use the convenience function NewBletherWindow to create
        BletherWindow object.

        """
        pass

    def finish_initializing(self, builder):
        """finish_initalizing should be called after parsing the ui definition
        and creating a BletherWindow object with it in order to finish
        initializing the start of the new BletherWindow instance.

        """
        #get a reference to the builder and set up the signals
        self.builder = builder
        self.builder.connect_signals(self)

        #uncomment the following code to read in preferences at start up
        #dlg = PreferencesBletherDialog.NewPreferencesBletherDialog()
        #self.preferences = dlg.get_preferences()

        #code for other initialization actions should be added here

        #Make the database!
        self.database = CouchDatabase("blether", create=True)

    def about(self, widget, data=None):
        """about - display the about box for blether """
        about = AboutBletherDialog.NewAboutBletherDialog()
        response = about.run()
        about.destroy()

    def preferences(self, widget, data=None):
        """preferences - display the preferences window for blether """
        prefs = PreferencesBletherDialog.NewPreferencesBletherDialog()
        response = prefs.run()
        if response == gtk.RESPONSE_OK:
            #make any updates based on changed preferences here
            pass
        prefs.destroy()

    def quit(self, widget, data=None):
        """quit - signal handler for closing the BletherWindow"""
        self.destroy()

    def on_destroy(self, widget, data=None):
        """on_destroy - called when the BletherWindow is close. """
        #clean up code for saving application state should be added here

        gtk.main_quit()

    def new_contact(self, widget, data=None):
        print "New contact..."
        new_contact = NewDialog.NewNewDialog()
        result = new_contact.run()
        
        #Get the stuff from the boxes

        prename = new_contact.prename_text
        surname = new_contact.surname_text
        email = new_contact.email_text
        phone = new_contact.phone_text
        mobile = new_contact.mobile_text
        address = new_contact.address_text
        twitter = new_contact.twitter_text

        new_contact.destroy()
        if result != gtk.RESPONSE_OK:
            return

        record_type = "http://wiki.ubuntu.com/Quickly"
        new_rec = Record({"record_type":record_type, "prename":prename, "surname":surname, "email":email, "phone":phone, "mobile":mobile, "address":address, "twitter":twitter})
        self.database.put_record(new_rec)

def NewBletherWindow():
    """NewBletherWindow - returns a fully instantiated
    BletherWindow object. Use this function rather than
    creating a BletherWindow directly.
    """

    #look for the ui file that describes the ui
    ui_filename = os.path.join(getdatapath(), 'ui', 'BletherWindow.ui')
    if not os.path.exists(ui_filename):
        ui_filename = None

    builder = gtk.Builder()
    builder.add_from_file(ui_filename)
    window = builder.get_object("blether_window")
    window.finish_initializing(builder)
    return window

if __name__ == "__main__":
    #support for command line options
    import logging, optparse
    parser = optparse.OptionParser(version="%prog %ver")
    parser.add_option("-v", "--verbose", action="store_true", dest="verbose", help="Show debug messages")
    (options, args) = parser.parse_args()

    #set the logging level to show debug messages
    if options.verbose:
        logging.basicConfig(level=logging.DEBUG)
        logging.debug('logging enabled')

    #run the application
    window = NewBletherWindow()
    window.show()
    gtk.main()

```

I can bring up the dialog just fine, but when I enter stuff into it and try to save by clicking OK (Couch) it gives me some weird error about JSON:

```
Traceback (most recent call last):
  File "bin/blether", line 107, in new_contact
    self.database.put_record(new_rec)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 157, in put_record
    record_id = self._add_record(record_data)
  File "/usr/lib/python2.6/dist-packages/desktopcouch/records/server_base.py", line 176, in _add_record
    return self.db.create(data)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 365, in create
    resp, data = self.resource.post(content=data)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 985, in post
    **params)
  File "/usr/lib/pymodules/python2.6/couchdb/client.py", line 1000, in _request
    body = json.encode(content).encode('utf-8')
  File "/usr/lib/pymodules/python2.6/couchdb/json.py", line 66, in encode
    return _encode(obj)
  File "/usr/lib/pymodules/python2.6/couchdb/json.py", line 114, in <lambda>
    dumps(obj, allow_nan=False, ensure_ascii=False)
  File "/usr/lib/pymodules/python2.6/simplejson/__init__.py", line 237, in dumps
    **kw).encode(obj)
  File "/usr/lib/pymodules/python2.6/simplejson/encoder.py", line 200, in encode
    chunks = self.iterencode(o, _one_shot=True)
  File "/usr/lib/pymodules/python2.6/simplejson/encoder.py", line 260, in iterencode
    return _iterencode(o, 0)
  File "/usr/lib/pymodules/python2.6/simplejson/encoder.py", line 177, in default
    raise TypeError(repr(o) + " is not JSON serializable")
TypeError: <bound method NewDialog.surname_text of <NewDialog object at 0x8cca464 (NewDialog at 0x8e46048)>> is not JSON serializable

```

Does anyone know what's going on?

---

### Post by DaithiF on 2009-11-19
Hi, i didn't read through the code too closely, but aren't you setting surname to the method rather than calling the method and setting surname with the result

```
surname = new_contact.surname_text

```
rather than
```
surname = new_contact.surname_text()
```

---

### Post by Tahakki on 2009-11-20
Fantastic, that's done it! Thank you so much, I'm still very, very new to Python and, indeed, programming in general.

Thanks!

---

