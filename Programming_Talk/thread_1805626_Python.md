---
title: "Python ???"
date: 2011-07-16
forum: Programming Talk
---

### Post by kaloasd on 2011-07-16
I wanted to learn Python and found some nice tutorials on YouTube. I also wanted the latest version but couldn't uninstall the default 2.7 because I had remove a lot of other stuff so I just installed the 3.2 and IDLE 3.2 (don't know if thats right to do). 

Next I followed the instructions here [http://wiki.wxpython.org/InstallingOnUbuntuOrDebian](http://wiki.wxpython.org/InstallingOnUbuntuOrDebian) for downloading wxPython, but skipped: 
```
deb http://apt.wxwidgets.org/ DIST-wx main 
deb-src http://apt.wxwidgets.org/ DIST-wx main
sudo apt-get update
```because the terminal said "No command 'deb' found,"

The problem is that this works:
```
import wx
app=wx.App()
win=wx.Frame(None)
win.Show()
app.MainLoop()
```but this doesn't:
```
import wx
 
class TestFrame(wx.Frame):
    def __init__(self, parent, title):
        wx.Frame.__init__(self, parent, title=title)
        text = wx.StaticText(self, label="Hello, World!")
 
app = wx.App(redirect=False)
frame = TestFrame(None, "Hello, world!")
frame.Show()
app.MainLoop()
```.

When I click the second one tthe pointer turns into a plus and i get a screenshot of an 
area I select

---

### Post by The Cog on 2011-07-16
As far as I can see, wxpython is only available in versions 2.6 and 2.8, which I take to mean that they are for those versions of python, and not for python version 3.x. I could be wrong though. I couldn't quickly see a statement about the version of python needed.

There are two packages in the Ubuntu repositories that give you wxpython - python-wxgtk2.6 and python-wxgtk2.8. If you are just starting learning, I would suggest using one of those.

Moving this thread to Programming Talk.

---

### Post by Bachstelze on 2011-07-16
> **The Cog said:**
> As far as I can see, wxpython is only available in versions 2.6 and 2.8, which I take to mean that they are for those versions of python, and not for python version 3.x. I could be wrong though. I couldn't quickly see a statement about the version of python needed.

2.6 and 2.8 are the versions of WxWidgets, not of Python. There is no Python 2.8. ;)

@kaloasd: As The Cog said, just using the packages from the repositories should work. You need Python 2.7, WxPython currently does not work with Python 3.

---

### Post by nvteighen on 2011-07-16
> **kaloasd said:**
> 
```
deb http://apt.wxwidgets.org/ DIST-wx main 
deb-src http://apt.wxwidgets.org/ DIST-wx main
sudo apt-get update
```

In the case of wxWidgets, this is completely unnecessary because Ubuntu already provides in its repos versions that are guarranteed to work on the system.

But for your interest, as you may be interested in adding repositories in the future. Those 'deb' lines aren't commands; that's why you got the error. You have to copy those two lines into the /etc/apt/sources.list file. That file controls the repositories you use for APT and everytime you want to add/remove a repository, it involves editing that time. Of course, you'll need root privileges for touching it.

After editing /etc/apt/sources.list, you always have to update APT (sudo apt-get update) in order to make the changes effective and be able to install things from the repos you've added.

But a kind advice: always look at the Ubuntu (or your distro's) repos first before adding any third-party repos.

---

### Post by juancarlospaco on 2011-07-16
Please use DESCRIPTIVE titles !

---

### Post by Bachstelze on 2011-07-16
> **juancarlospaco said:**
> Please use DESCRIPTIVE titles !

Please stop posting useless messages. A reminder to use descriptive titles is something you add to your answer to the question. On a post by itself it's just silly (not to mention the aggressive tone).

---

### Post by ziekfiguur on 2011-07-17
> **kaloasd said:**
> When I click the second one tthe pointer turns into a plus and i get a screenshot of an 
area I select

I had a similar problem some time ago. In my case the os didn't get the right interpreter for the program. make sure the first line of your program is `#!/usr/bin/env python' (without the quotes) and nothing more. Start your real code after that.

---

### Post by kaloasd on 2011-07-17
Thank you all for the help :D

---

