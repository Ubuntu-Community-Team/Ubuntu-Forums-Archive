---
title: "[Python] gtk.Dialog - How to prevent closeing"
date: 2007-05-16
forum: Programming Talk
---

### Post by Laterix on 2007-05-16
I'm learning Python and I created a small test application that uses GTK through Glade. I got everything to work except one thing.

I have a dialog in my app and I would like to create it only once and then show/hide when needed. The problem is that if user clicks X on dialog window as shown below, then dialog widget gets destroyed and my app fails to show it again (of course).

[IMG]http://users.utu.fi/ljtaim/pics/pydialog.png[/IMG]

So, my question is how can I disable that X button in dialog right upper corner?

---

### Post by WW on 2007-05-16
Be sure the function that handles the "delete_event" signal returns True after calling the dialog's hide() function.

---

### Post by Laterix on 2007-05-16
I tried to do that. I have this kind of signal handler for destroy
```

    def on_url_dialog_destroy(self, widget):
        print "Dialog close"
        url_dialog = self.widgets.get_widget("url_dialog")
        url_dialog.hide()
        return True

```
The first time I click X, nothing happens. Second time I click, this method is executed (print proves that) and it crashes, because it says
```

AttributeError: 'NoneType' object has no attribute 'hide'

```

---

### Post by christhemonkey on 2007-05-16
I also am having this problem, but not only can i not reopen that dialog box (or hide it) i also cant bring up any more dialog boxs after...

Any advice would be really appreciated.

---

### Post by Laterix on 2007-05-16
Ok, I got it to work. I used wrong event. Here is the handler that works. Thanks for helping!
```

def on_url_dialog_delete_event(self, widget, data):
        print "Dialog close"
        url_dialog = self.widgets.get_widget("url_dialog")
        url_dialog.hide()
        return True

```

---

### Post by Laterix on 2007-05-16
> **christhemonkey said:**
> I also am having this problem, but not only can i not reopen that dialog box (or hide it) i also cant bring up any more dialog boxs after...

Any advice would be really appreciated.
Could you provide some code or more specific information on this problem?

---

### Post by christhemonkey on 2007-05-16
Not right now... shall see if my event is correct and post back some time tomorrow possibly.

---

### Post by christhemonkey on 2007-05-17
Ok, im having bigger problems than that one right now... never mind!

I'll get back to you if this problem ever becomes of the utmost importance.

---

