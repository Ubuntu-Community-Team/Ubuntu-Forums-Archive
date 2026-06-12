---
title: "Gtk+ 3 How to set filename for file to be saved?"
date: 2012-10-25
forum: Programming Talk
---

### Post by myromance123 on 2012-10-25
Hi there.
Alright, so I am doing a very basic text editor (extremely basic) to allow me to learn and understand Gtk.FileChooserAction.SAVE.

My problem right now is that I do not know how to grab the filename the user puts into the FileChooser and set that as the files actual name when being saved. It currently defaults to "Untitled Document" and won't change. I believe this may be a problem in my logic but am unsure.

Here is my code to better bring clarity to the problem:
```
#!/usr/env/python
from gi.repository import Gtk

class TextWindow(Gtk.Window):
    def __init__(self):
        Gtk.Window.__init__(self, title="Mini Writer")

        self.set_size_request(200,200)
        table = Gtk.Table(2, 1, True)
        self.add(table)

        textview = Gtk.TextView()
        self.textbuffer = textview.get_buffer()
        table.attach(textview, 0, 1, 0, 1)

        button = Gtk.Button(label="Save As..")
        button.connect("clicked", self.button_pressed)
        table.attach(button, 0, 1, 1, 2, ypadding=5)

    def add_filters(self, dialog):
        filter_text = Gtk.FileFilter()
        filter_text.set_name("Text Files")
        filter_text.add_mime_type("text/plain")
        dialog.add_filter(filter_text)

    def button_pressed( self, button ):
        print "Button pressed."
        self.begin = self.textbuffer.get_start_iter()
        self.end = self.textbuffer.get_end_iter()
        print self.textbuffer.get_text(self.begin, self.end, False)
        dialog = Gtk.FileChooserDialog("Save your text file", self,
                                       Gtk.FileChooserAction.SAVE,
                                       (Gtk.STOCK_CANCEL, Gtk.ResponseType.CANCEL,
                                        Gtk.STOCK_SAVE, Gtk.ResponseType.ACCEPT))
        dialog.set_default_size(800, 400)

        self.add_filters(dialog)
        response = dialog.run()

        Gtk.FileChooser.set_do_overwrite_confirmation(dialog, True)

        self.user_edited_new_document = True

        if( self.user_edited_new_document ):
            Gtk.FileChooser.set_current_name(dialog, "Untitled document")
        else:
            Gtk.FileChooser.set_filename(filename)
            
        if response == Gtk.ResponseType.ACCEPT:
            #char *filename

            filename = Gtk.FileChooser.get_filename(dialog)
            print filename
            self.save_to_file(filename)
            #g_free (filename)

        dialog.destroy()

    def save_to_file(self, filename):
        #function to write the file to computer
        file = open(filename, "w+")
        file.write(self.textbuffer.get_text(self.begin, self.end, False))

        file.close()
        #since now it is no longer a new document, we tell it as so
        self.user_edited_new_document = False

        

win = TextWindow()
win.connect("delete-event", Gtk.main_quit)
win.show_all()
Gtk.main()

```

Right now this program opens up to a small window named Mini Writer. It has a basic Gtk.TextView() and a button to initiate saving.

Currently I can save anywhere I want, but it will always save to "Untitled Document". The save itself works, and the text is saved no problem. This is being done in IDLE 2.7 on Ubuntu 12.10.

Any help or guidance is greatly appreciated!

---

### Post by spjackson on 2012-10-26
You need to set the default filename before you run the dialog. You are setting it after running the dialog!

Move this line:
```

        response = dialog.run()

```
To immediately before this one:
```

        if response == Gtk.ResponseType.ACCEPT:

```

---

### Post by myromance123 on 2012-10-26
Thank you spjackson, that did the trick!
However, after I have set its filename and saved the first time, saving the same document a second time should run this code (according to my understanding):

```
else:
    Gtk.FileChooser.set_filename(filename)
```

It is not being run at all though. Correct me if my understanding is wrong. I perceive this as a way to keep the filename that I saved the document as the first time. This is so that the second time I try to save the same document, it should automatically remember the name I saved it as last time and subsequently bring me to the location/directory of my saved file. Is this correct?

**_EDIT:_**
Alright, so my mistake was where I positioned my boolean variable user_edited_new_document. I repositioned it into the __init__ function and now it works.

I also found I can't use filename directly into Gtk.FileChooser.set_filename(), it will result in an error saying 
```
UnboundLocalError: local variable 'filename' referenced before assignment
```

So, in the save_to_file function, I made a new variable self.old_filename and passed it filename. Seems to work without a problem now.

Thanks once again spjackson!

Here's the working code if anyone else needs it later on:
```
"""
This simple app allows the user to write some text.
Then click the button to save that text somewhere.
"""

#!/usr/env/python
from gi.repository import Gtk

class TextWindow(Gtk.Window):
    def __init__(self):
        Gtk.Window.__init__(self, title="Mini Writer")

        # variable to check if we need to use old filename
        self.user_edited_new_document = True

        self.set_size_request(200,200)
        table = Gtk.Table(2, 1, True)
        self.add(table)

        textview = Gtk.TextView()
        self.textbuffer = textview.get_buffer()
        table.attach(textview, 0, 1, 0, 1)

        button = Gtk.Button(label="Save As..")
        button.connect("clicked", self.button_pressed)
        table.attach(button, 0, 1, 1, 2, ypadding=5)

    def add_filters(self, dialog):
        #Add text file filter
        filter_text = Gtk.FileFilter()
        filter_text.set_name("Text Files")
        filter_text.add_mime_type("text/plain")
        dialog.add_filter(filter_text)

    def button_pressed( self, button ):
        self.begin = self.textbuffer.get_start_iter()
        self.end = self.textbuffer.get_end_iter()
        dialog = Gtk.FileChooserDialog("Save your text file", self,
                                       Gtk.FileChooserAction.SAVE,
                                       (Gtk.STOCK_CANCEL, Gtk.ResponseType.CANCEL,
                                        Gtk.STOCK_SAVE, Gtk.ResponseType.ACCEPT))
        dialog.set_default_size(800, 400)

        self.add_filters(dialog)

        Gtk.FileChooser.set_do_overwrite_confirmation(dialog, True)

        if( self.user_edited_new_document ):
            Gtk.FileChooser.set_current_name(dialog, "Untitled document")
        else:
            Gtk.FileChooser.set_filename(dialog, self.old_filename)

        response = dialog.run()
            
        if response == Gtk.ResponseType.ACCEPT:

            filename = Gtk.FileChooser.get_filename(dialog)
            print "This is the filename: " + filename
            self.save_to_file(filename)

        dialog.destroy()

    def save_to_file(self, filename):
        self.user_edited_new_document = False
        print "User edited is: " + str(self.user_edited_new_document)
        #function to write the file to computer
        file = open(filename, "w+")
        file.write(self.textbuffer.get_text(self.begin, self.end, False))

        file.close()

        #save old filename for later
        self.old_filename = filename
        

win = TextWindow()
win.connect("delete-event", Gtk.main_quit)
win.show_all()
Gtk.main()
```

---

