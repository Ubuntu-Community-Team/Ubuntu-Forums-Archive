---
title: "Python. How do I destroy dialog"
date: 2009-05-20
forum: Programming Talk
---

### Post by bwitherell on 2009-05-20
Hello,

I am just learning python and I am having a bit of trouble closing a message dialog before my program sleeps.

Here is the block of code that I am having problems with: 

```

import gtk
import time

message = "test"

dialog = gtk.MessageDialog(None, 0, gtk.MESSAGE_QUESTION, gtk.BUTTONS_YES_NO, message)

#dialog.add_button(gtk.STOCK_CLOSE, gtk.RESPONSE_CLOSE)

response = dialog.run()

dialog.destroy()	
time.sleep(10)

```

What happens is the dialog appears and with a yes and no button. If I click either of these buttons the program will sleep for 10 seconds before closing the dialog.

Why does the program sleep before destroying the dialog if dialog.destroy() is before time.sleep(10)?

What is wrong with my code? I have googled this for hours to no avail.

Any help I can get will be much appreciated. 

Thank You.

---

### Post by slavik on 2009-05-20
where's gtk->main()???

---

### Post by bwitherell on 2009-05-20
gtk.main() is at the end of the program

---

### Post by crdlb on 2009-05-20
Basically, the answer is: never sleep in a GUI app (at least not in the GUI thread). Gtk postpones some tasks to the mainloop (ie gtk.main()), so you must return control to it as soon as possible, and sleep forces your app to do nothing at all for the duration. Blocking the mainloop like that will also make your user interface completely freeze as gtk is unable to process X events.

If you want something to happen approximately 10 seconds in the future, use```
gobject.timeout_add_seconds(10, call_me_in_ten_seconds)
```
That will make the mainloop call your function in (again, approximately) 10 seconds.

---

### Post by bwitherell on 2009-05-21
Awesome!! Thank you so much! That was exactly the solution I was looking for. Your explantaion as to why I should use gobject is great. Thank you for teaching me something about python and helping me understand what I was doing.

---

