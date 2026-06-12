---
title: "problem binding function to event (wxpython)"
date: 2011-06-08
forum: Programming Talk
---

### Post by Steve5000 on 2011-06-08
Hi I'm new to both python and wxpython (and programming/scripting in general) so please take it easy on me I am still trying to gain knowledge! 

I am writing a simple script that once a button is pressed a cmd is sent to run a process and output a file. I cant get it to work: my code and error is below - any help would be much appreciated 

import wx 
import subprocess 

class window(wx.Frame): 

    def __init__(self,parent,id): 
        wx.Frame.__init__(self,parent,id,'Yahoo', size=(300,200)) 
        panel=wx.Panel(self) 

        pic=wx.Image("Penguins.bmp", wx.BITMAP_TYPE_BMP).ConvertToBitmap() 
        self.button=wx.BitmapButton(panel, -1, pic, pos=(10,10)) 
        self.Bind(wx.EVT_BUTTON, self.doMe, self.button) 
        self.button.SetDefault() 

    def doMe(self, event): 
        print 'starting' 
        p=subprocess.Popen(cmd,stdout=subprocess.PIPE, shell=True) 
        return p.communicate()[0].splitlines() 
        YahooTest = run("YPD.exe Yahoo.html") 
        print 'complete' 
                    
if __name__=='__main__': 
    app=wx.PySimpleApp() 
    frame=window(parent=None,id=-1) 
    frame.Show() 
    app.MainLoop() 



>>> 
starting 
Traceback (most recent call last): 
  File "N:\test\Button Run.py", line 17, in doMe 
    p=subprocess.Popen(cmd,stdout=subprocess.PIPE, shell=True) 
NameError: global name 'cmd' is not defined

---

### Post by Arndt on 2011-06-08
> **Steve5000 said:**
> Hi I'm new to both python and wxpython (and programming/scripting in general) so please take it easy on me I am still trying to gain knowledge! 

I am writing a simple script that once a button is pressed a cmd is sent to run a process and output a file. I cant get it to work: my code and error is below - any help would be much appreciated 

import wx 
import subprocess 

class window(wx.Frame): 

    def __init__(self,parent,id): 
        wx.Frame.__init__(self,parent,id,'Yahoo', size=(300,200)) 
        panel=wx.Panel(self) 

        pic=wx.Image("Penguins.bmp", wx.BITMAP_TYPE_BMP).ConvertToBitmap() 
        self.button=wx.BitmapButton(panel, -1, pic, pos=(10,10)) 
        self.Bind(wx.EVT_BUTTON, self.doMe, self.button) 
        self.button.SetDefault() 

    def doMe(self, event): 
        print 'starting' 
        p=subprocess.Popen(cmd,stdout=subprocess.PIPE, shell=True) 
        return p.communicate()[0].splitlines() 
        YahooTest = run("YPD.exe Yahoo.html") 
        print 'complete' 
                    
if __name__=='__main__': 
    app=wx.PySimpleApp() 
    frame=window(parent=None,id=-1) 
    frame.Show() 
    app.MainLoop() 



>>> 
starting 
Traceback (most recent call last): 
  File "N:\test\Button Run.py", line 17, in doMe 
    p=subprocess.Popen(cmd,stdout=subprocess.PIPE, shell=True) 
NameError: global name 'cmd' is not defined

Doesn't the error message say it all? The variable 'cmd' hasn't been set to anything.

---

