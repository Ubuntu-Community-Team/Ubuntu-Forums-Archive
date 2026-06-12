---
title: "[SOLVED] [wxPython] Printing to a text area"
date: 2008-12-05
forum: Programming Talk
---

### Post by dodle on 2008-12-05
I'm going to have to get a wxPython book, because I keep running into problems that I can't find solutions for in the tutorials.  I've seen this done with pyGtk and Glade, but can't remember how.

What I want to do is print some text to a text area from an input area.  I've been able to do the following to get text to print from a button:[PHP]import wx

class MainWindow(wx.Frame):
    def __init__(self, parent, ID, title):
        wx.Frame.__init__(self, parent, ID, title,wx.DefaultPosition,
                            wx.Size(205,220),
                            wx.DEFAULT_FRAME_STYLE & ~ (wx.RESIZE_BORDER |
                            wx.RESIZE_BOX | wx.MAXIMIZE_BOX))
        
        # ------ Area for the text output of pressing button
        textarea = wx.TextCtrl(self, -1,
                                style=wx.TE_MULTILINE|wx.BORDER_SUNKEN|wx.TE_READONLY|
                                wx.TE_RICH2, size=(200,100))
        self.usertext = textarea
        
        # ------ Area for the user's controls
        userin = wx.Panel(self, -1, (0,100), (200,100))

        wx.StaticText(userin, -1, "Type\nHere", pos=(15,0))
        wx.TextCtrl(userin, -1, "", pos=(48,5))
        Press = wx.Button(userin, -1, "Press", (60,30))
        
        Press.Bind(wx.EVT_BUTTON, self.inserttext)
    
    def inserttext(self, event):
        self.usertext.write("hiya ")

class MainApp(wx.App):
    def OnInit(self):
        myWindow = MainWindow(None, -1, "Text to Textarea")
        myWindow.Show(True)
        self.SetTopWindow(myWindow)
        return(True)

AppStart = MainApp(0)
AppStart.MainLoop()[/PHP]But what I would like to do is take the text that is input in the "Type Here" box, and display it in the upper text area when the button is presses.  Could someone help me with this.  I know this is basic programming, but I am a newby all together.  Thanks in advance.

Edit: Also, this is not as important right now, I would like the text from the "Type Here" area to be cleared after the button is pressed.

---

### Post by dodle on 2008-12-05
Can I used wx.DataObject to do this?

Edit: I just figured out how to clear "Type Here" with Clear().  Yessssss!!!!!  But I still need to figure out how to transfer it to the upper text area.

---

### Post by dodle on 2008-12-05
Figured it out!  Here it is:[PHP]import wx

class MainWindow(wx.Frame):
    def __init__(self, parent, ID, title):
        wx.Frame.__init__(self, parent, ID, title,wx.DefaultPosition,
                            wx.Size(205,220),
                            wx.DEFAULT_FRAME_STYLE & ~ (wx.RESIZE_BORDER |
                            wx.RESIZE_BOX | wx.MAXIMIZE_BOX))
        
        # ------ Area for the text output of pressing button
        textarea = wx.TextCtrl(self, -1,
                                style=wx.TE_MULTILINE|wx.BORDER_SUNKEN|wx.TE_READONLY|
                                wx.TE_RICH2, size=(200,100))
        self.usertext = textarea
        
        # ------ Area for the user's controls
        userin = wx.Panel(self, -1, (0,100), (200,100))

        wx.StaticText(userin, -1, "Type\nHere", pos=(15,0))
        
        # ------ Area for user to input text
        userbox = wx.TextCtrl(userin, -1, "", pos=(48,5))
        self.box1 = userbox
        
        # ------ Button to take text from userbox and place it in textarea
        Press = wx.Button(userin, -1, "Press", (60,30))
        
        Press.Bind(wx.EVT_BUTTON, self.inserttext)
                
    
    def inserttext(self, event):
        getit = self.box1.GetLineText(1)
        print getit
        self.box1.Clear()
        self.usertext.AppendText(getit)
    
    def mouseclick(self, event):
        
        self.box1.Clear()

class MainApp(wx.App):
    def OnInit(self):
        myWindow = MainWindow(None, -1, "Text to Textarea")
        myWindow.Show(True)
        self.SetTopWindow(myWindow)
        return(True)

AppStart = MainApp(0)
AppStart.MainLoop()  [/PHP]Thanks to [http://wxpython.org/docs/api/wx.TextCtrl-class.html.]("http://wxpython.org/docs/api/wx.TextCtrl-class.html")

---

