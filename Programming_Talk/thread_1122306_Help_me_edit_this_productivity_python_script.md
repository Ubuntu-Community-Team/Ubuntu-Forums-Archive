---
title: "Help me edit this productivity python script"
date: 2009-04-10
forum: Programming Talk
---

### Post by wersdaluv on 2009-04-10
[http://exit66.com/?p=272](http://exit66.com/?p=272)
```
#!/usr/bin/env python

from time import sleep
import gtk

message_title = "Wasting Time?"
message_text = "Consider if this is the best you can do with your time. Continue?"
minutes = 20
seconds = minutes * 60

class ProdBox(gtk.Dialog):
    def __init__(self):
        gtk.Dialog.__init__(self)

        self.ret = None

        self.connect("delete_event", self.delete_event)
        self.connect("destroy", self.quit)

        self.set_title(message_title)
        self.set_resizable(False)
        self.set_position(1)

        self.set_border_width(20)
        
        # Create box to pack widgets into
        self.message_label = gtk.Label(message_text)
        self.message_label.show()
        self.vbox.pack_start(self.message_label)
                
        self.hbox = gtk.HBox(False, 0)
        self.vbox.pack_start(self.hbox)

        # Create yes button
        self.yes_button = gtk.Button("_Yes")
        self.yes_button.set_border_width(10)
        self.yes_button.connect("clicked", self.yes)
        self.hbox.pack_start(self.yes_button, True, True, 0)
        self.yes_button.show()

        # Create no button
        self.no_button = gtk.Button("_No")
        self.no_button.set_border_width(10)
        self.no_button.connect("clicked", self.no)
        self.hbox.pack_start(self.no_button, True, True, 0)
        self.no_button.show()

        self.hbox.show()
        self.show()
        
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def yes(self, widget):
        self.ret = "yes"
        self.quit()
        
    def no(self, widget):
        self.ret = "no"
        self.quit()
        
    def quit(self, *args):
        self.hide()
        self.destroy()
        gtk.main_quit()

    
def show_message():
    go = ProdBox()
    gtk.main()
    return go.ret

if __name__ == "__main__":
    while True:
        ret = show_message()
        if ret == "yes":
            sleep(seconds)
        else:
            break
    
            
```

I slightly edited Andrew Barilla's script from the link above. What it does is to pop up a window that reminds me not to waste time every 20 mins and it will stop asking me (every 20 mins) if I press "No". 

I want to change it to asking "Are you spending your time wisely?" then if I press "Yes", it will ask me the same question after 20mins but if I press no, It will show me another window which tells me "Spend your time wisely, then." where I need to press "Yes" or "No" again. If I press "Yes there, it will wait for 20mins before popping the initial message again but if I press no, the same message will just reappear.

How do I do that? :)

---

### Post by wersdaluv on 2009-04-10
Managed to edit it

```
#!/usr/bin/env python

from time import sleep
import gtk

message_title = "Wasting Time?"
message_text = "Are you doing the best thing you could possibly do now?"
minutes = 20
seconds = minutes * 60

class ProdBox(gtk.Dialog):
    def __init__(self):
        gtk.Dialog.__init__(self)

        self.ret = None

        self.connect("delete_event", self.delete_event)
        self.connect("destroy", self.quit)

        self.set_title(message_title)
        self.set_resizable(False)
        self.set_position(1)

        self.set_border_width(20)
        
        # Create box to pack widgets into
        self.message_label = gtk.Label(message_text)
        self.message_label.show()
        self.vbox.pack_start(self.message_label)
                
        self.hbox = gtk.HBox(False, 0)
        self.vbox.pack_start(self.hbox)

        # Create yes button
        self.yes_button = gtk.Button("_Yes")
        self.yes_button.set_border_width(10)
        self.yes_button.connect("clicked", self.yes)
        self.hbox.pack_start(self.yes_button, True, True, 0)
        self.yes_button.show()

        # Create no button
        self.no_button = gtk.Button("_No")
        self.no_button.set_border_width(10)
        self.no_button.connect("clicked", self.no)
        self.hbox.pack_start(self.no_button, True, True, 0)
        self.no_button.show()

        self.hbox.show()
        self.show()
        
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def yes(self, widget):
        self.ret = "yes"
        self.quit()
        
    def no(self, widget):
        self.ret = "no"
        self.quit()
        
    def quit(self, *args):
        self.hide()
        self.destroy()
        gtk.main_quit()

    
def show_message():
    go = ProdBox()
    gtk.main()
    return go.ret

if __name__ == "__main__":
    while True:
        ret = show_message()
        if ret == "yes":
            sleep(seconds)
        else:
            break


message_title = "Be Productive, Please."
message_text = "Will you already spend your time wisely?"
    
class ProdInsBox(gtk.Dialog):
    def __init__(self):
        gtk.Dialog.__init__(self)

        self.ret = None

        self.connect("delete_event", self.delete_event)
        self.connect("destroy", self.quit)

        self.set_title(message_title)
        self.set_resizable(False)
        self.set_position(1)

        self.set_border_width(20)
        
        # Create box to pack widgets into
        self.message_label = gtk.Label(message_text)
        self.message_label.show()
        self.vbox.pack_start(self.message_label)
                
        self.hbox = gtk.HBox(False, 0)
        self.vbox.pack_start(self.hbox)

        # Create yes button
        self.yes_button = gtk.Button("_Yes")
        self.yes_button.set_border_width(10)
        self.yes_button.connect("clicked", self.yes)
        self.hbox.pack_start(self.yes_button, True, True, 0)
        self.yes_button.show()

        # Create no button
        self.no_button = gtk.Button("_No")
        self.no_button.set_border_width(10)
        self.no_button.connect("clicked", self.no)
        self.hbox.pack_start(self.no_button, True, True, 0)
        self.no_button.show()

        self.hbox.show()
        self.show()
            
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def yes(self, widget):
        self.ret = "yes"
        self.quit()
        
    def no(self, widget):
        self.ret = "no"
        self.quit()
        
    def quit(self, *args):
        self.hide()
        self.destroy()
        gtk.main_quit()

    
def show_message():
    go = ProdBox()
    gtk.main()
    return go.ret

if __name__ == "__main__":
    while True:
        ret = show_message()
        if ret == "yes":
            sleep(seconds)


```

There's just one problem. I want the ProdBox to be the one to appear after I say yes to the ProdInsBox. How do I do that?

---

### Post by abarilla on 2009-04-13
I modified the script.  You didn't need to create a separate class for the new dialog box.  Instead I added properties to pass in.  I also added an array of messages to loop through which includes not only the text and title but the time to wait before showing the message and the answer which causes the message to continue to show.

In the default code below, it will show your first message every 20 minutes until the user presses no and then the second one for every 5 minutes until the user presses yes.

Here's an enhanced version of the script:

```
#!/usr/bin/env python

# This is a GTK based version of the productivity script found here: 
#     http://lifehacker.com/5199748/productivity-script-reminds-you-to-spend-time-wisely
# Initially it had the same functionality but it has been since enhanced.
# 
# The script will loop endlessly until you press the close button in the message box
# instead of Yes or No.  It loops through the messages in the messages array found
# immediately after these comments.
#
# This array contains the definitions of the messages to show with the following properties:
#    title  - the text to show in the title bar of the message box
#    text   - the main text or question to show in the message box
#    time   - the time in minutes to wait before showing the message
#    answer - if the user clicks this answer (either "yes" or "no") the same message will 
#             continue to show, otherwise the next message will show

messages = [
    {'title'  : "Wasting Time?",
     'text'   : "Are you doing the best thing you could possibly do now?",
     'time'   : 20,
     'answer' : "yes"},
    {'title'  : "Be Productive, Please.",
     'text'   : "Are you already spending your time wisely?",
     'time'   : 5,
     'answer' : "no"},
    ]
    
from time import sleep
import gtk

class ProdBox(gtk.Dialog):
    def __init__(self, title, text):
        gtk.Dialog.__init__(self)

        self.ret = None

        self.connect("delete_event", self.delete_event)
        self.connect("destroy", self.quit)

        self.set_title(title)
        self.set_resizable(False)
        self.set_position(1)

        self.set_border_width(20)
        
        # Create box to pack widgets into
        self.message_label = gtk.Label(text)
        self.message_label.show()
        self.vbox.pack_start(self.message_label)
                
        self.hbox = gtk.HBox(False, 0)
        self.vbox.pack_start(self.hbox)

        # Create yes button
        self.yes_button = gtk.Button("_Yes")
        self.yes_button.set_border_width(10)
        self.yes_button.connect("clicked", self.yes)
        self.hbox.pack_start(self.yes_button, True, True, 0)
        self.yes_button.show()

        # Create no button
        self.no_button = gtk.Button("_No")
        self.no_button.set_border_width(10)
        self.no_button.connect("clicked", self.no)
        self.hbox.pack_start(self.no_button, True, True, 0)
        self.no_button.show()

        self.hbox.show()
        self.show()
        
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def yes(self, widget):
        self.ret = "yes"
        self.quit()
        
    def no(self, widget):
        self.ret = "no"
        self.quit()
        
    def quit(self, *args):
        self.hide()
        self.destroy()
        gtk.main_quit()

    
def show_message(title, text):
    go = ProdBox(title, text)
    gtk.main()
    return go.ret

current_message = 0

if __name__ == "__main__":
    while True:
        sleep(messages[current_message]['time'] * 60)
        ret = show_message(messages[current_message]['title'], messages[current_message]['text'])
        if ret == None:
            break
        elif ret != messages[current_message]['answer']:
            current_message += 1
            if current_message == len(messages):
                current_message = 0
```

---

### Post by wersdaluv on 2009-04-14
> **abarilla said:**
> I modified the script.  You didn't need to create a separate class for the new dialog box.  Instead I added properties to pass in.  I also added an array of messages to loop through which includes not only the text and title but the time to wait before showing the message and the answer which causes the message to continue to show.

In the default code below, it will show your first message every 20 minutes until the user presses no and then the second one for every 5 minutes until the user presses yes.

Here's an enhanced version of the script:

```
#!/usr/bin/env python

# This is a GTK based version of the productivity script found here: 
#     http://lifehacker.com/5199748/productivity-script-reminds-you-to-spend-time-wisely
# Initially it had the same functionality but it has been since enhanced.
# 
# The script will loop endlessly until you press the close button in the message box
# instead of Yes or No.  It loops through the messages in the messages array found
# immediately after these comments.
#
# This array contains the definitions of the messages to show with the following properties:
#    title  - the text to show in the title bar of the message box
#    text   - the main text or question to show in the message box
#    time   - the time in minutes to wait before showing the message
#    answer - if the user clicks this answer (either "yes" or "no") the same message will 
#             continue to show, otherwise the next message will show

messages = [
    {'title'  : "Wasting Time?",
     'text'   : "Are you doing the best thing you could possibly do now?",
     'time'   : 20,
     'answer' : "yes"},
    {'title'  : "Be Productive, Please.",
     'text'   : "Are you already spending your time wisely?",
     'time'   : 5,
     'answer' : "no"},
    ]
    
from time import sleep
import gtk

class ProdBox(gtk.Dialog):
    def __init__(self, title, text):
        gtk.Dialog.__init__(self)

        self.ret = None

        self.connect("delete_event", self.delete_event)
        self.connect("destroy", self.quit)

        self.set_title(title)
        self.set_resizable(False)
        self.set_position(1)

        self.set_border_width(20)
        
        # Create box to pack widgets into
        self.message_label = gtk.Label(text)
        self.message_label.show()
        self.vbox.pack_start(self.message_label)
                
        self.hbox = gtk.HBox(False, 0)
        self.vbox.pack_start(self.hbox)

        # Create yes button
        self.yes_button = gtk.Button("_Yes")
        self.yes_button.set_border_width(10)
        self.yes_button.connect("clicked", self.yes)
        self.hbox.pack_start(self.yes_button, True, True, 0)
        self.yes_button.show()

        # Create no button
        self.no_button = gtk.Button("_No")
        self.no_button.set_border_width(10)
        self.no_button.connect("clicked", self.no)
        self.hbox.pack_start(self.no_button, True, True, 0)
        self.no_button.show()

        self.hbox.show()
        self.show()
        
    def delete_event(self, widget, event, data=None):
        gtk.main_quit()
        return False

    def yes(self, widget):
        self.ret = "yes"
        self.quit()
        
    def no(self, widget):
        self.ret = "no"
        self.quit()
        
    def quit(self, *args):
        self.hide()
        self.destroy()
        gtk.main_quit()

    
def show_message(title, text):
    go = ProdBox(title, text)
    gtk.main()
    return go.ret

current_message = 0

if __name__ == "__main__":
    while True:
        sleep(messages[current_message]['time'] * 60)
        ret = show_message(messages[current_message]['title'], messages[current_message]['text'])
        if ret == None:
            break
        elif ret != messages[current_message]['answer']:
            current_message += 1
            if current_message == len(messages):
                current_message = 0
```
Niice. Thanks for spending time for this. Is there a way to make the script tally my yes and no responses then it will report it after an hour or something? :)

---

### Post by wersdaluv on 2009-04-14
I just noticed, when I continually press no, the two messages come out alternately. I want to see only the 2nd message until the user presses yes. Is that possible? :)

---

