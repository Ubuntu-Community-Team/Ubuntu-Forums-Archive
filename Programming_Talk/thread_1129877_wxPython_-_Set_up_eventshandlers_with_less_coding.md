---
title: "wxPython - Set up events/handlers with less coding?"
date: 2009-04-19
forum: Programming Talk
---

### Post by dodle on 2009-04-19
Is there a way to set up events/event handlers using a single line for multiple buttons/objects?  I already tried adding the buttons to a list, then binding the list.... that doesn't work.

For example if I bind three buttons, I use three lines of code:
[php]button1.Bind(wx.EVT_BUTTON, self.EventHandler)
button2.Bind(wx.EVT_BUTTON, self.EventHandler)
button3.Bind(wx.EVT_BUTTON, self.EventHandler)[/php]

or just connecting:
[php]wx.EVT_BUTTON(button1, -1, self.EventHandler)
wx.EVT_BUTTON(button2, -1, self.EventHandler)
wx.EVT_BUTTON(button3, -1, self.EventHandler)[/php]

---

### Post by dodle on 2009-04-27
[php]button1 = wx.Button(self, -1, "1")
button2 = wx.Button(self, -1, "2")
button3 = wx.Button(self, -1, "3")

button_group = [button1, button2, button3]

for entry in button_group:
    entry.Bind(wx.EVT_BUTTON, self.OnButton)[/php]

---

### Post by Sprut1 on 2009-04-27
I also think I once connected all button events to 1 handler like this:

```

wx.Bind(wx.EVT_BUTTON, Handler)

```

---

### Post by dodle on 2009-05-02
Thanks, that could be useful.

---

### Post by Sprut1 on 2009-05-02
> **dodle said:**
> Thanks, that could be useful.

Ye, here is a discussion I started a long time ago:
[http://ubuntuforums.org/showthread.php?t=1000790](http://ubuntuforums.org/showthread.php?t=1000790)

Notice in last post, using

```

event.GetEventObject().GetId()

```

in handler will grant you the id of which button was pressed. This might be usefull if you can manage all the ID's :)

---

