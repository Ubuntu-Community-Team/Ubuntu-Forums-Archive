---
title: "wxPython - sizer issue?"
date: 2009-10-10
forum: Programming Talk
---

### Post by aaronp on 2009-10-10
Hi all,
I have a class inherited from wx.Frame.
In this I have placed a wx.Panel and then some sizers:

```
        self.mainSizer = wx.BoxSizer(wx.VERTICAL)
        self.mainDisplaySizer = wx.BoxSizer(wx.HORIZONTAL)
        self.grid = wx.GridSizer(10,2,10,5)
        self.buttonSizer = wx.BoxSizer(wx.VERTICAL)
```

The mainSizer has a static text at the top and then the
mainDisplaySizer.
Inside the mainDisplaySizer I have added a staticText as a 'left
margin' then I've added self.grid, then another staticText as an
'inside margin' and then the buttonSizer.

It all looks fine in terms of layout but the issues are:
1. I would like the frame to open up at the correct size to fit all of
its contents nicely but without setting its size explicitly in the
__init__ method.
2. Also, even if I do explicitly set the size, any resizing that I do
doesn't affect any of the widgets.

I was under the impression from the reading I've been doing on various
sites that the point of me using sizers is that the widgets' size
would adapt to window resizing. I figure I am not using them quite
correctly but haven't really been able to figure out what I'm doing.

Any ideas?

thanks in advance
Aaron

---

