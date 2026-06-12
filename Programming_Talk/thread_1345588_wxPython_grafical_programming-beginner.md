---
title: "wxPython grafical programming-beginner"
date: 2009-12-04
forum: Programming Talk
---

### Post by Lucaya on 2009-12-04
Hello everyone,

im new here in this and wxPythn programming.
I got some experiance from C++,but im still a newbie in programming.

Well i changed to wxPaython and i want to create new windows and something for gameprogramming. Well i looked for some samples to learn at bit and found this code.

===================================================
#!/usr/bin/env python

from wxPython.wx import *

    class MyApp(wxApp):
        def OnInit (self):
            frame = wxFrame(NULL, -1, "Hello")
            frame.Show(true)
            self.SetTopWindow(frame)
            return true
        
        app = MyApp(0)
        app.MainLoop()
======================================================

originaly the sample if from a windows user, but i think its does matter which system is used.

I dont know the correct structure of python scripts so i dont realy know what the problem with this code, but my kde says the following error al the time:

IndentationError: unexpected indent
the error refer to line 5 class MyApp(wxApp):

Thank you for help me out =):D

---

