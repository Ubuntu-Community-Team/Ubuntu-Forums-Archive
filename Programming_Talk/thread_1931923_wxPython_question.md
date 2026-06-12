---
title: "wxPython question"
date: 2012-02-26
forum: Programming Talk
---

### Post by chevloschelios on 2012-02-26
Hi guys,

I am making GUI with wxPython and I wanna make something like prompt.
 I have TextCtrl and I want to type commands into it and after pressing  Enter execute it. I cant find way how to process text with pressing  Enter. 

Can somebody help me with this problem ?
Thank you

---

### Post by cgroza on 2012-02-28
You have to pass the wx.TE_PROCESS_ENTER flag to the text control when you create it.
Then you can bind the event wx.EVT_TEXT_ENTER to a function and do everything you need from there.

C++ documentation at:
[http://docs.wxwidgets.org/2.8/wx_wxtextctrl.html](http://docs.wxwidgets.org/2.8/wx_wxtextctrl.html)


There is wxPython documentation, but it is usually less detailed.

---

