---
title: "Python - wx.StaticText expand to the left?"
date: 2009-04-18
forum: Programming Talk
---

### Post by dodle on 2009-04-18
I am trying to create a caculator screen widget, but I am having problems with the display.  Whenever I expand the StaticText's label with more characters, it expands to the right so the characters disappear out of the widget's view.  

[php]import wx

class Screen(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title, wx.DefaultPosition, wx.DefaultSize)#size=(100,35), style=wx.SUNKEN_BORDER)
        
        # Attributes for Calculator Screen
        #self.AcceptsFocus()
        #self.AcceptsFocusFromKeyboard()
        #self.CenterOnParent()
        self.SetCursor(wx.StockCursor(wx.CURSOR_IBEAM))
        
        # Colors for display
        xwhite = "#ffffff"
        xblack = "#000000"
        
        self.SetBackgroundColour(xblack)
        self.SetForegroundColour(xwhite)
        
        # Calculator Display
        self.disp_out = wx.StaticText(self, -1, "0.")
        self.disp_out.SetForegroundColour(xwhite)
        
        # Stores values to later be added to the display
        self.num_key = None
        self.num_key = self.Bind(wx.EVT_KEY_DOWN, self.OnKey)
        
        # Layout of the display
        h_sizer = wx.BoxSizer(wx.HORIZONTAL)
        h_sizer.Add(self.disp_out, 1, wx.ALIGN_CENTER_VERTICAL|wx.RIGHT, 5)
        
        screen_sizer = wx.BoxSizer(wx.VERTICAL)
        screen_sizer.Add(h_sizer, 1, wx.ALIGN_RIGHT)
        
        self.SetAutoLayout(True)
        self.SetSizer(screen_sizer)
        self.Layout()
        
    def Clear(self):
        self.disp_out.SetLabel("")
    
    def Oppose(self):
        pass
    
    def GetValue(self):
        pass
    
    def OnGetVal(self, event_object):
        print event_object
        if event_object in (324, 48):
            self.num_key = "0"
        elif event_object in (325, 49):
            self.num_key = "1"
        elif event_object in (326, 50):
            self.num_key = "2"
        elif event_object in (327, 51):
            self.num_key = "3"
        elif event_object in (328, 52):
            self.num_key = "4"
        elif event_object in (329, 53):
            self.num_key = "5"
        elif event_object in (330, 54):
            self.num_key = "6"
        elif event_object in (331, 55):
            self.num_key = "7"
        elif event_object in (332, 56):
            self.num_key = "8"
        elif event_object in (333, 57):
            self.num_key = "9"
        else:
            pass
        return self.num_key

    def OnKey(self, event):
        event_object = event.GetKeyCode()
        dispVal = self.disp_out.GetLabel()
        
        self.OnGetVal(event_object)
        
        dispSplit = dispVal.split(".")
        
        I0 = dispSplit[0].split()
        I0.append(str(self.num_key))
        I0joined = "".join(I0)
        
        dispSplit[0] = I0joined
        
        joinVal = ".".join(dispSplit)
        
        self.disp_out.SetLabel(joinVal)
        self.disp_out.Refresh()

#Remove this when finished
class MyApp(wx.App):
    def OnInit(self):
        frame = Screen(None, -1, "Calc")
        frame.Show(True)
        self.SetTopWindow(frame)
        return True

app = MyApp(0)
app.MainLoop()[/php]

Is there some way to set a boundary on the right side, or just make the text expand to the left?

I've included a screenshot of what it looks like when the text goes out of view.

---

