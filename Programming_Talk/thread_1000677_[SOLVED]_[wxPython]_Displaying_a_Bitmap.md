---
title: "[SOLVED] [wxPython] Displaying a Bitmap"
date: 2008-12-03
forum: Programming Talk
---

### Post by dodle on 2008-12-03
I've found some tutorials on how to display a picture, but that's as far as the tutorials go.  I need to display a picture in a sub-window (I guess you would call it), and I can't figure out how.

Here is my script:[PHP]import wx

MenuItem_exit = 101
MenuItem_about = 100

class MainWindow(wx.Frame):
    def __init__(self, parent, ID, title):
        wx.Frame.__init__(self, parent, ID, title,
                        wx.DefaultPosition, wx.Size(800, 600),
                        wx.DEFAULT_FRAME_STYLE & ~ (wx.RESIZE_BORDER |
                        wx.RESIZE_BOX | wx.MAXIMIZE_BOX))
        
        self.Bind(wx.EVT_CLOSE, self.QuitGame)

        self.CreateStatusBar()
        self.SetStatusText("Active")
        
        self.FirePic = wx.Bitmap('display/fire.bmp')
        #wx.EVT_PAINT(self, self.ShowBack)

        
        white = wx.Colour(255, 255, 255)
        black = wx.Colour(0, 0, 0)
        red = wx.Colour(255, 0, 0)
        green = wx.Colour(0, 255, 0)
        blue = wx.Colour(0, 0, 255)
        yellow = wx.Colour(255, 255, 0)
        dblue = wx.Colour(0,0,162)
        mygreen = wx.Colour(10,133,2)
        
        file = wx.Menu()
        help = wx.Menu()
        
        screen = wx.Window(self, -1, (0, 0), (790, 349), style=wx.BORDER_SUNKEN)
        screen.SetBackgroundColour(mygreen)
        #wx.EVT_PAINT(screen, self.ShowBack)

        controls = wx.Panel(self, -1, (0, 350), (800, 250))
        north = wx.Button(controls, -1, "North", (365,5))
        south = wx.Button(controls, -1, "South", (365,55))
        east = wx.Button(controls, -1, "East", (450,30))
        west = wx.Button(controls, -1, "West", (280,30))
        search1 = wx.Button(controls, -1, "Search", (365, 30))


        file.Append(MenuItem_exit, "E&xit", "Quit the game?")
        
        help.Append(MenuItem_about, "&About", "About the game")
        
        MenuBar = wx.MenuBar()
        MenuBar.Append(file, "&File")
        MenuBar.Append(help, "&Help")
        
        self.SetMenuBar(MenuBar)
        
        wx.EVT_MENU(self, MenuItem_exit, self.QuitGame)
        wx.EVT_MENU(self, MenuItem_about, self.AboutGame)
        
        self.Centre()
    
        
    def QuitGame(self, event):
        dlg = wx.MessageDialog(self, 
            "Do you really want to quit? All information will be lost.",
            "Confirm Exit", wx.OK|wx.CANCEL|wx.ICON_QUESTION)
        result = dlg.ShowModal()
        dlg.Destroy()
        if result == wx.ID_OK:
            self.Destroy()
    
    def ShowBack(self,event):
        bg = wx.PaintDC(self)
        bg.DrawBitmap(self.FirePic, 0, 0)
    
    def AboutGame(self, event):
        about_text = "About this Game"
        dlg = wx.MessageDialog(self, "\
This game\n\
Created by Deluge 2008",
                                about_text, wx.OK)
        dlg.ShowModal()
    

class Game(wx.App):
    def OnInit(self):
        frame = MainWindow(None, -1, "MyGame")
        frame.Show(True)
        self.SetTopWindow(frame)
        return(True)

app = Game(0)
app.MainLoop()[/PHP]The upper window, called "screen", is where I want the bitmap to be displayed.  That's all I want, to display as soon as the program is run.  Do I need to use something other than a wx.Window?

---

### Post by dodle on 2008-12-09
Got it figured out.  [PHP]wx.StaticBitmap(self, wx.Bitmap("path/to/bitmap.bmp"), size, pos)[/PHP]

---

