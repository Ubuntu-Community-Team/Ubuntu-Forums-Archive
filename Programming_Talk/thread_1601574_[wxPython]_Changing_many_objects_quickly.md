---
title: "[wxPython] Changing many objects quickly"
date: 2010-10-20
forum: Programming Talk
---

### Post by Pyro.699 on 2010-10-20
Hey,

So im teaching myself how to make GUI's using the wxPython libary. Ive been using wxGlade as a building block to help me understand the flow, but ive come into a problem that i cant seem to find a solution for anywheres.

This is my test code:
[php]
#!/usr/bin/env python
import wx, sys, random, time, threading

class MainFrame(wx.Frame):
    def __init__(self, *args, **kwds):
    
        kwds["style"] = wx.DEFAULT_FRAME_STYLE
        wx.Frame.__init__(self, *args, **kwds)
        
        self._x = 14
        self._y = 14
        
        self.labels = []
        for row in xrange(self._y):
            self.labels.append( [] )
            for col in xrange(self._x):
                self.labels[-1].append(wx.StaticText(self, col+row*self._y, "0", style=wx.ALIGN_CENTRE))

        self.runButton = wx.Button(self, -1, "Run")
        
        self.__set_properties()
        self.__do_layout()
        
        self.Bind(wx.EVT_BUTTON, self.buttonPress, self.runButton)

    def __set_properties(self):
        self.SetTitle("MainFrame")
        
        for row in xrange(self._y):
            for col in xrange(self._x):
                self.labels[row][col].SetMinSize((23, 23))
                self.labels[row][col].SetBackgroundColour(wx.Colour(190, 190, 190))
                self.labels[row][col].SetFont(wx.Font(10, wx.SCRIPT, wx.NORMAL, wx.BOLD, 0, ""))

    def __do_layout(self):
        TopSizer = wx.BoxSizer(wx.VERTICAL)
        GridHolder = wx.GridSizer(self._x, self._y)
        
        for row in xrange(self._y):
            for col in xrange(self._y):
                GridHolder.Add(self.labels[row][col], 0, 0, 0)
        
        TopSizer.Add(GridHolder, 1, wx.EXPAND, 0)
        TopSizer.Add(self.runButton, 0, wx.ALIGN_CENTER_HORIZONTAL, 0)    
        self.SetSizer(TopSizer)
        TopSizer.Fit(self)
        self.Layout()
        
    def buttonPress(self, event):
        a = threading.Thread(target=self.doColor)
        a.start()
    
    def doColor(self):
        msColor = [ [  0,  0,  0], #0 - Black
                    [ 75,  0,250], #1 - Blue
                    [  0,130, 20], #2 - Green
                    [250,  0, 40], #3 - Red
                    [ 40,  0,125], #4 - Purple
                    [125,  0, 20], #5 - Maroon
                    [ 40,125,125], #6 - Turquoise
                    [  0,  0,  0], #7 - Black
                    [125,125,125]  #8 - Grey
                ]
                
        for z in range(10000):
            
            rX = random.randrange(0,self._x)
            rY = random.randrange(0,self._y)
            rV = random.randrange(1,9)
            
            self.labels[rY][rX].SetLabel( str(rV) )
            self.labels[rY][rX].SetForegroundColour(wx.Colour(*msColor[rV]))
            sys.stdout.write("%i, %i = %i\n"%(rX,rY,rV))


class MyGui(wx.App):
    def OnInit(self):
        wx.InitAllImageHandlers()
        mFrame = MainFrame(None, -1, "")
        self.SetTopWindow(mFrame)
        mFrame.Show()
        return 1

if __name__ == "__main__":
    runMe = MyGui(0)
    runMe.MainLoop()
[/php]Now, after running this code and hitting the 'Run' button, a few things can happen... one... you get this:
> **The Terminal]
The program 'python' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadGC (invalid GC parameter)'.
  (Details: serial 4770 error_code 13 request_code 56 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously said:**
> 
or...
[quote=The Terminal]
Pango:ERROR:/build/buildd/pango1.0-1.28.0/pango/pango-layout.c:3739:pango_layout_check_lines: assertion failed: (!layout->log_attrs)

or...
The program locks up...

So, im stuck for now... any help?

Thanks
~Cody

---

### Post by Pyro.699 on 2010-10-21
Hey, just wondering if anyone has any ideas :)

Thanks
~Cody

---

