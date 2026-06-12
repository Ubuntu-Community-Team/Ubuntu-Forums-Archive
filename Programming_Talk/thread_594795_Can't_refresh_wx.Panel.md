---
title: "Can't refresh wx.Panel"
date: 2007-10-28
forum: Programming Talk
---

### Post by spinetingler on 2007-10-28
I'm learning Python and using the wxPython GUI toolkit. I can display and initial image on a panel but when I try to display the next image the first image can still be seen in the background... as the second image is smaller that the first. How do I refresh the panel to remove the image?  :popcorn:

---

### Post by archivator on 2007-10-28
Do you mind giving us some code as your problem seems rather unusual?

---

### Post by Auria on 2007-10-28
Perhaps try to Clear() before drawing?
[http://www.wxwidgets.org/manuals/stable/wx_wxdc.html#wxdcclear](http://www.wxwidgets.org/manuals/stable/wx_wxdc.html#wxdcclear)

---

