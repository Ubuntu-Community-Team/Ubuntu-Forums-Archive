---
title: "[SOLVED] [wxPython] wx.KeyEvent help"
date: 2008-12-08
forum: Programming Talk
---

### Post by dodle on 2008-12-08
What I want to do is activate [COLOR="Blue"]inserttext(self,event)[/COLOR] when the "enter" key is pressed within [COLOR="Blue"]userbox[/COLOR].

Here is my script:[PHP]#! /usr/share/env python

import wx

class MainWindow(wx.Frame):
    def __init__(self, parent, ID, title):
        wx.Frame.__init__(self, parent, ID, title,wx.DefaultPosition,
                            wx.Size(205,220),
                            wx.DEFAULT_FRAME_STYLE & ~ (wx.RESIZE_BORDER |
                            wx.RESIZE_BOX | wx.MAXIMIZE_BOX))
        
        # ------ The Cursor and Font
#        myCursor = wx.CursorFromImage(wx.Image("cursor.bmp"))
#        self.SetCursor(myCursor)
#        myFont = wx.Font(14, "HOBBYHOR.TTF", wx.NORMAL, wx.NORMAL)
#        self.SetFont(myFont)
        
        # ------ Area for the text output of pressing button
        textarea = wx.TextCtrl(self, -1,
                                style=wx.TE_MULTILINE|wx.BORDER_SUNKEN|wx.TE_READONLY|
                                wx.TE_RICH2, size=(200,100))
        self.usertext = textarea
        
        self.extra = "You have typed: "
        
        # ------ Area for the user's controls
        userin = wx.Panel(self, -1, (0,100), (200,100))

        wx.StaticText(userin, -1, "Type\nHere", pos=(15,0))
        
        # ------ Area for user to input text

        userbox = wx.TextCtrl(userin, -1, "", pos=(48,5))
        userbox.SetFocus()
        userbox.SetMaxLength(17)
        self.box1 = userbox
        
        # ------ Button to take text from userbox and place it in textarea
        Press = wx.Button(userin, -1, "Press", (60,30))
        
        Press.Bind(wx.EVT_BUTTON, self.inserttext)                
    
    def inserttext(self, event):
        getit = self.box1.GetLineText(1)
        if getit == "":
            pass
        else:
            print getit
            self.box1.Clear()
            self.usertext.AppendText("%s %s\n" % (self.extra, getit))
    
    
class MainApp(wx.App):
    def OnInit(self):
        myWindow = MainWindow(None, -1, "Text to Textarea")
        myWindow.Show(True)
        self.SetTopWindow(myWindow)
        return(True)

AppStart = MainApp(0)
AppStart.MainLoop()  [/PHP]

---

### Post by dodle on 2008-12-08
Got it!  Here is the solution:  Look for the #####[php]#!/usr/share/env python

import wx

class MainWindow(wx.Frame):
    def __init__(self, parent, ID, title):
        wx.Frame.__init__(self, parent, ID, title,wx.DefaultPosition,
                            wx.Size(205,220),
                            wx.DEFAULT_FRAME_STYLE & ~ (wx.RESIZE_BORDER |
                            wx.RESIZE_BOX | wx.MAXIMIZE_BOX))
        
        # ------ The Cursor and Font
#        myCursor = wx.CursorFromImage(wx.Image("cursor.bmp"))
#        self.SetCursor(myCursor)
#        myFont = wx.Font(14, "HOBBYHOR.TTF", wx.NORMAL, wx.NORMAL)
#        self.SetFont(myFont)
        
        # ------ Area for the text output of pressing button
        textarea = wx.TextCtrl(self, -1,
                                style=wx.TE_MULTILINE|wx.BORDER_SUNKEN|
                                wx.TE_READONLY|
                                wx.TE_RICH2, size=(200,100))
        self.usertext = textarea
        
        self.extra = "You have typed: "
        
        # ------ Area for the user's controls
        userin = wx.Panel(self, -1, (0,100), (200,100))

        wx.StaticText(userin, -1, "Type\nHere", pos=(15,0))
        
        # ------ Area for user to input text
 ###### Here I had to set the style of my TextCtrl to wx.TE_PROCESS_ENTER #####
        userbox = wx.TextCtrl(userin, -1, "", pos=(48,5),
                                        style=wx.TE_PROCESS_ENTER)
        userbox.SetFocus()
        userbox.SetMaxLength(17)
        self.box1 = userbox
        
        # ------ Button to take text from userbox and place it in textarea
        Press = wx.Button(userin, -1, "Press", (60,30))

##### Here I created the event #####
        wx.EVT_TEXT_ENTER(self.box1, -1, self.inserttext)
        Press.Bind(wx.EVT_BUTTON, self.inserttext)                
    
    def inserttext(self, event):
        getit = self.box1.GetValue()
        if getit == "":
            pass
        else:
            print getit
            self.box1.Clear()
            self.box1.SetFocus()
            self.usertext.AppendText("%s %s\n" % (self.extra, getit))
    

class MainApp(wx.App):
    def OnInit(self):
        myWindow = MainWindow(None, -1, "Text to Textarea")
        myWindow.Show(True)
        self.SetTopWindow(myWindow)
        return(True)

AppStart = MainApp(0)
AppStart.MainLoop()  [/php]

---

