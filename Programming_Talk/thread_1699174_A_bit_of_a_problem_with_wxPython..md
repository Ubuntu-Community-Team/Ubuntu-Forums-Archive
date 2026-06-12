---
title: "A bit of a problem with wxPython."
date: 2011-03-03
forum: Programming Talk
---

### Post by gusnmithfrank on 2011-03-03
I searched Google and the Ubuntu forums, but didn't found a solution to my, im sure, quite simple problem. 

I started watching [thenewboston's YouTube Channel]("http://www.youtube.com/user/thenewboston") on Python programming and got to the point where I need to install the wxPython GUI.
I couldn't complete the guide in wxPython's official site, because after adding the extra repositories(as it is noted in the site) I got some error, saying that some of the packages had not been found, nor installed(don't remember the line exactly, but it think it's a common error, when it comes to editing the source.list manualy).

So, I searched the Software Center and found PyShell("python-wxtools") and installed it. I got new programs in the "Programming" area, called: PyCrust, PyShell and XRCed.
I tried to do the simple task given in one of the videos:
import wx
app=wx.App()
win=wx.Frame(None)
win.Show()
app.MainLoop()

but after saving and runing it - I always get an error:
"Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    import wx
ImportError: No module named wx"

I get the same error message when trying to import wx in IDLE.

I also installed some other wx packages, using "apt-get install python-wxversion", but that did not solved the problem.


Is there a way to solve it or I have to use PyShell to write code in order to run it?

---

### Post by Arndt on 2011-03-03
> **gusnmithfrank said:**
> I searched Google and the Ubuntu forums, but didn't found a solution to my, im sure, quite simple problem. 

I started watching [thenewboston's YouTube Channel]("http://www.youtube.com/user/thenewboston") on Python programming and got to the point where I need to install the wxPython GUI.
I couldn't complete the guide in wxPython's official site, because after adding the extra repositories(as it is noted in the site) I got some error, saying that some of the packages had not been found, nor installed(don't remember the line exactly, but it think it's a common error, when it comes to editing the source.list manualy).

So, I searched the Software Center and found PyShell("python-wxtools") and installed it. I got new programs in the "Programming" area, called: PyCrust, PyShell and XRCed.
I tried to do the simple task given in one of the videos:
import wx
app=wx.App()
win=wx.Frame(None)
win.Show()
app.MainLoop()

but after saving and runing it - I always get an error:
"Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    import wx
ImportError: No module named wx"

I get the same error message when trying to import wx in IDLE.

I also installed some other wx packages, using "apt-get install python-wxversion", but that did not solved the problem.


Is there a way to solve it or I have to use PyShell to write code in order to run it?

I don't use PyShell (nor have I used the Software Center), and I can run your little program (I mainly use wx with C++, but wxPython sometimes for experimenting). I think I just installed the package python-wxgtk2.8, using synaptic.

---

### Post by gusnmithfrank on 2011-03-03
I read that problem might be caused by the preinstalled version of python. 

Maybe its built-in, but i have Python 2.6 installed (no IDLE for it, though) but i wanted to use the latest 2.X version, so I Installed 2.7.1 also.

Can I completely remove all Python versions and all the IDLEs/standalones(like PyShell)/WX and such, associated with it, and installing a fresh 2.7.1 version, without causing system failure? (what a sentence that is!)

I think that should repair the issues.

---

### Post by Arndt on 2011-03-03
> **gusnmithfrank said:**
> I read that problem might be caused by the preinstalled version of python. 

Maybe its built-in, but i have Python 2.6 installed (no IDLE for it, though) but i wanted to use the latest 2.X version, so I Installed 2.7.1 also.

Can I completely remove all Python versions and all the IDLEs/standalones(like PyShell)/WX and such, associated with it, and installing a fresh 2.7.1 version, without causing system failure? (what a sentence that is!)

I think that should repair the issues.

I think I have seen people reporting having enormous problems after deinstalling Python, so I wouldn't answer yes to that. I don't know.

---

### Post by dodle on 2011-03-03
> **gusnmithfrank said:**
> ```
"Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    import wx
ImportError: No module named wx"
```

I'm pretty sure that just means you don't have wxPython installed. Either open synaptic and install python-wxgtk2.8 or open a terminal and type:

```
sudo apt-get install python-wxgtk2.8
```

You shouldn't need to add any extra repositories, it is in Ubuntu's.

---

### Post by gusnmithfrank on 2011-03-04
I reinstalled Ubuntu, because I broke the GUI.
Anyways, now I'm going to use the default Python version. Which wxgtk should I install for Python 2.6.6 - wxgtk2.8 or wxgtk2.6 
Does it even matter? ;d

---

### Post by cgroza on 2011-03-04
> **gusnmithfrank said:**
> I reinstalled Ubuntu, because I broke the GUI.
Anyways, now I'm going to use the default Python version. Which wxgtk should I install for Python 2.6.6 - wxgtk2.8 or wxgtk2.6 
Does it even matter? ;d
I have both installed and there is no problem. Get the 2.8.

---

### Post by gusnmithfrank on 2011-03-04
Well, thank you, lad. I was not up for more crashed GUIs. :)

---

### Post by Crazedpsyc on 2011-03-04
FYI: The problem was simply that python-wxgtk2.8 was missing. It is what actually contains the wx module. wxtools is just a collection of those programs you mentioned, which often make developing wxPython easier

And, the crashed gui part was because so many vital parts of ubuntu depend on python. When you removed python, most of ubuntu was removed as well!

---

### Post by cgroza on 2011-03-04
> **Crazedpsyc said:**
> FYI: The problem was simply that python-wxgtk2.8 was missing. It is what actually contains the wx module. wxtools is just a collection of those programs you mentioned, which often make developing wxPython easier
I really found no benefit in them (except wxGlade which I used once to get some code sample). I write my GUI with my own fingers. :D

---

### Post by Crazedpsyc on 2011-03-07
> **cgroza said:**
> I really found no benefit in them (except wxGlade which I used once to get some code sample). I write my GUI with my own fingers. :D
Very good! So do I, but many people like to use pyShell or pyCrust for debugging and testing. I agree that gedit is an excellent way to make guis though! ;)

---

