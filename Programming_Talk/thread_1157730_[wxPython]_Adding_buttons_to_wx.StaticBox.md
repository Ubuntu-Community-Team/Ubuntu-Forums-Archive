---
title: "[wxPython] Adding buttons to wx.StaticBox?"
date: 2009-05-13
forum: Programming Talk
---

### Post by dodle on 2009-05-13
I want there to be a border around some of my widgets and the only way that I know of to create a border is with wx.StaticBox.

I create my panel and border:
[php]lpanel = wx.Panel(self, -1)
lframe = wx.StaticBox(lpanel, -1)

lsizer = wx.BoxSizer(wx.VERTICAL)
lsizer.Add(lframe, 1, wx.EXPAND)

lpanel.SetAutoLayout(True)
lpanel.SetSizer(lsizer)
lpanel.Layout()[/php]

But I can't figure out how to put items inside the border.  If I try adding another widget to the sizer, it is placed under the border instead of inside.

**Edit:** I got it figured out.  Instead of using wx.BoxSizer, I needed to use wx.StaticBoxSizer.

---

