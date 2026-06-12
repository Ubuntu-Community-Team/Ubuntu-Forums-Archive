---
title: "[wx/wxPython] wx.FileDialog: Auto Extension on Save"
date: 2010-07-17
forum: Programming Talk
---

### Post by dodle on 2010-07-17
Is there a way to have a wx.FileDialog automatically add a file extension when the "save" button is pressed? For example if I am saving as a text file, and I call my file "instructions" I want the dialog to add ".txt" to the end of it. And if I name my file "instructions.txt", I want it to leave it alone.

**Edit:** According to the wx docs, I should be able to set a default file extension.  But I can't figure out how.  [http://docs.wxwidgets.org/stable/wx_commondialogsoverview.html#wxfiledialogoverview](http://docs.wxwidgets.org/stable/wx_commondialogsoverview.html#wxfiledialogoverview).  Specifically, I am using Python, but any C++ solutions may be helpful as well.


**Edit:** wx.FileDialog.GetChildren() returns an empty wx.WindowList.

---

