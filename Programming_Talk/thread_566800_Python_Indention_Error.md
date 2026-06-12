---
title: "Python Indention Error"
date: 2007-10-03
forum: Programming Talk
---

### Post by mevets on 2007-10-03
I get a:
```

File "alarm.py", line 11
gtk.main_quit()

IndentationError: expected an indented block

```
Script:
```

#!/usr/bin/env python

# alarm.py

import pygtk
pygtk.require('2.0')
import gtk

class Clock:
   	def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False
        
   	def clicked_btnApply(self, widget):
   		strDay = self.cmbDay.get_text()
   		print strDay
   		return False

    def __init__(self):
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("Alarm Clock")

        self.window.connect("delete_event", self.delete_event)

        self.window.set_border_width(10)

        vbox1 = gtk.VBox(False, 5)
        self.window.add(vbox1)
        vbox1.show()
        
        # make Snooze button
        btnSnooze = gtk.Button("Stop", gtk.STOCK_CANCEL)
        hboxSnooze = gtk.HBox(True, 0)
        hboxSnooze.pack_start(btnSnooze, True, True, 0)
        #vbox1.pack_start(hboxSnooze, True, True, 0)
        
        hboxSetTime = gtk.HBox(False, 0)
        vbox1.pack_start(hboxSetTime, True, True, 0)
        # make the day combobox
        cmbDay = gtk.combo_box_entry_new_text()
        cmbDay.append_text('Monday')
        cmbDay.append_text('Tuesday')
        cmbDay.append_text('Wednesday')
        cmbDay.append_text('Thursday')
        cmbDay.append_text('Friday')
        cmbDay.append_text('Saturday')
        cmbDay.append_text('Sunday')
        cmbDay.set_active(0)
        hboxSetTime.pack_start(cmbDay, False, False, 0)
        
        # make AM/PM toggle button
        togAM = gtk.ToggleButton("AM")
        togAM.set_active(True)
        hboxSetTime.pack_end(togAM, False, False, 0)
        
        # make minute spin button
        adjMins = gtk.Adjustment(30, 0, 59, 1, 0, 0)
        spinMins = gtk.SpinButton(adjMins, 0, 0)
        hboxSetTime.pack_end(spinMins, False, False, 0)
        
        hboxSetTime.pack_end(gtk.Label(":"), False, False, 0)
        
        # make hour spin button
        adjHour = gtk.Adjustment(7, 1, 12, 1, 0, 0)
        spinHour = gtk.SpinButton(adjHour, 0, 0)
        hboxSetTime.pack_end(spinHour, False, False, 0)
        
        # add a separator
        hsep = gtk.HSeparator()
        vbox1.pack_start(hsep, False, True, 0)
        
        # make a horizontal box for the close and apply buttons
        btnBox = gtk.HBox(False, 5)
        
        # make close button
        btnClose = gtk.Button("Close", gtk.STOCK_CLOSE)
        btnClose.connect("clicked", lambda wid: gtk.main_quit())
        btnBox.pack_end(btnClose, False, False, 0)
        
        # make apply button
        btnApply = gtk.Button("Apply", gtk.STOCK_APPLY)
        btnApply.connect("clicked", self.clicked_btnApply)
        btnBox.pack_end(btnApply, False, False, 0)
        vbox1.pack_start(btnBox, False, False, 0)
        
        self.window.show_all()
        #btnSnooze.hide()
        
        return

def main():
    gtk.main()
    return 0       

if __name__ == "__main__":
    Clock()
    main()

```
I have tried moving clicked_btnApply above delete_event but I then get another error. Can anyone tell me where I have gone wrong?

---

### Post by dwblas on 2007-10-03
It's tough to tell without the actual error message, but the def's should all be indented the same amount, i.e.```
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False
        
    def clicked_btnApply(self, widget):
   		strDay = self.cmbDay.get_text()
   		print strDay
   		return False

    def __init__(self)
```

---

### Post by Tuna-Fish on 2007-10-03
> **mevets said:**
> I get a:
```

File "alarm.py", line 11
gtk.main_quit()

IndentationError: expected an indented block

```
Script:
```

#!/usr/bin/env python

# alarm.py

import pygtk
pygtk.require('2.0')
import gtk

class Clock:
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False


```
I
The line "def delete_event..." was indented one block too deep.

When you get some form of syntax error, look at the line mentioned and up of that line. BTW, clicked_btnapply is also indented too deep.

---

### Post by mevets on 2007-10-03
Yeah I copied and pasted dwblas code and it worked. It looks fine in Geany, maybe it was a spaces vs. tabs issue?

---

### Post by pmasiar on 2007-10-04
> **mevets said:**
> Yeah I copied and pasted dwblas code and it worked. It looks fine in Geany, maybe it was a spaces vs. tabs issue?

Use real editor. Use tools which help you in your job.

Real editor is one which lets you set tab size, and converts leading tabs to spaces. Set tab size to 4. Done. You will never have this kind of error again.

---

### Post by CptPicard on 2007-10-04
Use a language which has proper block delimiters... ;)

---

### Post by 1337455 10534 on 2007-10-04
Even the python IDE will tell you, at least mine does, select all and Format->> Untabify Region... Yes, set it to 4.

---

### Post by mevets on 2007-10-04
Im using SPE now, is that better sir?

---

### Post by dwblas on 2007-10-04
And now, you will hopefully help someone with the same error.  There will be more than one.  It is easy to get so involved with the logic of the code that you overlook the obvious.

---

### Post by finer recliner on 2007-10-04
python is sensitive to tabs vs. spaces. stick to just one in the future.

(didnt read the above comments, so im sorry if this was already mentioned)

---

