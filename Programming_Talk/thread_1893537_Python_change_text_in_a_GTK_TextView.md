---
title: "Python change text in a GTK TextView"
date: 2011-12-10
forum: Programming Talk
---

### Post by nshiell on 2011-12-10
Ok, I'm kinda newb to GTK/Python
I have created a window using glade with a text view.
It displays fine, but when I show the window I would like to change the text in the text view.

I'm stuck as I don't know how to get an the text view and how to change it's text.
I have looked at as much docs as I can but still clueless

Can you tell me how I can do this please

---

### Post by Bodsda on 2011-12-10
> **nshiell said:**
> Ok, I'm kinda newb to GTK/Python
I have created a window using glade with a text view.
It displays fine, but when I show the window I would like to change the text in the text view.

I'm stuck as I don't know how to get an the text view and how to change it's text.
I have looked at as much docs as I can but still clueless

Can you tell me how I can do this please

Best up to date PyGTK tutorial I have used - [http://www.learngtk.org/pygtk-tutorial/textviewconstruction.html](http://www.learngtk.org/pygtk-tutorial/textviewconstruction.html)

You can make the text editable with ```
textview.set_editable(True)
``` 
If you want to set the original text in the buffer, you'll want ```
tetbuffer.set_text("This is my text")
```

Hope this helps,
Bodsda
Ubuntu Beginners Team

---

### Post by nshiell on 2012-01-06
Hi thanks but this has not helped me.
I have designed a UI using Glade so first I need to know to get an instance? of the text view, then I need to know how top set some text for it I guess??????????????????

Everything else I have tried has either produced errors or done noting.

---

### Post by CoffeeRain on 2012-01-06
Could you show what you have done and then post the error message?

---

### Post by nshiell on 2012-01-06
Sure,
file KickOffWindow.ui
[HTML]
.........
        <child>
          <object class="GtkTextView" id="textview_commands">
            <property name="height_request">300</property>
            <property name="visible">True</property>
            <property name="can_focus">True</property>
            <property name="accepts_tab">False</property>
          </object>
          <packing>
            <property name="expand">True</property>
            <property name="fill">True</property>
            <property name="position">2</property>
          </packing>
        </child>
............
[/HTML]

In my code: -
```

def menuitem_show_settings(self, w):
        window = self.KickOffWindow.KickOffWindow()
        window.show()
        box = self.KickOffWindow.textview_commands()

```

CLI: -
```

Traceback (most recent call last):
  File "/home/nicholas/Python/kick-off/kick_off_lib/Kick_off_appindicator.py", line 44, in menuitem_show_settings
    box = self.KickOffWindow.textview_commands()
AttributeError: 'module' object has no attribute 'textview_commands'

```

When I call "menuitem_show_settings"
I get up my window OK, but I wanna set some text in the text view aaaaarrrrggggggghhhh!!!

---

