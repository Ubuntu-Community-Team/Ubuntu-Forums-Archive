---
title: "WxPython Dynamic Button/list Adding with events"
date: 2010-11-24
forum: Programming Talk
---

### Post by Crazedpsyc on 2010-11-24
I have a simple wxPython app that uses os.listdir to get the contents of a directory, defines an "AddButton" event which creates a wx.Button and binds it to an os.system event based on the button's name, finally it uses this function like this:
```
map(AddButton, dirConts)
``` in which AddButton is the AddButton function (obviously) and dirConts is the output of os.listdir
It looks great until I find that ALL of the buttons are bound to the last event!
Any ideas on how to fix this?

EDIT: The AddButton function binds to os.system('./run ' + app) (the only contents of the directory os.listdir looks at should be the apps, so I defined AddButton(app): which takes the name of each item and uses it here and for the wx.Button title

---

### Post by Arndt on 2010-11-24
> **Crazedpsyc said:**
> I have a simple wxPython app that uses os.listdir to get the contents of a directory, defines an "AddButton" event which creates a wx.Button and binds it to an os.system event based on the button's name, finally it uses this function like this:
```
map(AddButton, dirConts)
``` in which AddButton is the AddButton function (obviously) and dirConts is the output of os.listdir
It looks great until I find that ALL of the buttons are bound to the last event!
Any ideas on how to fix this?

EDIT: The AddButton function binds to os.system('./run ' + app) (the only contents of the directory os.listdir looks at should be the apps, so I defined AddButton(app): which takes the name of each item and uses it here and for the wx.Button title

I find your description somewhat cryptic, but it may make perfect sense. Do you have a small complete program which exhibits the problem?

---

### Post by Crazedpsyc on 2010-11-24
Sure:
```

import wx, os, sys
class MyFrame(wx.Frame):
    def __init__(self, parent, title):
        wx.Frame.__init__(self, parent, -1, title, pos=(-1, -1), size=(350, 500))
        panel = wx.Panel(self)
        vbox = wx.BoxSizer(wx.VERTICAL)
    hbox = wx.BoxSizer()
    vbox.Add(hbox)
        panel.SetSizer(vbox)
        panel.Layout()
    def putAppName(appname, index):
        global torun
        if globals().has_key('torun') == False: torun = []
        torun.append(appname)
    def getAppName():
        global torun
        global ind
        return torun[ind]
    def runApp(blah):
        torun = getAppName()
        os.system('Applications/menu/AppRun ' + torun)
    def addButton(appname):
        appbtn = appname
        appbtn = wx.Button(panel, -1, appname)
        vbox.Add(appbtn, -1)
        global ind
        if globals().has_key('ind') == False: ind = 0
        else: ind = ind + 1
        putAppName(appname, ind)
        # This is where the problem lies. because the button is appbtn each time it must get confused here
        **appbtn.Bind(wx.EVT_BUTTON, runApp)**

    **map(addButton, appdir)**
    appdir = os.listdir('Applications')
    appdir.remove('menu')
class MyApp(wx.App):
    def OnInit(self):
        frame = MyFrame(None, "Test")
        self.SetTopWindow(frame)

        print "Testing..."

        frame.Show(True)
        return True
        
app = MyApp()
app.MainLoop()

```

---

### Post by Arndt on 2010-11-24
> **Crazedpsyc said:**
> Sure:
```

import wx, os, sys
class MyFrame(wx.Frame):
    def __init__(self, parent, title):
        wx.Frame.__init__(self, parent, -1, title, pos=(-1, -1), size=(350, 500))
        panel = wx.Panel(self)
        vbox = wx.BoxSizer(wx.VERTICAL)
    hbox = wx.BoxSizer()
    vbox.Add(hbox)
        panel.SetSizer(vbox)
        panel.Layout()
    def putAppName(appname, index):
        global torun
        if globals().has_key('torun') == False: torun = []
        torun.append(appname)
    def getAppName():
        global torun
        global ind
        return torun[ind]
    def runApp(blah):
        torun = getAppName()
        os.system('Applications/menu/AppRun ' + torun)
    def addButton(appname):
        appbtn = appname
        appbtn = wx.Button(panel, -1, appname)
        vbox.Add(appbtn, -1)
        global ind
        if globals().has_key('ind') == False: ind = 0
        else: ind = ind + 1
        putAppName(appname, ind)
        # This is where the problem lies. because the button is appbtn each time it must get confused here
        **appbtn.Bind(wx.EVT_BUTTON, runApp)**

    **map(addButton, appdir)**
    appdir = os.listdir('Applications')
    appdir.remove('menu')
class MyApp(wx.App):
    def OnInit(self):
        frame = MyFrame(None, "Test")
        self.SetTopWindow(frame)

        print "Testing..."

        frame.Show(True)
        return True
        
app = MyApp()
app.MainLoop()

```

I'm sorry, I'm not able to get this to run. Is this python 3 or 2? I seem to have to add 'self' in lots of places, among other things.

---

### Post by Crazedpsyc on 2010-11-26
python 2, try this one:
```
#!/usr/bin/env python
import os
# 
kill = True
menudirname = 'Applications/menu/'
menudir = os.listdir(menudirname)
try: from configobj import ConfigObj
except ImportError: print "The configuration reading/writing module 'configobj' is not properly installed. On debian based systems you can use 'sudo apt-get install python-configobj'"
#MeEnu should be run from /media/device/PortableAppsLinux/ 
try:
    menudir = os.listdir('./Applications/menu/')
    cdir = True # CorrectDir = True (for later use in reading the config file)
except OSError:
    #attempt to guess the path based on the location of this script
    import sys
    print 'Attempting to find config file. in the future please cd to the PortableAppsLinux directory on your device'
    menudirname = '/media/thumb/PortableAppsLinux/Applications/menu/'

    try: menudir = os.listdir(menudirname)
    except OSError:
        print "There was an error locating the 'menu' directory in your Applications folder. Creating one now..."
        try: 
            os.mkdir(menudirname)
            menudir = os.listdir(menudirname)
        except OSError:
            print "No Applications directory found either. Creating one..."
            os.mkdir("/media/thumb/PortableAppsLinux/Applications/")
            os.mkdir(menudirname)
            menudir = os.listdir(menudirname)
def createConfig():
    config = ConfigObj()
    config.filename = menudirname + 'menu.conf'
    config["MeEnu"] = {}
    config["MeEnu"]["bgcolor"] = "black"
    config["MeEnu"]["btncolor"] = ['black', 'gray', 'white']
    config["MeEnu"]["updsrv"] = "http://my.ip/"
    config["MeEnu"]["updfile"] = "forage/palupd.xml"
    config.write()
if 'menu.conf' in menudir:
    print 'Configuration exists, reading values...'
    if cdir == True:
        conf = ConfigObj(r"Applications/menu/menu.conf")
        print 'bgcolor:', conf['MeEnu']['bgcolor']
        print 'btncolor:', conf['MeEnu']['btncolor']
        print 'Update Server:', conf['MeEnu']['updsrv']
        print 'Update File:', conf['MeEnu']['updfile']
    else:
        conf = ConfigObj(r"/media/macaddrofthumb/PortableAppsLinux/Applications/menu/menu.conf")
else:
    print 'No configuration found in Applications/menu/. creating menu.conf in PortableAppsLinux/Applications/menu/'
    createConfig()
import sys
if 'updateconf' in sys.argv or 'uc' in sys.argv:
    print "Updating menu.conf..."
    createConfig()


# Now the menu app is finally created
import wx
import os
try:
    from agw import gradientbutton as GB
 #   bitmapDir = "/home/me/Desktop/py/bitmaps/"
except ImportError: # if it's not there locally, try the wxPython lib.
    import wx.lib.agw.gradientbutton as GB
  #  bitmapDir = "/home/me/Desktop/py/agw/bitmaps/"
class MyFrame(wx.Frame):
    """
    This is MyFrame.  It just shows a few controls on a wxPanel,
    and has a simple menu.
    """
    def __init__(self, parent, title):
        wx.Frame.__init__(self, parent, -1, title, pos=(-1, -1), size=(350, 500))

       

        # Now create the Panel to put the other controls on.
        panel = wx.Panel(self)

        # Use a sizer to layout the controls, stacked vertically and with
        # a 10 pixel border around each
        vbox = wx.BoxSizer(wx.VERTICAL)
    hbox = wx.BoxSizer()
    vbox.Add(hbox)
        panel.SetSizer(vbox)
        panel.Layout()
    def putAppName(appname, index):
        global torun
        if globals().has_key('torun') == False: torun = []
        torun.append(appname)
    def getAppName():
        global torun
        global ind
        return torun[ind]
    def runApp(blah):
        torun = getAppName()
        os.system('Applications/menu/AppRun ' + torun)
    def addButton(appname):
        appbtn = appname
        appbtn = wx.Button(panel, -1, appname)
        vbox.Add(appbtn, -1)
        global ind
        if globals().has_key('ind') == False: ind = 0
        else: ind = ind + 1
        putAppName(appname, ind)
        appbtn.Bind(wx.EVT_BUTTON, runApp)
      #  bitmap = wx.Bitmap("", wx.BITMAP_TYPE_PNG)
        xbtn = wx.Button(panel, -1, "Exit")
    xbtn.SetBackgroundColour("Red")
    #xbtn.align("right")
    hbox.Add(xbtn, -1, wx.RIGHT)
    #_init_.SetBackgroundColor(self, "Black")
    appdir = os.listdir('Applications')
    appdir.remove('menu')
    appdir.remove('Shotwell')
    #xbtn.Bind(wx.EVT_BUTTON, OnTimeToClose)
    map(addButton, appdir)

    #print "Binding events to buttons"
       # self.BindEvents(self.xbtn)
   # print "Setting winicon" # This has to be cut out to make it work, because you don't have the icon
     #   winIcon = wx.Icon('/home/me/Desktop/py/icon.png', wx.BITMAP_TYPE_PNG)
       # self.SetIcon(winIcon)


        def OnTimeToClose(event, error=True):
        kill = error
            print "Leaving the PAL Menu"

            self.Close()

    def Exit(event):
        kill = False
        OnTimeToClose("blah", error=False)
    xbtn.Bind(wx.EVT_BUTTON, Exit)

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
        frame = MyFrame(None, "PortAppMenu 0.1")
        self.SetTopWindow(frame)

        print "PyPortAppmenu V.0.1"

        frame.Show(True)
        return True
        
app = MyApp()
app.MainLoop()

#if kill == True: print "Please use the built-in close button to quit the PAL menu next time"
#elif kill == False: print "Thank you for using the Closinator!"

```
I know it's a bit messy right now.
If there is an easier way to do this with a list, I am planning to switch to a list soon anyway.

---

### Post by Crazedpsyc on 2010-11-29
bump

---

### Post by Arndt on 2010-11-29
> **Crazedpsyc said:**
> bump

This part

```

      vbox = wx.BoxSizer(wx.VERTICAL)
    hbox = wx.BoxSizer()
    vbox.Add(hbox)
        panel.SetSizer(vbox)

```

gave me problems last time (unexpected indentation or something), so I'm not at all sure that you have run this code yourself.

---

### Post by Crazedpsyc on 2010-11-29
I copied it directly from my py script which I have run many times. The only things I changed were a few bits like the hardware address of my thumb drive (which I marked). No code was changed this time. It runs fine except for always running that last program on the list. I have a screenshot here to show it.

Although now that I look, there is not supposed to be indentation there, and there is not in my version. try unindenting there

---

### Post by Crazedpsyc on 2010-12-02
bump

---

### Post by MadCow108 on 2010-12-02
runApp always gets the same index to look up its app, which is the index of the last value added.

you could solve it with minimal redesign by function currying (second time I give this tip today ;) ):
```

import functools, subprocess

...

appbtn.Bind(wx.EVT_BUTTON, functools.partial(self.runApp, index=ind))
#or give it the run string directly

def: runApp(self, bla, index)
  global torun
  subprocess.call([torun[index], "somearg"])

```


that code needs major cleanup btw ._.
use self for class internals

---

### Post by Crazedpsyc on 2010-12-03
Thanks for the response, I will try that tomorrow!
Yes I know it definitely needs to be cleaned up a lot. I usually completely rewrite things like this after I know how to do it better just to get rid of unnecessary code I forgot about and little things like changing all the tabs to spaces etc.

I still don't fully understand the whole "self" thing, because the book I learned python from did not use that at any point, even though it did make several big wxpython apps

---

### Post by Crazedpsyc on 2010-12-28
Sorry for the long delay in response, but I tried it and it works great! Thank you!
There is still one problem which I have no idea how to solve though: When I run an app from the menu, the menu freezes!
Is there any way to spawn the apprun process in the background, or to at least minimize the menu?
I had to change the subprocess.call back to an os.system because subprocess returned an error saying that the file did not exist.
Maybe it doesn't understand the current directory?

---

