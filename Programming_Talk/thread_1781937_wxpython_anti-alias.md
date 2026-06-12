---
title: "wxpython anti-alias"
date: 2011-06-14
forum: Programming Talk
---

### Post by Mosabama on 2011-06-14
Hello,

is there an anti alias mode for drawing lines in wxpython?

they really look ugly using this:

```

dc = wx.PaintDC(self)
SetDeviceOrigin(40, 240)
dc.SetAxisOrientation(True, True)
dc.SetPen(wx.Pen('#0AB1FF',1))
dc.Drawlines(lines_array)


```

Thanks in advance

---

### Post by Mosabama on 2011-06-19
anyone?

---

