---
title: "Can't import wxpython though I have packages"
date: 2008-06-28
forum: Programming Talk
---

### Post by Nexusx6 on 2008-06-28
I was getting my feet wet in wxpython, and an ebook I have was showing some sample code. Following along with the author, I made a file called wx_test.py and put the following code in it:
```

import wx

app = wx.App()
win = wx.Frame(None, title="Simple Editor")
loadButton = wx.Button(win, label='Open')
saveButton = wx.Button(win, label='Save')
win.Show()
app.MainLoop()

```

However, when I try to run the program, the Python interpreter dishes this out:
```
Traceback (most recent call last):
  File "/home/fox/programing/wx_test.py", line 1, in <module>
    import wx
ImportError: No module named wx
```

I'm completely lost :( I have these packages all installed, so I can't see why Python can't import it:
> python-wxgtk2.8 python-wxtools python-wxversion

In case it matters, I'm running Kubuntu 8.04. Any help is appreciated

---

### Post by cdekter on 2008-06-29
Try re-installing the packages you listed. It definitely makes no sense that you are getting that error...

---

### Post by Nexusx6 on 2008-06-29
I found out why I can't import wx. There's a bug in hardy/gutsy of some sort that doesn't put the mod in its correct place: [the launchpad page on it can be found here]("https://bugs.launchpad.net/ubuntu/+source/wxwidgets2.8/+bug/211553")

I've tried all the suggestions posted on launchpad, like using "ln" to link the files. When I tried to copy wx.pth like suggested, I got a weird error telling me the file I was going to cp was the same, or something like that (don't remember the exact error). The end result of these attempts was a very unstable program; I could only run the program once. Once I closed it, if I tried to run it again without closing/restarting IDLE I get this error:
```
Traceback (most recent call last):
  File "/home/fox/programing/wx_test.py", line 3, in <module>
    win = wx.Frame(None, title="Simple Editor")
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-ansi/wx/_windows.py", line 497, in __init__
    _windows_.Frame_swiginit(self,_windows_.new_Frame(*args, **kwargs))
PyNoAppError: The wx.App object must be created first!
```

/sigh. 

Should/Can I just compile this from source? Would that fix everything? If so, how can I? I have the source un-tar'd, but I don't know what commands to type in terminal.

[screenshot]: IDLE behaves very very weird while the simple program is running. Notice how the program "wipes" the text under the two windows

---

