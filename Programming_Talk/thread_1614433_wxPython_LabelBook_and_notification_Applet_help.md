---
title: "wxPython LabelBook and notification Applet help"
date: 2010-11-05
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-11-05
I am making a menu app in wxPython that I want to be 'pretty'. I need to know 2 things, although the first is much more important.
1. How do I actually make a labelbook? I have the wxPython demo and it gives a LabelBook demo, but I am finding it hard to comprehend and replicate without exactly replicating. I have successfully imported the labelbook module, and I have a window all set up and ready for it, even automatically positioned in the bottom right corner! But I am stuck with a blank window because I can't add the LabelBook to my BoxSizer. It says:
```
    sizer.Add(labelBook, 0, wx.ALL, 10)
  File "/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/_core.py", line 12681, in Add
    return _core_.Sizer_Add(*args, **kwargs)
TypeError: wx.Window, wx.Sizer, wx.Size, or (w,h) expected for item

``` (That's only the relevant part)
So how do I get past that error? I do need a BoxSizer because I plan to add GradientButtons to the bottom later on. I need an example of how to make the LabelBook (in "def labelBook(self)" form with a couple pages) as well

2. How can I make a Notification area applet in wxPython? I have made on in pygtk before, so do you think it would be easier to make an "applet.py" in pygtk to import into my main script? I do know how to do that already, but I heard there was a way to do it in pure wxPython instead.

3. (this isn't even worth calling a question and it is really not important at this time) How can I make the window corners smooth if I remove the window border? I will probably figure this out when I start reading up on pyCairo, but I would rather do it with wx if possible.

Thanks in advance guys! (And don't make it too easy for me, I want to learn from this)

---

### Post by Crazedpsyc on 2010-11-07
Bump?

---

### Post by Crazedpsyc on 2010-11-08
Still nobody? If there's any other info that would be useful, I'll try to get it

---

### Post by robots.jpg on 2010-11-09
You should post your code, especially the part where you define **labelBook**. The error suggests that it can't be added to a sizer because whatever type of object it is, it doesn't inherit wx.Window (which it should) or wx.Sizer.  If nothing else, run type(labelBook) on it and see what that returns.

---

### Post by Crazedpsyc on 2010-11-09
type(LB) (after import wx.lib.agw.labelbook as LB) gives "<type 'module'>
here's my script:
```
#!/usr/bin/env python
import wx
import os
try:
    from agw import labelbook as LB
    from agw.fmresources import *
except ImportError: # if it's not there locally, try the wxPython lib.
    import wx.lib.agw.labelbook as LB
    from wx.lib.agw.fmresources import *

try:
    from agw import gradientbutton as GB
    bitmapDir = "bitmaps/"
except ImportError: # if it's not there locally, try the wxPython lib.
    import wx.lib.agw.gradientbutton as GB
    bitmapDir = "agw/bitmaps/"

class MyFrame(wx.Frame):
    """
    This is MyFrame.  It just shows a few controls on a wxPanel,
    and has a simple menu.
    """
    def __init__(self, parent, title):
        wx.Frame.__init__(self, parent, -1, title, pos=(1020, 200), size=(350, 500))

       

        # Now create the Panel to put the other controls on.
        panel = wx.Panel(self)

        # Use a sizer to layout the controls, stacked vertically and with
        # a 10 pixel border around each
        sizer = wx.BoxSizer(wx.VERTICAL)

        panel.SetSizer(sizer)
        panel.Layout()

        bitmap = wx.Bitmap("buttonpic.png", wx.BITMAP_TYPE_PNG)
        self.xbtn = GB.GradientButton(panel, -1, bitmap, "GradientButton")
    print "Binding events to buttons"
        self.BindEvents(self.xbtn)
    print "Setting winicon"
        winIcon = wx.Icon('pic.png', wx.BITMAP_TYPE_PNG)
        self.SetIcon(winIcon)


    def OnTimeToClose(self, event):
        print "Exiting"
        self.Close()

    def OnFunButton(self, evt):
        """Event handler for the button click."""
        print "FunButton Clicked"

    def labelBook(self):
    lB1 = LB.LabelBook()
        lB1._init_(lB1, MyFrame, size=(340, 490))
        lB1.CreateImageContainer(lB1)

    def BindEvents(self, button):
        self.Bind(wx.EVT_BUTTON, self.OnTimeToClose(self), self.xbtn)

class MyApp(wx.App):
    def OnInit(self):
        frame = MyFrame(None, "Program 0.1")
        self.SetTopWindow(frame)

        print "Program V.0.1"

        frame.Show(True)
        return True
        
app = MyApp()
app.MainLoop()


```and here is the demo code:
```
import wx
import wx.lib.colourselect as csel
import random

import os
import sys

try:
    dirName = os.path.dirname(os.path.abspath(__file__))
except:
    dirName = os.path.dirname(os.path.abspath(sys.argv[0]))

bitmapDir = os.path.join(dirName, 'bitmaps')
sys.path.append(os.path.split(dirName)[0])

try:
    from agw import labelbook as LB
    from agw.fmresources import *
except ImportError: # if it's not there locally, try the wxPython lib.
    import wx.lib.agw.labelbook as LB
    from wx.lib.agw.fmresources import *

import images

_pageTexts = ["Hello", "From", "wxPython", "LabelBook", "Demo"]
_pageIcons = ["roll.png", "charge.png", "add.png", "decrypted.png", "news.png"]
_pageColours = [wx.RED, wx.GREEN, wx.WHITE, wx.BLUE, "Pink"]

#----------------------------------------------------------------------
class SamplePane(wx.Panel):
    """
    Just a simple test window to put into the LabelBook.
    """
    def __init__(self, parent, colour, label):

        wx.Panel.__init__(self, parent, style=wx.BORDER_SUNKEN)
        self.SetBackgroundColour(colour)

        label = label + "\nEnjoy the LabelBook && FlatImageBook demo!"
        static = wx.StaticText(self, -1, label, pos=(10, 10))        

#----------------------------------------------------------------------

class LabelBookDemo(wx.Frame):

    def __init__(self, parent, log):

        wx.Frame.__init__(self, parent)

        self.initializing = True

        self.log = log

        self.splitter = wx.SplitterWindow(self, -1, style=wx.SP_3D|wx.SP_BORDER|
                                          wx.SP_LIVE_UPDATE|wx.SP_3DSASH)
        self.mainpanel = wx.Panel(self.splitter, -1)
        self.leftpanel = wx.Panel(self.splitter, -1, style=wx.SUNKEN_BORDER)

        self.sizer_3_staticbox = wx.StaticBox(self.leftpanel, -1, "Book Styles")
        self.sizer_4_staticbox = wx.StaticBox(self.leftpanel, -1, "Colours")

        radioList = ["LabelBook", "FlatImageBook"]
        self.labelbook = wx.RadioBox(self.leftpanel, -1, "Book Type", wx.DefaultPosition,
                                     wx.DefaultSize, radioList, 2, wx.RA_SPECIFY_ROWS)

        radioList = ["Left", "Right", "Top", "Bottom"]
        self.bookdirection = wx.RadioBox(self.leftpanel, -1, "Book Orientation",
                                         wx.DefaultPosition, wx.DefaultSize, radioList,
                                         2, wx.RA_SPECIFY_ROWS)

        self.border = wx.CheckBox(self.leftpanel, -1, "Draw Book Border")
        self.onlytext = wx.CheckBox(self.leftpanel, -1, "Show Only Text")
        self.onlyimages = wx.CheckBox(self.leftpanel, -1, "Show Only Images")
        self.shadow = wx.CheckBox(self.leftpanel, -1, "Draw Shadows")
        self.pin = wx.CheckBox(self.leftpanel, -1, "Use Pin Button")
        self.gradient = wx.CheckBox(self.leftpanel, -1, "Draw Gradient Shading")
        self.web = wx.CheckBox(self.leftpanel, -1, "Web Highlight")
        self.fittext = wx.CheckBox(self.leftpanel, -1, "Fit Label Text")
        self.background = csel.ColourSelect(self.leftpanel, -1, "Choose...",
                                            wx.Colour(127, 169, 241), size=(-1, 20))
        self.activetab = csel.ColourSelect(self.leftpanel, -1, "Choose...",
                                           wx.Colour(251, 250, 247), size=(-1, 20))
        self.tabsborder = csel.ColourSelect(self.leftpanel, -1, "Choose...",
                                            wx.Colour(172, 168, 153), size=(-1, 20))
        self.textcolour = csel.ColourSelect(self.leftpanel, -1, "Choose...",
                                            wx.BLACK, size=(-1, 20))
        self.activetextcolour = csel.ColourSelect(self.leftpanel, -1, "Choose...",
                                                  wx.BLACK, size=(-1, 20))
        self.hilite = csel.ColourSelect(self.leftpanel, -1, "Choose...",
                                        wx.Colour(191, 216, 216), size=(-1, 20))

        self.SetProperties()
        self.CreateLabelBook()
        self.DoLayout()

        self.Bind(wx.EVT_RADIOBOX, self.OnBookType, self.labelbook)
        self.Bind(wx.EVT_RADIOBOX, self.OnBookOrientation, self.bookdirection)

        self.Bind(wx.EVT_CHECKBOX, self.OnStyle, self.border)
        self.Bind(wx.EVT_CHECKBOX, self.OnStyle, self.onlytext)
        self.Bind(wx.EVT_CHECKBOX, self.OnStyle, self.onlyimages)
        self.Bind(wx.EVT_CHECKBOX, self.OnStyle, self.shadow)
        self.Bind(wx.EVT_CHECKBOX, self.OnStyle, self.pin)
        self.Bind(wx.EVT_CHECKBOX, self.OnStyle, self.gradient)
        self.Bind(wx.EVT_CHECKBOX, self.OnStyle, self.web)
        self.Bind(wx.EVT_CHECKBOX, self.OnStyle, self.fittext)

        self.Bind(csel.EVT_COLOURSELECT, self.OnBookColours, self.background)
        self.Bind(csel.EVT_COLOURSELECT, self.OnBookColours, self.activetab)
        self.Bind(csel.EVT_COLOURSELECT, self.OnBookColours, self.activetextcolour)
        self.Bind(csel.EVT_COLOURSELECT, self.OnBookColours, self.tabsborder)
        self.Bind(csel.EVT_COLOURSELECT, self.OnBookColours, self.textcolour)
        self.Bind(csel.EVT_COLOURSELECT, self.OnBookColours, self.hilite)

        self.Bind(LB.EVT_IMAGENOTEBOOK_PAGE_CHANGING, self.OnPageChanging)
        self.Bind(LB.EVT_IMAGENOTEBOOK_PAGE_CHANGED, self.OnPageChanged)
        self.Bind(LB.EVT_IMAGENOTEBOOK_PAGE_CLOSING, self.OnPageClosing)
        self.Bind(LB.EVT_IMAGENOTEBOOK_PAGE_CLOSED, self.OnPageClosed)


        statusbar = self.CreateStatusBar(2, wx.ST_SIZEGRIP)
        statusbar.SetStatusWidths([-2, -1])
        # statusbar fields
        statusbar_fields = [("LabelBook & FlatImageBook wxPython Demo, Andrea Gavana @ 03 Nov 2006"),
                            ("Welcome To wxPython!")]

        for i in range(len(statusbar_fields)):
            statusbar.SetStatusText(statusbar_fields[i], i)

        self.CreateMenu()

        self.SetSize((800,700))

        self.SetIcon(images.Mondrian.GetIcon())  
        self.CenterOnScreen()

        self.initializing = False
        self.SendSizeEvent()


    def SetProperties(self):

        self.SetTitle("LabelBook & FlatImageBook wxPython Demo ;-)")
        self.pin.SetValue(1)
        self.splitter.SetMinimumPaneSize(120)


    def DoLayout(self):

        mainsizer = wx.BoxSizer(wx.VERTICAL)
        panelsizer = wx.BoxSizer(wx.VERTICAL)
        leftsizer = wx.BoxSizer(wx.VERTICAL)
        sizer_3 = wx.StaticBoxSizer(self.sizer_3_staticbox, wx.VERTICAL)
        sizer_4 = wx.StaticBoxSizer(self.sizer_4_staticbox, wx.VERTICAL)
        gridsizer = wx.FlexGridSizer(6, 2, 5, 5)

        sizer_2 = wx.BoxSizer(wx.VERTICAL)
        sizer_1 = wx.BoxSizer(wx.VERTICAL)
        sizer_1.Add(self.labelbook, 0, wx.ALL, 3)
        leftsizer.Add(sizer_1, 0, wx.ALL|wx.EXPAND, 5)
        sizer_2.Add(self.bookdirection, 0, wx.ALL, 3)
        leftsizer.Add(sizer_2, 0, wx.ALL|wx.EXPAND, 5)

        sizer_3.Add(self.border, 0, wx.ALL, 3)        
        sizer_3.Add(self.onlytext, 0, wx.LEFT|wx.BOTTOM, 3)
        sizer_3.Add(self.onlyimages, 0, wx.LEFT|wx.BOTTOM, 3)
        sizer_3.Add(self.shadow, 0, wx.LEFT|wx.BOTTOM, 3)
        sizer_3.Add(self.pin, 0, wx.LEFT|wx.BOTTOM, 3)
        sizer_3.Add(self.gradient, 0, wx.LEFT|wx.BOTTOM, 3)
        sizer_3.Add(self.web, 0, wx.LEFT|wx.BOTTOM, 3)
        sizer_3.Add(self.fittext, 0, wx.LEFT|wx.BOTTOM, 3)
        leftsizer.Add(sizer_3, 0, wx.ALL|wx.EXPAND, 5)

        label1 = wx.StaticText(self.leftpanel, -1, "Tab Area Background Colour: ")
        label2 = wx.StaticText(self.leftpanel, -1, "Active Tab Colour: ")
        label3 = wx.StaticText(self.leftpanel, -1, "Tabs Border Colour: ")
        label4 = wx.StaticText(self.leftpanel, -1, "Text Colour: ")
        label5 = wx.StaticText(self.leftpanel, -1, "Active Tab Text Colour: ")
        label6 = wx.StaticText(self.leftpanel, -1, "Tab Highlight Colour: ")

        gridsizer.Add(label1, 0, wx.EXPAND|wx.ALIGN_CENTER_VERTICAL|wx.LEFT|wx.RIGHT, 3)
        gridsizer.Add(self.background, 0)
        gridsizer.Add(label2, 0, wx.EXPAND|wx.ALIGN_CENTER_VERTICAL|wx.LEFT|wx.RIGHT, 3)
        gridsizer.Add(self.activetab, 0)
        gridsizer.Add(label3, 0, wx.EXPAND|wx.ALIGN_CENTER_VERTICAL|wx.LEFT|wx.RIGHT, 3)
        gridsizer.Add(self.tabsborder, 0)
        gridsizer.Add(label4, 0, wx.EXPAND|wx.ALIGN_CENTER_VERTICAL|wx.LEFT|wx.RIGHT, 3)
        gridsizer.Add(self.textcolour, 0)
        gridsizer.Add(label5, 0, wx.EXPAND|wx.ALIGN_CENTER_VERTICAL|wx.LEFT|wx.RIGHT, 3)
        gridsizer.Add(self.activetextcolour, 0)
        gridsizer.Add(label6, 0, wx.EXPAND|wx.ALIGN_CENTER_VERTICAL|wx.LEFT|wx.RIGHT, 3)
        gridsizer.Add(self.hilite, 0)

        sizer_4.Add(gridsizer, 1, wx.EXPAND)
        gridsizer.Layout()
        leftsizer.Add(sizer_4, 0, wx.ALL|wx.EXPAND, 5)

        self.leftpanel.SetSizer(leftsizer)
        leftsizer.Layout()
        leftsizer.SetSizeHints(self.leftpanel)
        leftsizer.Fit(self.leftpanel)

        panelsizer.Add(self.book, 1, wx.EXPAND, 0)
        self.mainpanel.SetSizer(panelsizer)
        panelsizer.Layout()

        self.splitter.SplitVertically(self.leftpanel, self.mainpanel, 200)
        mainsizer.Add(self.splitter, 1, wx.EXPAND, 0)

        self.SetSizer(mainsizer)
        mainsizer.Layout()
        self.Layout()


    def CreateLabelBook(self, btype=0):

        if not self.initializing:
            self.Freeze()
            panelsizer = self.mainpanel.GetSizer()
            panelsizer.Detach(0)
            self.book.Destroy()
        else:
            self.imagelist = self.CreateImageList()

        self.EnableChoices(btype)
        style = self.GetBookStyles()

        if btype == 0: # it is a labelbook:
            self.book = LB.LabelBook(self.mainpanel, -1, agwStyle=style)
            if self.bookdirection.GetSelection() > 1:
                self.bookdirection.SetSelection(0)

            self.SetUserColours()                

        else:
            self.book = LB.FlatImageBook(self.mainpanel, -1, agwStyle=style)

        self.book.AssignImageList(self.imagelist)

        for indx, txts in enumerate(_pageTexts):
            label = "This is panel number %d"%(indx+1)
            self.book.AddPage(SamplePane(self.book, _pageColours[indx], label),
                              txts, True, indx)

        self.book.SetSelection(0)            

        if not self.initializing:
            panelsizer.Add(self.book, 1, wx.EXPAND)
            panelsizer.Layout()
            self.GetSizer().Layout()
            self.Layout()
            self.Thaw()

        self.SendSizeEvent()
        wx.CallAfter(self.book.SetAGWWindowStyleFlag, style)


    def EnableChoices(self, btype):

        self.bookdirection.EnableItem(2, btype)
        self.bookdirection.EnableItem(3, btype)
        self.onlyimages.Enable(btype)
        self.onlytext.Enable(btype)
        self.gradient.Enable(not btype)
        self.web.Enable(not btype)
        self.shadow.Enable(not btype)
        self.background.Enable(not btype)
        self.activetab.Enable(not btype)
        self.activetextcolour.Enable(not btype)
        self.textcolour.Enable(not btype)
        self.hilite.Enable(not btype)
        self.tabsborder.Enable(not btype)
        self.fittext.Enable(not btype)


    def GetBookStyles(self):

        style = INB_FIT_BUTTON
        style = self.GetBookOrientation(style)

        if self.onlytext.IsEnabled() and self.onlytext.GetValue():
            style |= INB_SHOW_ONLY_TEXT
        if self.onlyimages.IsEnabled() and self.onlyimages.GetValue():
            style |= INB_SHOW_ONLY_IMAGES
        if self.pin.GetValue():
            style |= INB_USE_PIN_BUTTON
        if self.shadow.GetValue():
            style |= INB_DRAW_SHADOW
        if self.web.GetValue():
            style |= INB_WEB_HILITE
        if self.gradient.GetValue():
            style |= INB_GRADIENT_BACKGROUND
        if self.border.GetValue():
            style |= INB_BORDER
        if self.fittext.IsEnabled() and self.fittext.GetValue():
            style |= INB_FIT_LABELTEXT

        return style


    def CreateImageList(self):

        imagelist = wx.ImageList(32, 32)
        for img in _pageIcons:
            newImg = os.path.join(bitmapDir, "lb%s"%img)
            bmp = wx.Bitmap(newImg, wx.BITMAP_TYPE_PNG)
            imagelist.Add(bmp)

        return imagelist


    def GetBookOrientation(self, style):

        selection = self.bookdirection.GetSelection()
        if selection == 0:
            style |= INB_LEFT
        elif selection == 1:
            style |= INB_RIGHT
        elif selection == 2:
            style |= INB_TOP
        else:
            style |= INB_BOTTOM

        return style


    def OnBookType(self, event):

        self.CreateLabelBook(event.GetInt())
        event.Skip()


    def OnBookOrientation(self, event):

        style = self.GetBookStyles()
        self.book.SetAGWWindowStyleFlag(style)

        event.Skip()


    def OnStyle(self, event):

        style = self.GetBookStyles()
        self.book.SetAGWWindowStyleFlag(style)

        event.Skip()


    def OnBookColours(self, event):

        obj = event.GetId()
        colour = event.GetValue()

        if obj == self.background.GetId():
            self.book.SetColour(INB_TAB_AREA_BACKGROUND_COLOUR, colour)
        elif obj == self.activetab.GetId():
            self.book.SetColour(INB_ACTIVE_TAB_COLOUR, colour)
        elif obj == self.tabsborder.GetId():
            self.book.SetColour(INB_TABS_BORDER_COLOUR, colour)
        elif obj == self.textcolour.GetId():
            self.book.SetColour(INB_TEXT_COLOUR, colour)
        elif obj == self.activetextcolour.GetId():
            self.book.SetColour(INB_ACTIVE_TEXT_COLOUR, colour)
        else:
            self.book.SetColour(INB_HILITE_TAB_COLOUR, colour)

        self.book.Refresh()


    def SetUserColours(self):

        self.book.SetColour(INB_TAB_AREA_BACKGROUND_COLOUR, self.background.GetColour())
        self.book.SetColour(INB_ACTIVE_TAB_COLOUR, self.activetab.GetColour())
        self.book.SetColour(INB_TABS_BORDER_COLOUR, self.tabsborder.GetColour())
        self.book.SetColour(INB_TEXT_COLOUR, self.textcolour.GetColour())
        self.book.SetColour(INB_ACTIVE_TEXT_COLOUR, self.activetextcolour.GetColour())
        self.book.SetColour(INB_HILITE_TAB_COLOUR, self.hilite.GetColour())


    def OnPageChanging(self, event):

        oldsel = event.GetOldSelection()
        newsel = event.GetSelection()
        self.log.write("Page Changing From: " + str(oldsel) + " To: " + str(newsel) + "\n")
        event.Skip()


    def OnPageChanged(self, event):

        newsel = event.GetSelection()
        self.log.write("Page Changed To: " + str(newsel) + "\n")
        event.Skip()


    def OnPageClosing(self, event):

        newsel = event.GetSelection()
        self.log.write("Closing Page: " + str(newsel) + "\n")
        event.Skip()


    def OnPageClosed(self, event):

        newsel = event.GetSelection()
        self.log.write("Closed Page: " + str(newsel) + "\n")
        event.Skip()


    def OnAddPage(self, event):

        pageCount = self.book.GetPageCount()
        indx = random.randint(0, 4)
        label = "This is panel number %d"%(pageCount+1)
        self.book.AddPage(SamplePane(self.book, _pageColours[indx], label),
                          "Added Page", True, indx)


    def OnDeletePage(self, event):

        msg = "Please Enter The Page Number You Want To Remove:"
        dlg = wx.TextEntryDialog(self, msg, "Enter Page")

        if dlg.ShowModal() != wx.ID_OK:
            dlg.Destroy()
            return

        userString = dlg.GetValue()
        dlg.Destroy()

        try:
            page = int(userString)
        except:
            return

        if page < 0 or page > self.book.GetPageCount() - 1:
            return

        self.book.DeletePage(page)


    def OnDeleteAllPages(self, event):

        self.book.DeleteAllPages()        


    def CreateMenu(self):

        menuBar = wx.MenuBar(wx.MB_DOCKABLE)
        fileMenu = wx.Menu()
        editMenu = wx.Menu()
        helpMenu = wx.Menu()

        item = wx.MenuItem(fileMenu, wx.ID_ANY, "E&xit")
        self.Bind(wx.EVT_MENU, self.OnQuit, item)
        fileMenu.AppendItem(item)

        item = wx.MenuItem(editMenu, wx.ID_ANY, "Add Page")
        self.Bind(wx.EVT_MENU, self.OnAddPage, item)
        editMenu.AppendItem(item)

        editMenu.AppendSeparator()

        item = wx.MenuItem(editMenu, wx.ID_ANY, "Delete Page")
        self.Bind(wx.EVT_MENU, self.OnDeletePage, item)
        editMenu.AppendItem(item)

        item = wx.MenuItem(editMenu, wx.ID_ANY, "Delete All Pages")
        self.Bind(wx.EVT_MENU, self.OnDeleteAllPages, item)
        editMenu.AppendItem(item)

        item = wx.MenuItem(helpMenu, wx.ID_ANY, "About")
        self.Bind(wx.EVT_MENU, self.OnAbout, item)
        helpMenu.AppendItem(item)

        menuBar.Append(fileMenu, "&File")
        menuBar.Append(editMenu, "&Edit")
        menuBar.Append(helpMenu, "&Help")

        self.SetMenuBar(menuBar)


    def OnQuit(self, event):

        self.Destroy()


    def OnAbout(self, event):

        msg = "This Is The About Dialog Of The LabelBook & FlatImageBook Demo.\n\n" + \
            "Author: Andrea Gavana @ 03 Nov 2006\n\n" + \
            "Please Report Any Bug/Requests Of Improvements\n" + \
            "To Me At The Following Adresses:\n\n" + \
            "andrea.gavana@gmail.com\n" + "gavana@kpo.kz\n\n" + \
            "Welcome To wxPython " + wx.VERSION_STRING + "!!"

        dlg = wx.MessageDialog(self, msg, "LabelBook wxPython Demo",
                               wx.OK | wx.ICON_INFORMATION)
        dlg.ShowModal()
        dlg.Destroy()


#---------------------------------------------------------------------------


class TestPanel(wx.Panel):
    def __init__(self, parent, log):
        self.log = log
        wx.Panel.__init__(self, parent, -1)

        b = wx.Button(self, -1, " Test LabelBook And FlatImageBook ", (50,50))
        self.Bind(wx.EVT_BUTTON, self.OnButton, b)


    def OnButton(self, evt):
        self.win = LabelBookDemo(self, self.log)
        self.win.Show(True)

#----------------------------------------------------------------------

def runTest(frame, nb, log):
    win = TestPanel(nb, log)
    return win

#----------------------------------------------------------------------


overview = LB.__doc__


if __name__ == '__main__':
    import sys,os
    import run
    run.main(['', os.path.basename(sys.argv[0])] + sys.argv[1:])


```As you might be able to see, I am also having trouble binding a simple event like close to the gradientbutton

The demo depends on some minimodules that came with it

---

