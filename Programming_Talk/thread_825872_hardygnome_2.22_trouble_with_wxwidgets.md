---
title: "hardy/gnome 2.22 trouble with wxwidgets"
date: 2008-06-11
forum: Programming Talk
---

### Post by johnnyb01 on 2008-06-11
I'm running the same wxPython code on two different machines. One of them had Gutsy until yesterday (now Hardy), the other one has been Hardy for awhile.

My application makes its own hotkeys using callbacks based on wx.EVT_CHAR. Under Gutsy, this worked fine, but it doesn't work under Hardy -- the callbacks never occur. Other callbacks (like mouse clicks) still work as always. I suspect this may be some compatibility problem between Wx (2.8.7.1) the new version of Gnome (2.22).

Has anybody else experienced this?

---

