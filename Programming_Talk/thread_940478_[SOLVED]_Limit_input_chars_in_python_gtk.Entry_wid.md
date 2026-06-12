---
title: "[SOLVED] Limit input chars in python gtk.Entry widget"
date: 2008-10-07
forum: Programming Talk
---

### Post by soxs on 2008-10-07
Hi, I am going to do a little shiny math program: [https://launchpad.net/gv](https://launchpad.net/gv)
And for that I need to know if there is a better way to do input-character limitation than this:
```
 def insert_cb(widget, text, length, *args):
    # if you don't do this, garbage comes in with text
    text = text[:length]
    pos = widget.get_position()
    # stop default emission
    widget.emit_stop_by_name("insert_text")
    gtk.idle_add(insert, widget, text, pos)

 def insert(widget, text, pos):
    # the next three lines set up the text. this is done because we
    # can't use insert_text(): it always inserts at position zero.
    orig_text = widget.get_text()
    text = string.replace(text, " ", "<SPACE>")
    new_text = orig_text[:pos] + text + orig_text[pos:]
    # avoid recursive calls triggered by set_text
    widget.signal_handler_block(insert_sig)
    # replace the text with some new text
    widget.set_text(new_text)
    widget.signal_handler_unblock(insert_sig)
    # set the correct position in the widget
    widget.set_position(pos + len(text))

 entry = gtk.Entry()
 insert_sig = entry.connect("insert_text", insert_cb)
```

thx a lot

---

### Post by xlinuks on 2008-10-07
I'm not a Python programmer, but I would suggest checking whether your code applies to situations when the user (1) pastes text and (2) does DnD (drag and drop).

---

### Post by soxs on 2008-10-07
> **xlinuks said:**
> I'm not a Python programmer, but I would suggest checking whether your code applies to situations when the user (1) pastes text and (2) does DnD (drag and drop).

Pasting is same is typing (at least for python it seems to be like that), dnd doesn't matter as I don't support it so it will do nothing.
EDIT: Unfortunatly this is NOT the same as I thought, and it will require to connect another signal to gtk.Entry.

---

### Post by gomputor on 2008-10-07
```
entry = gtk.Entry()
entry.set_max_length(3)
```

---

### Post by soxs on 2008-10-07
> **gomputor said:**
> ```
entry = gtk.Entry()
entry.set_max_length(3)
```

Oh, sorry, I wanted to limit the char variety, so the user can input only numbers or only letters. I hope this got clarified now.

---

### Post by gomputor on 2008-10-07
> **soxs said:**
> Oh, sorry, I wanted to limit the char variety, so the user can input only numbers or only letters. I hope this got clarified now.

Oh, I see :)

You can try something like this and if it satisfies you then modify it to suit your needs:
```
def accept_only_nums(widget):
    pos = widget.get_position()
    char = widget.get_chars(pos, pos + 1)
    if char not in "0123456789":
        widget.select_region(pos, pos + 1)
        widget.delete_selection()
```
and connect it with the **on_changed** signal of the Entry.

---

### Post by soxs on 2008-10-07
Will check if that will work for my purposes

NOTE: I got around that code from Post #1 doesn't work anymore it's outdated (it seems to be running with gtk 1.2 though)

---

### Post by soxs on 2008-10-07
A script that finally works:

```
#!/usr/bin/env python
# vim: set fileencoding=utf-8 :
import gtk
import pygtk

class xEntry(gtk.Entry):
    def __init__(self, allowedchars):
        gtk.Entry.__init__(self)
        self.allowedchars=allowedchars
        self.connect("changed", self.charcheck, None)

    def charcheck(self, widget, string, *args):
        pos = widget.get_position()
        char = widget.get_chars(pos, pos + 1)
        if char not in self.allowedchars:
            widget.select_region(pos, pos + 1)
            widget.delete_selection()


class MainWindow(gtk.Window):
    def __init__(self):
        print "111"
        gtk.Window.__init__(self,gtk.WINDOW_TOPLEVEL)
        self.entry = xEntry("1234567890.")        
        self.box = gtk.VBox()
        self.box.pack_start(self.entry)
        self.add(self.box)
        self.show_all()

def main():
    m=MainWindow()
    gtk.main()

if __name__ == "__main__":
    main()
```

@gomputor: The signal is named **changed** without the **on_**

---

### Post by gomputor on 2008-10-07
> **soxs said:**
> @gomputor: The signal is named **changed** without the **on_**

Yeah, I know that :) It's just I always put **on** before my defs, ie
**def on_myEntry_changed()** and not **def myEntry_changed()**

---

### Post by soxs on 2008-10-07
> **gomputor said:**
> Yeah, I know that :) It's just I always put **on** before my defs, ie
**def on_myEntry_changed()** and not **def myEntry_changed()**

That's useless and cost me 3mins of my lifetime... -.-

---

### Post by gomputor on 2008-10-07
> **soxs said:**
> That's useless and cost me 3mins of my lifetime... -.-
Oh really? It cost 3 whole minutes of your lifetime? Then I must apologize
for costing you such a great waste of your precious time. I'm terribly sorry,
I won't do that again!

[PS: If it's useless or not it depends on how you are designing your windows,
for example writing them from scratch or with glade, and if so working with
the .glade file or with the .xml file of the gtk-builder?
Anyway, I'm terribly sorry once again.]

---

### Post by soxs on 2008-10-07
> **gomputor said:**
> Oh really? It cost 3 whole minutes of your lifetime? Then I must apologize
for costing you such a great waste of your precious time. I'm terribly sorry,
I won't do that again!


Good, just keep that on_ locked up ;-).
Note: Without your idea of doing it that way, I would have been stuck half way before as I am still learning python and geovectors is rather a "learning by doing" project than a project for itself (though it seems to be useable atm).

> **gomputor said:**
> 
[PS: If it's useless or not it depends on how you are designing your windows,
for example writing them from scratch or with glade, and if so working with
the .glade file or with the .xml file of the gtk-builder?
Anyway, I'm terribly sorry once again.]
I like to keep track of what I am doing and keep the number of dependencies as low as possible (for the sake of windows compatibilty and install joy for the avarge IE/Win User).

---

