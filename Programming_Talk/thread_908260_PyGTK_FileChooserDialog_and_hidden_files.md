---
title: "PyGTK: FileChooserDialog and hidden files"
date: 2008-09-02
forum: Programming Talk
---

### Post by MacUntu on 2008-09-02
I want to have a file chooser dialog that doesn't display hidden files per default. After a bit of API reading setting the chooser's show_hidden attribut via set_show_hidden(False) should do the trick but it fails. 

get_show_hidden() always returns the state that is set in the dialog with Ctrl+H - is this a backend problem?

[PHP]import pygtk
pygtk.require("2.0")
import gtk

fcd = gtk.FileChooserDialog("Select source directory...",
                            None,
                            gtk.FILE_CHOOSER_ACTION_SELECT_FOLDER,
                            (gtk.STOCK_CANCEL, gtk.RESPONSE_CANCEL,
                            gtk.STOCK_OPEN, gtk.RESPONSE_OK))

fcd.set_default_response(gtk.RESPONSE_OK)
print fcd.get_show_hidden() # True/False

fcd.set_show_hidden(False)
print fcd.get_show_hidden() # False

response = fcd.run()
print fcd.get_show_hidden() # True/False

if response == gtk.RESPONSE_OK:
    print fcd.get_filename()
elif response == gtk.RESPONSE_CANCEL:
    print 'No folder selected.'
    
fcd.destroy()[/PHP]

---

### Post by rogeriopvl on 2008-09-02
It should work :\

And according to this:

[http://www.pygtk.org/docs/pygtk/class-gtkfilechooser.html](http://www.pygtk.org/docs/pygtk/class-gtkfilechooser.html)

By default doesn't show hidden files.

Edit: I tried and it worked. No hidden files :\

---

### Post by MacUntu on 2008-09-02
That's weird. Did you try to change the state to show hidden files with Ctrl+H and then restart the thing?

Not working for me on another machine (intrepid this time):

First run:
   False, False
Then Ctrl+H => show hidden files, closed the dialog, second run:
   True, False, True

:-/

---

