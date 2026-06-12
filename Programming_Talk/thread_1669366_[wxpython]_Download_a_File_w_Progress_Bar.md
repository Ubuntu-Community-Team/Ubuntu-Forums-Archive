---
title: "[wxpython] Download a File w/ Progress Bar"
date: 2011-01-17
forum: Programming Talk
---

### Post by Pyro.699 on 2011-01-17
Hello,

I'm looking for some help when it comes to giving the user feedback on a single files download progress. I have several questions and i will try and make them as straightforward and to-the-point as i can.

[LIST]
[*]How do you get the size of the file downloading and its current progress. I am using a HTTP wrapper and am able to get the headers... Im guessing that it is located within 'Content-Length'
[*]Once we have the file size how is it that i get an accurate depiction of how much the file has already been downloaded.
[*]With as little work as possible how do i create a [_wx.ProgressDialog_](http://www.wxpython.org/docs/api/wx.ProgressDialog-class.html). The file gets downloaded in a Non-Gui thread, and [_wx.PySimpleApp_](http://www.wxpython.org/docs/api/wx.PySimpleApp-class.html) has yet to be declared. So for a good example of how to do this could be as simple as [_this_](http://www.java2s.com/Tutorial/Python/0380__wxPython/Aprogressbox.htm).
[*]I have tried just starting an app and creating the dialog in the same thread, but it hangs... Im not really sure how to properly do this and need a good hand xD
[/LIST]

If there are any more questions id be happy to answer them the best i can.

Thanks
~Cody

---

