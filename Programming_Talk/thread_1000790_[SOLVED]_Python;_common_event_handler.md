---
title: "[SOLVED] Python; common event handler"
date: 2008-12-03
forum: Programming Talk
---

### Post by Sprut1 on 2008-12-03
Okay, so I've been googling for 4 hours and can't find any examples or help with this, but I really hope its possible. What I want is a common handler for all buttons in a frame.

```

    self.Bind(wx.EVT_BUTTON, self.Handler)

    def Handler(self, event):
	#handles all button clicks

```

I've tried figuring out if event return ID or something off what caused the event, but I failed doing so. So basically I'm wondering if this is doable or if its a lost cause, if its doable, does the event object return ID or Name of the button that caused event?

I'm used to having one event handling procedure.

Also, while we're at it, is it possible to have that event handler in an other module?

All help appriciated!
~Sprut1

---

### Post by SeanHodges on 2008-12-04
I assume you are referring to wxPython?

I haven't used it before, but I'd imagine you could iterate through all the buttons in the frame and add the binding to each one.

Something like this (untested):

```
for button_it in self.GetChildren:
    if type(button_it) == type(wx.Button): 
        self.button_it.Bind(wx.EVT_BUTTON, self.buttonClick)
```

---

### Post by Sprut1 on 2008-12-04
> **SeanHodges said:**
> I assume you are referring to wxPython?

I haven't used it before, but I'd imagine you could iterate through all the buttons in the frame and add the binding to each one.

Something like this (untested):

```
for button_it in self.GetChildren:
    if type(button_it) == type(wx.Button): 
        self.button_it.Bind(wx.EVT_BUTTON, self.buttonClick)
```

WxPython Ye, sorry if I didn't make that clear.

```
self.Bind(wx.EVT_BUTTON, self.Handler)

```

This line actually do exactly what you mean, it binds all button events to a handler, the problem however when doing this is that I don't know which button was pressed, which can be covered better like this:

```
self.Bind(wx.EVT_BUTTON, self.btnHelpHandler, self.btnHelp)
```

But as I said before then I must have 1 handler for every single button, I'd rather have 1 handler and parse which button was pressed within it, this is what Im used to. If this ain't possible, I'll accept that, just want to know :)

Edit: Just too show exactly what I want;
Say I have a frame with 3 buttons, btnHelp, btnAbout and btnQuit.

```

       self.Bind(wx.EVT_BUTTON, self.Handler) #in init class

       def Handler(self, event):
             if event.Name == "btnHelp":
                   #do
             elif event.Name == "btnAbout":
                   #do
             elif event.Name == "btnQuit":
                   #do

```

Something like that, event.Name I made up.

---

### Post by SeanHodges on 2008-12-05
I'd imagine your example should work if you use "event.GetEventObject().GetName()" in place of "event.Name()".

[http://www.wxpython.org/docs/api/wx.Event-class.html#GetEventObject](http://www.wxpython.org/docs/api/wx.Event-class.html#GetEventObject)

---

### Post by Sprut1 on 2008-12-06
Thanks this was exactly what I was looking for, however:

```
event.GetEventObject().GetName()
```

only returned "button", but :

```
event.GetEventObject().GetId()
```

returns the ID for the button that was pressed :)

Thanks alot!

---

