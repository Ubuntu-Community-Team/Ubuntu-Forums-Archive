---
title: "wxPython, Adjusting Widget size on EVT_SIZE"
date: 2010-12-19
forum: Programming Talk
---

### Post by cgroza on 2010-12-19
Hello everyone!
I am developing a simple text editor and I want to dinamicaly  resize a wx.stc.StyledTextCtrl but I don't seem to make it.

I used the wx.EVT_SIZE to bind the OnSize function to the MainFrame but the terminal spits out an error and all my widgets are gon and just a littel tiny square is left.

I tried with a BoxSizer but I don't have experience with it, and when I tried it it only shower a small portion of one of my buttons.

Here is the code:
```

class Editor(wx.Frame):
    def __init__(self,id,parent):

        #Read Configuration with exterior function

        if  "editorClass.py" not in sys.argv[-1]:
            self.file_to_open = sys.argv[-1]
            self.job_file = True

        else:
            self.job_file = False
            self.file_to_open = "New Document"   #Default Name

        self.MainFrame = wx.Frame.__init__(self,parent,id,'gEcrit', size=(700,500))

        self.NewTabImage = wx.Image('icons/newtab.bmp', wx.BITMAP_TYPE_ANY).ConvertToBitmap()
        self.OpenImage = wx.Image('icons/open.bmp', wx.BITMAP_TYPE_ANY).ConvertToBitmap()
        self.SaveImage = wx.Image('icons/save.bmp', wx.BITMAP_TYPE_ANY).ConvertToBitmap()
        self.SaveAsImage = wx.Image('icons/saveas.bmp', wx.BITMAP_TYPE_ANY).ConvertToBitmap()
        self.ConfigImage = wx.Image('icons/config.bmp', wx.BITMAP_TYPE_ANY).ConvertToBitmap()
        self.QuitImage = wx.Image('icons/quit.bmp', wx.BITMAP_TYPE_ANY).ConvertToBitmap()

        self.nb = wx.aui.AuiNotebook(self)
        self.text_id = 0
        self.NewTab(self.file_to_open,self.file_to_open)
        self.Bind(wx.EVT_SIZE, self.OnSize) #here I am binding the event.
    
    
    def OnSize(self,event):
        NewSize = self.GetSize() #and here I try to set the new size
        self.TextWidget.SetSize(NewSize)
        self.TextWidget.Refresh()



def NewTab(self,nb,file_to_open):
        self.ConfFrame = Config   #Creatinga Config instance

        panel = wx.Panel(self)
        panel.identifierTag = nb
        self.nb.AddPage(panel, nb)

        # Put text_id into a local variable.
        # We do this so that the lambda takes the current value,
        # and not the constantly-incrementing one.
        text_id = self.text_id

        NewButton = wx.BitmapButton(panel, id=8, bitmap = self.NewTabImage,\
         pos=(1,0), size = (64,64))

        OpenButton = wx.BitmapButton(panel, id=-1, bitmap = self.OpenImage,\
         pos=(69,0), size = (64,64))

        SaveButton = wx.BitmapButton(panel, id=-1, bitmap = self.SaveImage,\
         pos=(138,0), size = (64,64))

        SaveAsButton = wx.BitmapButton(panel, id=-1, bitmap = self.SaveAsImage,\
         pos=(207,0), size = (64,64))

        ConfigButton = wx.BitmapButton(panel, id=-1, bitmap = self.ConfigImage,\
         pos=(276,0), size = (64,64))

        QuitButton = wx.BitmapButton(panel, id=-1, bitmap = self.QuitImage,\
         pos=(345,0), size = (64,64))

        self.Bind(wx.EVT_BUTTON, self.CallNewTab , NewButton)
        self.Bind(wx.EVT_BUTTON, self.OpenFile, OpenButton)
        self.Bind(wx.EVT_BUTTON, lambda event: self.Save(event, text_id), SaveButton)
        self.Bind(wx.EVT_BUTTON, lambda event: self.SaveAs(event, text_id), SaveAsButton)
        self.Bind(wx.EVT_BUTTON, self.ConfFrame, ConfigButton)
        self.Bind(wx.EVT_BUTTON, quit, QuitButton)

        h,y = self.GetSize()     #Get height and width of MainFrame
        y -= 100                 #Adjusting the height of TextWidget

        self.TextWidget =  wx.stc.StyledTextCtrl(panel,self.text_id,pos =(0,70), size = (h,y))
        self.TextWidget.SetProperty("fold", "1")
        self.TextWidget.SetMarginType(1, wx.stc.STC_MARGIN_NUMBER)
        self.TextWidget.SetMarginWidth(1,45)
        if file_to_open != "" and nb != "New Document":
            self.TextWidget.LoadFile(file_to_open)
        # Increment the ID.
        self.text_id += 1
```Maybe this is simple and I can't do it becaouse of my ignorance, but please give me some clues of what I am doing wrong.
Thanks.

---

### Post by robots.jpg on 2010-12-20
If you're just trying to resize your TextCtrl to match the frame, save yourself a ton of trouble and learn how to use sizers.  You will eventually lose your mind positioning everything manually like that.  Here's a quick example using BoxSizers with three buttons on top and a text area below (pretending wx.ToolBar doesn't exist):

```

import wx, wx.stc

MIN_SIZE = (400,200)

class MainWindow(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title)

        self.SetMinSize(MIN_SIZE)

        # Widgets
        self.panel = wx.Panel(self, wx.ID_ANY)

        self.button1 = wx.Button(self.panel, wx.ID_ANY, '1')
        self.button2 = wx.Button(self.panel, wx.ID_ANY, '2')
        self.button3 = wx.Button(self.panel, wx.ID_ANY, '3')
        
        self.text = wx.stc.StyledTextCtrl(self.panel, wx.ID_ANY)

        # Horizontal sizer for the buttons
        self.button_sizer = wx.BoxSizer(wx.HORIZONTAL)
        self.button_sizer.Add(self.button1, 0)
        self.button_sizer.Add(self.button2, 0)
        self.button_sizer.Add(self.button3, 0)
                
        # Vertical sizer for the button sizer and text
        self.main_sizer = wx.BoxSizer(wx.VERTICAL)
        self.main_sizer.Add(self.button_sizer, 0, wx.EXPAND)
        self.main_sizer.Add(self.text, 1, wx.EXPAND)

        # Assign the sizer to the panel, and resize it
        self.panel.SetSizer(self.main_sizer)
        self.main_sizer.Fit(self.panel)
        
app = wx.App()
frame = MainWindow(None, wx.ID_ANY, 'The Title')
frame.Show()
app.MainLoop()

```I think that's similar to the layout in your code.  No need to handle the resize event.

---

### Post by cgroza on 2010-12-20
Thank you very much. I waited so much for the answer and now I am very happy!

---

