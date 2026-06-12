---
title: "Python code works on Windows not Linux"
date: 2011-07-17
forum: Programming Talk
---

### Post by KoolPenguin on 2011-07-17
I cannot figure out why the menu bar is not working on Linux but, it works flawlessly on a Windows platform.  I get no errors when running it on Linux and everything works just no menu bar is displayed. Any help would be appreciated.

Using wxPython 2.8 with Python 2.7, 32 bit install on both machines.

Windows screenshot (sorry, no linux screenshot):

[IMG]http://dl.dropbox.com/u/31531443/crafty-winshot.PNG[/IMG]

```

class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title, wx.DefaultPosition, wx.Size(400, 320))
        menubar = wx.MenuBar()
        file = wx.Menu()
        help = wx.Menu()
        file.Append(10, '&Quit', "Exit Shrewd's Crafty GUI")
        help.Append(11, '&About', "About Shrewd's Crafty GUI")
        menubar.Append(file, '&File')
        menubar.Append(help, '&Help')
        self.SetMenuBar(menubar)
        wx.EVT_MENU(self, 11, self.OnAbout)
        wx.EVT_MENU(self, 10, self.OnClose)
        sizer = wx.BoxSizer(wx.VERTICAL)
        
        gs = wx.GridSizer(4, 2, 10, 5)
        gs.AddMany([(wx.Button(self, 1, 'Install Minecraft'), 0, wx.EXPAND),
                    (wx.Button(self, 2, 'Install Minecraft Server'), 0, wx.EXPAND),
                    (wx.Button(self, 3, 'Remove Minecraft'), 0, wx.EXPAND),
                    (wx.Button(self, 4, 'Remove Minecraft Server'), 0, wx.EXPAND),
                    (wx.Button(self, 5, 'Play Minecraft'), 0, wx.EXPAND),
                    (wx.Button(self, 6, 'Start Minecraft Server'), 0, wx.EXPAND),
                    (wx.Button(self, 7, 'Install Minecraft Mod'), 0, wx.EXPAND),
                    (wx.Button(self, 10, 'Close Crafty GUI'), 0, wx.EXPAND)])
        
        sizer.Add(gs, 1, wx.EXPAND)

        self.SetSizer(sizer)
        self.statusbar = self.CreateStatusBar()
        self.Centre()

        self.Bind(wx.EVT_BUTTON, self.OnInstallMine, id=1)
        self.Bind(wx.EVT_BUTTON, self.OnPlayMine, id=5)
        self.Bind(wx.EVT_BUTTON, self.OnClose, id=10)

```

Thanks
--
Chris

---

