---
title: "parent and child windows"
date: 2008-08-29
forum: Programming Talk
---

### Post by Tiri on 2008-08-29
Alrighty, been looking for an answer to this for a bit, was just wondering if there was anyway to close a parent frame from a child panel in python. I've tried a few things but I havn't had any luck, and at this point any help would be appreciated. :(

class Buttons(wx.Panel):
    def __init__(self,parent,id):
        wx.Panel.__init__(self,parent,id)
        sizer = wx.GridSizer(1, 3, 2, 2)
        sizer.Add(wx.Button(self, 102, 'Close', size=(50, -1)))
        self.SetSizer(sizer)
        self.Bind(wx.EVT_BUTTON, self.OnExit, id=102)

    def OnExit(self, event):
        *insert closing code here*

That is where im trying to close my parent from.

---

