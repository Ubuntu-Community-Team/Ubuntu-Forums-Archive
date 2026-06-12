---
title: "Open App by double-Clicking Document File"
date: 2010-11-18
forum: Programming Talk
---

### Post by pauljwells on 2010-11-18
I've written a program in Python/wxPython that saves its data in a file with its own extension.
I want to be able to double-click the data file and have the program open and load the data, much like open office does with doc files etc.
I haven't been able to find the right terms to google to give me any clues!

I'm guessing I need to somehow add *args, **kwargs to one of my classes or methods and bind it to a file-opening method??

The program will be mostly deployed on Windows machines but I'd like to make it work on any platform.

Thanks for any pointers...

---

### Post by worksofcraft on 2010-11-18
> **pauljwells said:**
> I've written a program in Python/wxPython that saves its data in a file with its own extension.
I want to be able to double-click the data file and have the program open and load the data, much like open office does with doc files etc.
I haven't been able to find the right terms to google to give me any clues!

I'm guessing I need to somehow add *args, **kwargs to one of my classes or methods and bind it to a file-opening method??

The program will be mostly deployed on Windows machines but I'd like to make it work on any platform.

Thanks for any pointers...

I think it's about the same for Windows and for Linux too: Just open a folder with one of these files in and right click it. Select "Properties" menu and then the "Open With" tab... hopefully that will be self explanatory and do what you want :)

---

### Post by pauljwells on 2010-11-19
> **worksofcraft said:**
> I think it's about the same for Windows and for Linux too: Just open a folder with one of these files in and right click it. Select "Properties" menu and then the "Open With" tab... hopefully that will be self explanatory and do what you want :)

Nope, that just writes an entry in the register in Windows and I suppose something in a conf file for Nautilus. I would do that manually and in any case need to include it in the installer script.

What I'm trying to find out is how the file is passed to the program as an argument. How would it be done in C or C++ for example?

---

### Post by pauljwells on 2010-11-19
A bit of googling (turns out it all works like 'C') and a lot of trial and error and I've coded this - NOW I can do the 'open with' thing and then double-clicking works.

Think I deserve some :popcorn:

```

import wx
import sys
import frames
import nsc_bmp

class App(wx.App):
    def OnInit(self):
#Splash Screen
        splashImage = nsc_bmp.getNscBmp()
        wx.SplashScreen(splashImage, wx.SPLASH_CENTRE_ON_SCREEN|wx.SPLASH_TIMEOUT, 1000, None, wx.ID_ANY)
        wx.Yield()
#Main Window
        fileOpen = sys.argv[1:]
        frame = frames.MainFrame(fileOpen)
        frame.Center()
        frame.Show(True)
        self.SetTopWindow(frame)
        return True
    
def main():
    app = App(redirect=False)
    app.MainLoop()
    return True

if __name__ == '__main__':
    main()
```

```
class MainFrame(wx.Frame):
    def __init__(self, fileOpen = None):

...

        if fileOpen:
            fileName = ''
            for element in fileOpen:
                fileName += element + ' '
            fileName = fileName[0:-1]
            self.openOnStart(fileName)
            print fileName
            

...

    def openOnStart(self, fileOpen):
        filehandle = open(fileOpen,'r')
        openObject = pickle.load(filehandle)
        #Clever code to determine program version
        self.HoursDB = openObject
        self.refreshAllFields()
        filehandle.close()
        return

```

---

