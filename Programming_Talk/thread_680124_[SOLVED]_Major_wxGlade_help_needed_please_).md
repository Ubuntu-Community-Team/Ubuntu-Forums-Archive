---
title: "[SOLVED] Major wxGlade help needed please :)"
date: 2008-01-27
forum: Programming Talk
---

### Post by 1337455 10534 on 2008-01-27
I created this cool-looking GUI for my project (see my sig), but I have no idea how to implement it.
Ok, so I generated code for my GUI, all I have to do now is to assign functions to each action (ie create handlers?). How do I do this?
Can I merge existing code with the GUI?

Anyone know of any good documentation for wxGlade? I did this completely out of trial/error...

---

### Post by diaa on 2008-01-27
wxGlade generate code that uses the open-source application framework *wxWidgets*, you should find out the details of the event handlers in [wxPython documentation]("http://www.wxpython.org/docs/api/"), also I suggest you check [wxPython wiki]("http://wiki.wxpython.org/").

*wxPython is wxWidgets bindings for Python, since the library is originally written in C++*

---

### Post by 1337455 10534 on 2008-01-27
thanks

---

### Post by 1337455 10534 on 2008-01-29
I can't mark this as solved just yet...
I need to run certain functions when things happen (eg if i pick a name from a list). Using wxGlade, can I just pick a widget, select its event tab, and enter in the name of the function in the handler box? If not, how can I programmatically? The links are good, but they don't elaborarte on handlers...

---

### Post by diaa on 2008-01-29
> **1337455 10534 said:**
> I need to run certain functions when things happen (eg if i pick a name from a list). Using wxGlade, can I just pick a widget, select its event tab, and enter in the name of the function in the handler box? If not, how can I programmatically?

yes that's possible, you can use wxGlade to set event handlers, then what's the problem?

---

### Post by 1337455 10534 on 2008-01-29
Well, I picked a widget and typed 'yes' to the event box. I generated the code, and all I get is this;
```

# begin wxGlade: Frame.__init__
# begin wxGlade: Frame.__set_properties
# begin wxGlade: Frame.__do_layout
# blah blah blah
# end wxGlade

    def yes(self, event): # wxGlade: Frame.<event_handler>
        print "Event handler `yes' not implemented!"
        event.Skip()

# end of class Frame\
class VeduGUI(wx.App):
# blah

```
All it did was define "yes". I can see that it is up to me now to make "yes" useful, but how do I know that yes will only run if that widget is activated?

---

### Post by 1337455 10534 on 2008-01-29
self.choice(#widgety things)
self.Bind(wx.EVT_CHOICE, self.yes)
def yes(self,event):
 import time
 time.sleep(5)
 print "yea"

Success!

---

### Post by diaa on 2008-01-29
I don't understand what's the problem now, can you state it clearly?

---

### Post by 1337455 10534 on 2008-01-29
Um, I fixed it, I posted what I did in the lsat post, but thank you veryb much for the concern :).
To elaborate, self.choice is the choice widget (#widgety thigns are test on the widget etc.).
Then self.Bind(wx.EVT_CHOICE, self.yes) tells the program for the choice event, execute the yes function.
So I'm happy. No harm in guessing

---

