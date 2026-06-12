---
title: "Confused about wxPython window closing"
date: 2007-02-14
forum: Programming Talk
---

### Post by oedipuss on 2007-02-14
I'm writing an application with wxPython, and I'm a bit confused about how to close it properly.

I have a class that inherits from wx.App, in which there's a member wx.Frame as myapp.frame, which contains sizers, textboxes,menus and a canvas.
Where do I bind a close event ? 

```
myapp.Bind(wx.EVT_CLOSE, function)
or
myapp.frame.Bind(wx.EVT_CLOSE, function)
```

and what do I do in 'function' ? Do I call close() on the frame, or destroy()? Or do I call destroy() on the app itself, and should I destroy() the canvas too?
Also, I'd like the same function to be called whether the user selects Exit from the menu, or whether he clicks the X button.

I'm sorry if the question is kinda foolish, I'm new to wxpython , thanks in advance..

---

### Post by Omnios on 2007-02-14
You might find this interesting. Its a how to vid

[http://showmedo.com/videos/video?name=wxPythonBeginnersHelloWorld&fromSeriesID=4](http://showmedo.com/videos/video?name=wxPythonBeginnersHelloWorld&fromSeriesID=4)

---

