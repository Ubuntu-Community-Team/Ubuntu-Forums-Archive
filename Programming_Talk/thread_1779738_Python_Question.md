---
title: "Python Question"
date: 2011-06-10
forum: Programming Talk
---

### Post by Mosabama on 2011-06-10
I have the following code:

```
]
#!/usr/bin/python

# linechart.py

import wx

import time

years = ('2003', '2004', '2005')

class LineChart(wx.Panel): 

    x=0
    y=0

    def __init__(self, parent):
        wx.Panel.__init__(self, parent)
        self.SetBackgroundColour('WHITE')

        self.Bind(wx.EVT_PAINT, self.OnPaint)
        #self.Bind(wx.EVT_DRAW, self.OnPaint)
    
    def OnPaint(self, event):
        dc = wx.PaintDC(self)     
        dc.SetDeviceOrigin(40, 240)
        dc.SetAxisOrientation(True, True)
        dc.SetPen(wx.Pen('WHITE'))
        dc.DrawRectangle(1, 1, 300, 200)
        self.DrawAxis(dc)
        self.DrawGrid(dc)
        self.DrawTitle(dc)
        self.DrawData(dc)
        print "yea"

    def DrawAxis(self, dc):
        dc.SetPen(wx.Pen('#0AB1FF'))
        font =  dc.GetFont()
        font.SetPointSize(8)
        dc.SetFont(font)
        dc.DrawLine(1, 1, 300, 1)
        dc.DrawLine(1, 1, 1, 201)

        for i in range(20, 220, 20):
            dc.DrawText(str(i), -30, i+5)
            dc.DrawLine(2, i, -5, i)

        for i in range(100, 300, 100):
            dc.DrawLine(i, 2, i, -5)

        for i in range(3):
            dc.DrawText(years[i], i*100-13, -10)



    def DrawGrid(self, dc):
        dc.SetPen(wx.Pen('#d5d5d5'))

        for i in range(20, 220, 20):
            dc.DrawLine(2, i, 300, i)

        for i in range(100, 300, 100):
            dc.DrawLine(i, 2, i, 200)

    def DrawTitle(self, dc):
        font =  dc.GetFont()
        font.SetWeight(wx.FONTWEIGHT_BOLD)
        dc.SetFont(font)
        dc.DrawText('Historical Prices', 90, 235)


    def DrawData(self, dc):
        #self.getdata()
        dc.SetPen(wx.Pen('#0ab1ff'))
        dc.SetBrush(wx.Brush('orange'))
        #self.getdata()
        dc.DrawCircle(self.x, self.y, 3)

           
    def getdata(self):
        
       
        self.y=self.y + 1
        self.x=self.x + 1
    
class LineChartExample(wx.Frame):
    def __init__(self, parent, id, title):
        wx.Frame.__init__(self, parent, id, title, size=(390, 300))

        panel = wx.Panel(self, -1)
        panel.SetBackgroundColour('WHITE')

        hbox = wx.BoxSizer(wx.HORIZONTAL)
        linechart = LineChart(panel)
        hbox.Add(linechart, 1, wx.EXPAND | wx.ALL, 15)
        panel.SetSizer(hbox)

        self.Centre()
        self.Show(True)



app = wx.App()
LineChartExample(None, -1, 'A line chart')
app.MainLoop()

```

I am trying to plot some data live but here it seems that this program prints only one point and the Drawdata function is called only once.

I want the Drawdata function to be called when ever the Getdata function is called and at the same time I want the getdata function to be called every 1 sec lets say?
How can I do this? and how can I do it with our using alot of CPU and at the same time without using the time.sleep function because it screws wx and nothing will respond to user.

I hope I explained what I need, and sorry for the lengthy code.

Thanks in advance..

---

### Post by cgroza on 2011-06-10
Instead of time.sleep you could use the wx timer classes. About the others, I do not know:
What did you do so far to debug your code?

---

### Post by Mosabama on 2011-06-10
Thank you for your reply,
Can you please tell me where to put the timer?? and how to make the drawing occur every 1 sec for example?

I am not much into python I am new .. so I dont know how to debug what so ever.
I kinda understand the idea of the wx.timer but I dont know what to do with it exactly in this case.
Thanks

---

### Post by cgroza on 2011-06-11
You must create a class that inherits from wxTimer, and overwrite the appropriate methods.

Documentation here:

[http://docs.wxwidgets.org/stable/wx_wxtimer.html](http://docs.wxwidgets.org/stable/wx_wxtimer.html)
[http://www.wxpython.org/docs/api/wx.Timer-class.html](http://www.wxpython.org/docs/api/wx.Timer-class.html)

I am shooting in the dark now, but I think your DrawData is only called once because the events it is binded to only fire once.

---

### Post by Mosabama on 2011-06-11
Thank you very much, the Timer helped alot:

```

 self.timer=wx.Timer(self)
 self.Bind(wx.EVT_TIMER, self.getdata,self.timer)
 self.timer.Start(1000)

```

Now the getdata function is called every 1 sec, and getdata calls the function that draws the data. it works after I made the dc object global.

Thank you again.

---

### Post by cgroza on 2011-06-12
No problem.

---

