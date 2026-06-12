---
title: "[SOLVED] wxPython &amp;quot;close&amp;quot; menu item icon"
date: 2008-09-06
forum: Programming Talk
---

### Post by suprfish on 2008-09-06
Currently learning the ins-and-outs of wxPython. I've run into a little problem and I can't find any docs about it: using wxPython, how can I make a "close" menu item which uses whatever icon the theme is supposed to?

```

file = wx.Menu()
file.Append(11, '&Close\tCtrl+W')

```

I'm sure there is something built in to wxWidgets, but I can't find it. Thanks for any help :)

---

### Post by StOoZ on 2008-09-06
well , I use wxwidgets in C++ , but I guess the concept is quite the same.
append to the wxmenu , a wxmenu item , which you then you set its icon with wxMenuItem::SetBitmap : 
[http://docs.wxwidgets.org/stable/wx_wxmenuitem.html#wxmenuitemsetbitmap]("http://docs.wxwidgets.org/stable/wx_wxmenuitem.html#wxmenuitemsetbitmap")

I never used that function , I like my menu items without any graphics. (-:

---

### Post by suprfish on 2008-09-06
Thanks, but what if, for example, the user has set their environment to use a specific icon theme? How can I use whatever that theme says I should use as the "close" icon? I feel like there's some standard way to do it that I'm missing.

---

### Post by suprfish on 2008-09-06
(bump)

---

### Post by suprfish on 2008-09-06
Got it, it's
```

file.Append(wx.ID_EXIT, '&Close\tCtrl+W')

```
which makes sense, but I couldn't find any documentation on it so I did a search on google code...

---

### Post by StOoZ on 2008-09-07
I think its not what I meant to do in the first place.
:)

---

