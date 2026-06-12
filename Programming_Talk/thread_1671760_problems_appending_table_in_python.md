---
title: "problems appending table in python"
date: 2011-01-20
forum: Programming Talk
---

### Post by Stefan J on 2011-01-20
Hi!

I'am new to python, gtk, glade. I want to build an simple app. With it I want to feed a database with values entered via a GUI. The GUI is designed in glade.

The program works in that way:

1. load the the UI definition file
2. connect the signal with the event handlers
3. use the gtk.builder to create the window

> 4. get the liststore object
> 5. append the data

I did not get it work. Maybe you can help me. Thanks!

Stefan

now the code:
...
        builder = gtk.Builder()
        builder.add_from_file('{0}UI.glade'.format(gladeFilePath))
        builder.connect_signals(
            {
             "destroy" : gtk.main_quit,
             #main wnd
             "on_bClose_wAPDmain_clicked" : self.wAPDmain_Close,
             "on_bHALManager_wAPDmain_clicked" : self.wAPDmain_HALmanager,
              }
            )
        self.wAPDmain = builder.get_object("wAPDmain")
        self.table = gtk.ListStore (builder.get_object ("liststore_HALComponent"))
...
self.table.append((123, 'bar', 'dsg'))
...
>>> when calling the append function the code fails

I think ge_object returns only a GOject and I need the liststore object. I have no idea how to manage it.

---

