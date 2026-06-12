---
title: "Faulty wxPython Code"
date: 2010-02-17
forum: Programming Talk
---

### Post by TehCodr on 2010-02-17
Hi, I was having a bit of trouble with a GUI toolkit for Python, wxPython.

I'm trying to make it activate different windows depending on the button/menu item clicked but It says __init__ takes 3 arguments, and only 2 are given for all of my settings files.

This is the content of the main launcher.py:

```
import wx
import videosettings
import keysettings
import mousesettings
import usersettings
import enetsettings
import audiosettings
import commands
import py_compile

ID_VIDEO=101
ID_AUDIO=101
ID_MOUSE=101
ID_KEYS=101
ID_USER=101
ID_ENET=101
ID_EXIT=110

app=wx.PySimpleApp()

class gamesettings(wx.Frame):
    def __init__(self, parent, id):
        wx.Frame.__init__(self, parent, id, "Game Settings", size=(1024,768))
        panel=wx.Panel(self)
        Game=wx.MenuBar()
        About=wx.Menu()
        About.Append(ID_VIDEO, "&Video Settings")
        About.Append(ID_AUDIO, "&Audio Settings")
        About.Append(ID_MOUSE, "&Mouse Settings")
        About.Append(ID_KEYS, "Key&board Settings")
        About.Append(ID_USER, "&User Settings")
        About.Append(ID_ENET, "&Connection Settings")
        About.Append(ID_EXIT, "E&xit")
        Game.Append(About, "Project XS17")
        self.SetMenuBar(Game)
        
        VideoMenu=wx.EVT_MENU(self, ID_VIDEO, videosettings.videosettings)
        AudioMenu=wx.EVT_MENU(self, ID_AUDIO, audiosettings.audiosettings)
        MouseMenu=wx.EVT_MENU(self, ID_MOUSE, mousesettings.mousesettings)
        KeyMenu=wx.EVT_MENU(self, ID_KEYS, keysettings.keysettings)
        UserMenu=wx.EVT_MENU(self, ID_USER, usersettings.usersettings)
        EnetMenu=wx.EVT_MENU(self, ID_ENET, enetsettings.enetsettings)
        
        
        VideoSettings=wx.Button(panel,label="Video Settings", pos=(439,20), size=(110,30))
        VideoButton = self.Bind(wx.EVT_BUTTON, videosettings.videosettings, VideoSettings)
        AudioSettings=wx.Button(panel,label="Audio Settings", pos=(439,50), size=(110,30))
        AudioButton=self.Bind(wx.EVT_BUTTON, audiosettings.audiosettings, AudioSettings)
        MouseSettings=wx.Button(panel,label="Mouse Settings", pos=(439,80), size=(110,30))
        MouseButton=self.Bind(wx.EVT_BUTTON, mousesettings.mousesettings, MouseSettings)
        KeySettings=wx.Button(panel,label="Keyboard Settings", pos=(427,110), size=(135,30))
        KeyButton=self.Bind(wx.EVT_BUTTON, keysettings.keysettings, KeySettings)
        UserSettings=wx.Button(panel,label="User Settings", pos=(439,140), size=(110,30))
        UserButton=self.Bind(wx.EVT_BUTTON, usersettings.usersettings, UserSettings)
        EnetSettings=wx.Button(panel,label="Connection Settings", pos=(422,170), size=(145,30))
        EnetButton=self.Bind(wx.EVT_BUTTON, enetsettings.enetsettings, EnetSettings)
        

if __name__=='__main__':
    frame=gamesettings(parent=None,id=-1)
    frame.Show()
    app.MainLoop()
    if wx.Event(id=0, eventType=wx.EVT_BUTTON) == VideoButton:
        frame=videosettings(parent=None,id=-1)
    elif wx.Event(id=0, eventType=wx.EVT_BUTTON) == AudioButton:
        frame=audiosettings(parent=None,id=-1)
    elif wx.Event(id=0, eventType=wx.EVT_BUTTON) == KeyButton:
        frame=keysettings(parent=None,id=-1)    
    elif wx.Event(id=0, eventType=wx.EVT_BUTTON) == MouseButton:
        frame=mousesettings(parent=None,id=-1)
    elif wx.Event(id=0, eventType=wx.EVT_BUTTON) == UserButton:
        frame=usersettings(parent=None,id=-1)
    elif wx.Event(id=0, eventType=wx.EVT_BUTTON) == EnetButton:
        frame=enetsettings(parent=None,id=-1)
    else:
        frame=gamesettings(parent=None,id=-1)
    frame.Show()
    app.MainLoop()
```

and a settings file looks like this (They're all identical for now, but named different):

```
import wx
import videosettings
import keysettings
import mousesettings
import usersettings
import enetsettings

ID_VIDEO=101
ID_AUDIO=101
ID_MOUSE=101
ID_KEYS=101
ID_USER=101
ID_ENET=101
ID_EXIT=110

class audiosettings(wx.Frame):
    def __init__(self, parent, id, title, size):
        wx.Frame.__init__(self, parent, id, "Audio Settings", size=(1024,768))
        panel=wx.Panel(self)
        Game=wx.MenuBar()
        About=wx.Menu()
        About.Append(ID_VIDEO, "&Video Settings")
        About.Append(ID_AUDIO, "&Audio Settings")
        About.Append(ID_MOUSE, "&Mouse Settings")
        About.Append(ID_KEYS, "Key&board Settings")
        About.Append(ID_USER, "&User Settings")
        About.Append(ID_ENET, "&Connection Settings")
        About.Append(ID_EXIT, "E&xit")
        Game.Append(About, "Project XS17")
        self.SetMenuBar(Game)
        
        wx.EVT_MENU(self, ID_VIDEO, videosettings.videosettings)
        wx.EVT_MENU(self, ID_AUDIO, audiosettings.audiosettings)
        wx.EVT_MENU(self, ID_MOUSE, mousesettings.mousesettings)
        wx.EVT_MENU(self, ID_KEYS, keysettings.keysettings)
        wx.EVT_MENU(self, ID_USER, usersettings.usersettings)
        wx.EVT_MENU(self, ID_ENET, enetsettings.enetsettings)
```

At __init__, I need a third argument or something

Thanks,
TehCodr

---

