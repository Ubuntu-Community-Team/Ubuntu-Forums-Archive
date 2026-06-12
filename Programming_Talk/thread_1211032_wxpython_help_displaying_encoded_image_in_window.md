---
title: "wxpython: help displaying encoded image in window"
date: 2009-07-12
forum: Programming Talk
---

### Post by DocFox on 2009-07-12
Hi - i am struggling with something here.

i am writing a gui in wxpython, and i want to display a dynamically generate a graphic through html in a wx.htmlWindow widget. i have gotten as far as creating the graphic, converting it to base64 and dropping the base64 encoded graphic into the html. This html displays fine when loaded in firefox.

```

img64 is the encoded graphic file.
myhtml='<html><img src="data:image/png;base64,%s\"></html>' % img64

```

just not in the wx.htmlWindow widget...

any ideas? can wx.htmlWindow handle the <img src:"data ...> format?

ben

---

### Post by DocFox on 2009-07-12
found this thread: [http://groups.google.com/group/wxPython-users/browse_thread/thread/53d41c2c7a490f8d/b602940d6f0ea20e?lnk=gst&q=base64+htmlWindow#b602940d6f0ea20e]("http://groups.google.com/group/wxPython-users/browse_thread/thread/53d41c2c7a490f8d/b602940d6f0ea20e?lnk=gst&q=base64+htmlWindow#b602940d6f0ea20e"):

htmlwindow cant understand base64 encoded graphics, whilst firefox can (hence the phenomenon i mentioned in my first post)

first i convert the png file to a wx.Image object (this works - i can display the wx.Image). then apparently i need to use the wx.MemoryFSHandler:

```

        self.imgRAM=wx.MemoryFSHandler()
        self.imgRAM.AddFile('img.png',self.imagepng, wx.BITMAP_TYPE_PNG)

```
 
this doesnt trigger an error, but when i add this to the html i get nothing...:

```
<img src = "memory:img.png" align="center">
```

is there something i'm missing here? ](*,)

---

### Post by DocFox on 2009-07-13
OK I figured this out. The line **wx.FileSystem.AddHandler(wx.MemoryFSHandler())** is required before creating the MemoryFSHandler object.

I thought i would post a working wx.dialog for any pythoneers looking for the solution to creating a dynamic image in wx.python wx.html.HtmlWindow:

[PHP]#!/usr/bin/env python

import wx
import wx.html
import cStringIO
import Image

import matplotlib
matplotlib.use('Agg')
import matplotlib.pyplot

class DynamicHTMLImage(wx.Dialog):
    
    def __init__(self, parent):
        '''Example dialog to display a dynamically generated image file
           in a wx.html.HtmlWindow'''
        
        wx.Dialog.__init__(self, parent, -1,'Dynamic Image', size=(750,750))

        #get the dynamic image required for the htmlwindow
        self.bitmap=self.getDynamicImage()


        #store the image in wx.FileSystem Object
        #note use of wx.FileSystem and wx.MemoryFSHandler
        #after AddFile, image can be retrieved with 'memory:filename'
        wx.FileSystem.AddHandler(wx.MemoryFSHandler())
        self.imgRAM=wx.MemoryFSHandler()
        self.imgRAM.AddFile('im.png',self.bitmap, wx.BITMAP_TYPE_PNG)

        #sets up html window
        html=wx.html.HtmlWindow(self)
        #now pass the memory address of the image to get the html
        html.SetPage(self.getHTML('memory:im.png'))

        #sets up the dialog with an OK button that dismisses the dialog
        button = wx.Button(self, wx.ID_OK,"OK")
        sizer=wx.BoxSizer(wx.VERTICAL)
        sizer.Add(html,1,wx.EXPAND|wx.ALL,5)
        sizer.Add(button,0, wx.ALIGN_CENTER|wx.ALL,5)
        self.SetSizer(sizer) 
        self.Layout()


        #done!

    def getDynamicImage(self):
        '''In this instance uses matplot to make a dynamic image,
           this could be anything - loading data from file/internet...
        '''
        #make matlab figure
        fig = matplotlib.pyplot.figure()
        ax=fig.add_subplot(111)
        ax.plot([1,2,3])

        #convert to python.Image object 
        imgdata=cStringIO.StringIO()
        fig.savefig(imgdata,format='png')
        imgdata.seek(0)
        im=Image.open(imgdata)

        #convert to wx.Image Object and then to wx.Bitmap
        self.wxim=wx.EmptyImage(im.size[0],im.size[1])
        self.wxim.SetData(im.convert("RGB").tostring())
        self.wximbmp=wx.BitmapFromImage(self.wxim)

        
        return self.wximbmp

    
    def getHTML(self,imagename):
        # a simple html string
        htmltext='''
        <html>        <center>
        <br>Image should display below here:<br>
        <img src="%s" height=450 width=600>
        <br>and above here<br>
        </center>
        </html>
        '''
        #string substitution with objects placed in the wx.FileSystem
        #note: if there are multiple images, imagename could be a tuple
        return htmltext % imagename
        
    
if __name__ == "__main__":

    app=wx.PySimpleApp()
    frm=DynamicHTMLImage(None)
    frm.Show()
    app.MainLoop()
[/PHP]

Best of luck...

---

