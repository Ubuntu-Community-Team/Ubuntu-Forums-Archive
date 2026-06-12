---
title: "wxPython error - programming newbie"
date: 2010-05-27
forum: Programming Talk
---

### Post by Axolotl9250 on 2010-05-27
Hi there, I'm new to programming and thought if I'm going to use a OS that's open source then I should get an appreciation as to how programs are made and how it's all done, I don't necessarily want to know how to become and expert programmer, but enough to do some things as a hobby.

I decided to start with python because it was recommended for being easy. I've done quite a few online tutorials and I've bought a few books. Anyway I wanted to learn more about GUI programming so I downloaded wxPython and wxWidgets via synaptic and then decided to add the api to my sources list and use update manager to get all the updates, I also got some tools and things as well which were dependencies. Anyway I'm using the wcPyWiki [HTML]http://wiki.wxpython.org/Getting%20Started#A_First_Application:_.22Hello.2C_World.22[/HTML] to get started and I did as it said and entered the following into a text file (I did this using IDLE and EMACS).
```
#!/usr/bin/python
import wx

app = wx.App(False) # Creates a new app, don't stdout/stderr to a window.
frame = wx.Frame(None, wx.ID_ANY, "Hello World") # A Frame is a top-level window.
frame.Show(True) # Show the frame.
app.Mainloop()
```When I run it in IDLE it gives me the following error ```
Traceback (most recent call last):
  File "/home/ben/wx.py", line 2, in <module>
    import wx
  File "/home/ben/wx.py", line 4, in <module>
    app = wx.App(False) # Creates a new app, don't stdout/stderr to a window.
AttributeError: 'module' object has no attribute 'App'
```and in EMACS it returns with: ```
>>> Traceback (most recent call last):
  File "/tmp/py83997Gw", line 7, in <module>
    app.Mainloop()
AttributeError: 'App' object has no attribute 'Mainloop'
>>> 
```Can anybody give some advice - I'm fairly computer literate and I've had Ubuntu for a few months, but a newcomer to programming.
Thanks.

[EDIT]The reason I did it in IDLE and EMACS is I did it in IDLE first and when it didn't work I tried EMACS to see if it would come up with the same error.

---

### Post by dodle on 2010-05-27
You need to rename your file to something other than "wx.py".  The filename is interfering with importing wx.  

**Edit:** Also, you need to call "app.MainLoop()", not "app.Mainloop()", captital "L".

---

### Post by Axolotl9250 on 2010-05-27
Thanks, it works now ^^. I was doing some reading about and in this wiki it shows how to generate the GUI and such and make menus and buttons. Then I was reading on the net and somebody mentioned wxGlade. Does anyone have an opinion on this? It looks to me like you drag and drop to make the physical layout of the app and then if it generates code, the coding to make event's happen is done afterwards. Is this a good/easy approach?

---

### Post by dodle on 2010-05-27
I haven't used wxGlade much, or any other Rapid Application Development tools, but I think they work just as well as coding an entire project yourself.  With experience it would probably be much faster to produce applications with it.  I personally just wanted to learn as much about coding as I could before I got into using RAD tools.

---

