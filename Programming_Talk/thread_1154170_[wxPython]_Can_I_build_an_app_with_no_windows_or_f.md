---
title: "[wxPython] Can I build an app with no windows or frames?"
date: 2009-05-09
forum: Programming Talk
---

### Post by dodle on 2009-05-09
Can I build an application that runs without using any wx.Frame?  I want to show and icon in the taskbar and have all tasks done through it.  I've tried doing the following but it's not working:
[php]import wx

class IconThing(wx.Frame):
    def __init__(self, parent, ID, title):
        wx.Frame.__init__(self, parent, ID, title, wx.DefaultPosition, wx.DefaultSize)
        
        myicon = wx.Icon("icon.png", wx.BITMAP_TYPE_PNG)
        self.tbicon = wx.TaskBarIcon()
        self.tbicon.SetIcon(myicon, "Hello")
        
        self.Bind(wx.EVT_CLOSE, self.onQuit)
        self.tbicon.Bind(wx.EVT_TASKBAR_LEFT_UP, self.onUp)
        
        size = self.GetSize()
        width = size[0]
        height = size[1]
        print size
        print width
        print height
        print width/2
        
        # -- Bouncin Ball
        image = wx.StaticBitmap(self, -1, wx.Bitmap("icon.png", wx.BITMAP_TYPE_PNG))
        image.SetPosition(wx.Point(width/2, height/2))
        
    
    def onQuit(self, event):
        self.tbicon.Destroy()
        self.Destroy()
    
    def onUp(self, event):
        Val = self.IsIconized()
        if Val == False:
            self.Iconize()
            self.Hide()
        elif Val == True:
            self.Restore()
            self.Show()


class IconApp(wx.App):
    def OnInit(self):
        ico = IconThing(None, -1, "Icon Test")
        ico.Show(True)
        self.SetTopWindow(ico)
        return True

app = IconApp(0)
app.MainLoop()[/php]

---

