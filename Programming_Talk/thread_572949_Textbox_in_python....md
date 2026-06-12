---
title: "Textbox in python..."
date: 2007-10-11
forum: Programming Talk
---

### Post by smartboyathome on 2007-10-11
Just to let you know, I am still pretty novice at python. Anyway...

I am wanting to create a GUI with a textbox so I don't have to go into GConf to edit the file with the new text anymore. Problem is I can't find how to do this. I would like it to replace the <no value> text in the command in GConf with the value inputed, or to set it to know value when the text box is blank. Thanks for helping to anyone who does!

---

### Post by pmasiar on 2007-10-11
EasyGUI is the easiest way to do GUI in Python. But why you need GUI? Plain old command-line is MUCH simpler to code, and will work exactly as well.

---

### Post by smartboyathome on 2007-10-11
Because I am hoping for my 'rents to use it sometime too, and they HATE to use the command line. :P

---

### Post by pmasiar on 2007-10-11
EasyGUI is your answer.

BTW re your sig: you want to give Ubuntu CDs to scare children? :-) Or Foxkeh does?

---

### Post by tehkain on 2007-10-11
```

# !/usr/bin/env python
import gtk
import pygtk
import gconf
class Gui:
    def __init__(self):
        self.keylocation = '/apps/avant-window-navigator/applets/MediaControl/Album_Art'
        self.client = gconf.client_get_default()
        window = gtk.Window()
        window.connect("destroy", lambda w: gtk.main_quit())
        vbox = gtk.VBox()
        hbox = gtk.HBox()
        label = gtk.Label('Loading')
        entry = gtk.Entry()
        button = gtk.Button(stock='gtk-ok')
        vbox.pack_start(label)
        vbox.add(hbox)
        hbox.pack_start(entry)
        hbox.pack_end(button)
        #entry.connect('activated',self.key_set,entry.get_text())
        button.connect('clicked',self.key_set)
        window.add(vbox)
        label.set_label(self.load_keys())
        window.show_all()
        self.label = label
        self.entry = entry
    def gconfkey(self):
        
        self.entry = entry    
    def load_keys(self):
        """
        Loads all the gconf variables 
        """
        var = self.client.get_string(self.keylocation)
        var = 'Current key value: ' + var
        return var
    def key_set(self,widget):
        """
        This Method takes the keyname and sets a value
        """
        var = self.entry.get_text()
        try:
            self.client.set_string        (self.keylocation,var)
        except:
            print 'Fail' 
        self.label.set_label(self.load_keys())
if __name__ == '__main__':
    main = Gui()
    gtk.main()
        

```

---

### Post by smartboyathome on 2007-10-11
> **pmasiar said:**
> BTW re your sig: you want to give Ubuntu CDs to scare children? :-) Or Foxkeh does?

No, no, I am saying people should give the CDs out instead of candy. ;)

Also, thank you tehkain, I will try that.

---

### Post by Wybiral on 2007-10-11
> **smartboyathome said:**
> No, no, I am saying people should give the CDs out instead of candy. ;)

INSTEAD OF CANDY??? Are you mad? You should give them out WITH candy or you're going to get tricked!

---

