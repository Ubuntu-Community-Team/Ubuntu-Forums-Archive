---
title: "wxPython, Why &quot;&amp;File&quot;, and not just &quot;File&quot;?"
date: 2010-08-26
forum: Programming Talk
---

### Post by Jackarow on 2010-08-26
While exploring wxpython, I keep running into a reoccurring convention. When creating menus, buttons, and the like, why do people use "&File" and not just plain old "File"? What purpose (if any) does the ampersand serve? Why the seemingly odd, but reoccurring theme?

Just for clarity sake, the following is a sample program, inspired by code from the book "wxPython in Action" by Noel Rappin. Notice the ampersand naming conventions.
> 

import wx

class DiveCalc(wx.Frame):

    def __init__(self, parent, id):
        wx.Frame.__init__(self, parent, id, 'Python Dive App', size=(340,200))
        panel = wx.Panel(self, -1)
        panel.SetBackgroundColour('#00FFFF')
        self.Bind(wx.EVT_CLOSE, self.OnCloseWindow)
        self.createMenuBar()
        self.createTextFields(panel)
        self.createButtonBar(panel)

    def menuData(self):
        return (("&File",
            ("&Open", "Open in status bar", self.OnOpen),
            ("&Quit", "Quit", self.OnCloseWindow)),
            ("&Edit",
            ("&Copy", "Copy", self.OnCopy),
            ("C&ut", "Cut", self.OnCut),
            ("&Paste", "Paste", self.OnPaste)))
            
    def createMenuBar(self):
        menuBar = wx.MenuBar()
        for eachMenuData in self.menuData():
            menuLabel = eachMenuData[0]
            menuItems = eachMenuData[1:]
            menuBar.Append(self.createMenu(menuItems), menuLabel)
        self.SetMenuBar(menuBar)

    def createMenu(self, menuData):
        menu = wx.Menu()
        for eachLabel, eachStatus, eachHandler in menuData:
            menuItem = menu.Append(-1, eachLabel, eachStatus)
            self.Bind(wx.EVT_MENU, eachHandler, menuItem)
        return menu

    def textFieldData(self):
        return (("Depth", (10, 50)),
                ("Time", (10, 80)),
                ("Letter Group", (10, 110)))

    def createTextFields(self, panel):
        for eachLabel, eachPos in self.textFieldData():
            self.createCaptionedText(panel, eachLabel, eachPos)

    def createCaptionedText(self, panel, label, pos):
        static = wx.StaticText(panel, wx.NewId(), label, pos)
        static.SetBackgroundColour("White")
        textPos = (pos[0] + 90, pos[1])
        wx.TextCtrl(panel, wx.NewId(), "", size=(100, -1), pos=textPos)

    def buttonData(self):
        return ((
    
    # Group empty event handlers
    def OnOpen(self, event): pass
    def OnCopy(self, event): pass
    def OnCut(self, event): pass
    def OnPaste(self, event): pass
    def OnCloseWindow(self, event):
                self.Destroy()

                 
if __name__ == '__main__':
    app = wx.PySimpleApp()
    frame = DiveCalc(parent=None, id=-1)
    frame.Show()
    app.MainLoop()


---

### Post by myrtle1908 on 2010-08-26
Not sure about wxPython specifically but normally this auto-maps shortcut keys eg

&File - ALT+F opens File menu

---

### Post by matthew.ball on 2010-08-27
Yeah, it's the underscore that appears on certain menu entries.

I think the actual keyboard shortcut is mapped through an event, but not really sure - it could be done automagically.

---

