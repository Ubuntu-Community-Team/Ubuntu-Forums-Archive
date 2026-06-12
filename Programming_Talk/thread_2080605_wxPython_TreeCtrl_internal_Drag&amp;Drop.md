---
title: "wxPython TreeCtrl internal Drag&amp;Drop"
date: 2012-11-04
forum: Programming Talk
---

### Post by jw37 on 2012-11-04
Good datetime.datetime.now() everybody!

I'm trying to do some drag&drop operations in a wx.TreeCtrl but i cannot make it work. I want to drag an item inside the TreeCtrl, not into/from it. The problems is that the EVT_TREE_END_DRAG event does not trigger in the following test example:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import wx

class TestFrame(wx.Frame):
    def __init__(self, *args, **kwds):
        wx.Frame.__init__(self, *args, **kwds)
        self.tree_ctrl_1 = wx.TreeCtrl(
                self,
                style=wx.TR_HAS_BUTTONS|wx.TR_NO_LINES|wx.TR_HIDE_ROOT)

        self.__set_properties()
        self.__do_layout()

        self.Bind(wx.EVT_TREE_BEGIN_DRAG, self._on_begin_drag, self.tree_ctrl_1)
        self.Bind(wx.EVT_TREE_END_DRAG, self._on_end_drag, self.tree_ctrl_1)
        
        root = self.tree_ctrl_1.AddRoot("root")
        self.groups = {
                "Group 1": ["Allison", "Peter", "Fred", "Mary"],
                "Group 2": ["Graham", "Ted", "Donald"]}
        for gr, ls in sorted(self.groups.iteritems()):
            gr_item = self.tree_ctrl_1.AppendItem(root, gr)
            for p in ls:
                self.tree_ctrl_1.AppendItem(gr_item, p)
        self.tree_ctrl_1.ExpandAll()

    def __set_properties(self):
        self.SetTitle("Test Drag'n'Drop")
        self.SetMinSize((300, 400))

    def __do_layout(self):
        sizer_1 = wx.BoxSizer(wx.VERTICAL)
        sizer_1.Add(self.tree_ctrl_1, 1, wx.EXPAND, 0)
        self.SetSizer(sizer_1)
        sizer_1.Fit(self)
        self.Layout()

    def _on_begin_drag(self, event):
        item_id = event.GetItem()
        # Only non-container items can be dragged.
        if self.tree_ctrl_1.ItemHasChildren(item_id):
            event.Veto()
            event.Skip()
            return
        
        txt = self.tree_ctrl_1.GetItemText(item_id)
        print txt
        
        event.Skip()

    def _on_end_drag(self, event):
        print "End drag"
        # here goes the real task: move the item from group to the other group
        event.Skip()


if __name__ == "__main__":
    app = wx.PySimpleApp(0)
    wx.InitAllImageHandlers()
    frame_1 = TestFrame(None, -1, "")
    app.SetTopWindow(frame_1)
    frame_1.Show()
    app.MainLoop()

```I have also messed with the DropSource and DropTarget and all those classes but didn't understood how to use them. Robin Dunn wrote somewhere that for TreeCtrl internal use, the wx.EVT_TREE_BEGIN_DRAG and wx.EVT_TREE_END_DRAG would do the thing. I've messed hours with this, without finding any good example.

python-wxgtk2.8 (2.8.10.1)

Does someone know how to do this?

---

