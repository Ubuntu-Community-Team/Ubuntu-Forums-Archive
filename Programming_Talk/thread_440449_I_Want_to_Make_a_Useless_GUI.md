---
title: "I Want to Make a Useless GUI"
date: 2007-05-11
forum: Programming Talk
---

### Post by user1397 on 2007-05-11
As a learning experience, I would like to make a GUI for an extremely mundane program...which I haven't thought of yet.

I don't care for the actual function of the program, I just want to be able to design a neat and preferably pleasing GUI for it.

So after I get my skills down with python, I would like to make a gui based on python, but I don't know what toolkit to use (on windows).  For linux I would use pyGTK (which I would learn later, now I want to learn how to make a python program with a GUI in windows).

** So does anybody know a good guide on designing python-GUIs under windows?** (I have windows xp).

I'm aiming for a look kinda like the current official bittorrent client (in windows), which I know is written in python, but I don't know the toolkit it uses (does anyone know?)  I know that that is probably really hard, but I'm willing to learn :)

**Also**, how do you package windows programs to make them executables (.exe) ?

---

### Post by nicholas22 on 2007-05-11
This might be the wrong forum! :popcorn:

---

### Post by bashologist on 2007-05-11
> **ubuntuman001 said:**
> **Also**, how do you package windows programs to make them executables (.exe) ?Search google for "python frozen binaries". You could try "py2exe".

---

### Post by Skardal on 2007-05-11
For making exe files: [http://py2exe.org]("http://py2exe.org")
For making windows GUI, I'd guess [wxPython]("http://www.wxpython.org") , but I've got no experience with it. There is a learning section at their page :)

You could also check out [this list]("http://wiki.python.org/moin/GuiProgramming").

---

### Post by user1397 on 2007-05-11
> **nicholas22 said:**
> This might be the wrong forum! :popcorn:Unless my eyes lie to me, at the top of this forum it says: 

> **Programming Talk:**
This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any language is allowed.

---

### Post by user1397 on 2007-05-11
> **Skardal said:**
> For making exe files: [http://py2exe.org](http://py2exe.org)
For making windows GUI, I'd guess [wxPython]("http://www.wxpython.org") , but I've got no experience with it. There is a learning section at their page :)

You could also check out [this list]("http://wiki.python.org/moin/GuiProgramming").thanks a bunch, very useful links.

edit: just found out that even the official bittorrent client uses py2exe to make their executables, according to the py2exe site!  I didn't know that...

But, does anyone know what bittorrent uses for its GUI toolkit?

---

### Post by noerrorsfound on 2007-05-11
> **ubuntuman001 said:**
> But, does anyone know what bittorrent uses for its GUI toolkit?
I think it's just Tkinter which is included by default in Python.

---

### Post by user1397 on 2007-05-11
> **noerrorsfound said:**
> I think it's just Tkinter which is included by default in Python.hmmm...well it ceratinly doesn't *look* like Tk, cause it's very pretty (don't mean to bash on Tkinter, but hey!)

---

### Post by WW on 2007-05-11
It's wx.

---

### Post by snoop on 2007-05-11
If you want to see how to make a gui with python and gtk, see this video (it explains quite a bit)

[http://www.archive.org/details/HampshireLinuxUserGroupPythonGladeGTK](http://www.archive.org/details/HampshireLinuxUserGroupPythonGladeGTK)

---

### Post by user1397 on 2007-05-11
> **WW said:**
> It's wx.is that an educated guess?  or can you back this up with a link? (please)

---

### Post by user1397 on 2007-05-11
> **snoop said:**
> If you want to see how to make a gui with python and gtk, see this video (it explains quite a bit)

[http://www.archive.org/details/HampshireLinuxUserGroupPythonGladeGTK](http://www.archive.org/details/HampshireLinuxUserGroupPythonGladeGTK)that looks interesting, thank you.

---

### Post by WW on 2007-05-11
> **ubuntuman001 said:**
> is that an educated guess?  or can you back this up with a link? (please)

Go to the download page: [http://download.bittorrent.com/dl/](http://download.bittorrent.com/dl/)

Grab BitTorrent-5.0.7.tar.gz, open it up in the Archive Manager, double-click on the BitTorrent subdirectory, then go into the GUI_**wx** subdirectory, and take a look at any of the files.  For example, CheckBoxDialog.py begins
```

# by Greg Hazel

import sys

from BitTorrent.GUI_wx import BTDialog, ElectroStaticText
from BitTorrent.GUI_wx import SPACING
[color=blue]import wx[/color]

class CheckBoxDialog(BTDialog):

    def __init__(self, parent, title, label, checkbox_label, checkbox_value):
	style=wx.DEFAULT_DIALOG_STYLE
	if sys.platform == 'darwin':
	    # no system menu or close box on the mac
	    style = wx.CAPTION|wx.CLOSE_BOX
        BTDialog.__init__(self, parent=parent, id=wx.ID_ANY, title=title, style=style)
        self.text = ElectroStaticText(self, label=label)

        self.checkbox = wx.CheckBox(self, label=checkbox_label)
        self.checkbox.SetValue(checkbox_value)

```

---

### Post by user1397 on 2007-05-11
> **WW said:**
> Go to the download page: [http://download.bittorrent.com/dl/](http://download.bittorrent.com/dl/)

Grab BitTorrent-5.0.7.tar.gz, open it up in the Archive Manager, double-click on the BitTorrent subdirectory, then go into the GUI_**wx** subdirectory, and take a look at any of the files.  For example, CheckBoxDialog.py begins
Ah, well that would prove it!

Thanks for the fast response.

---

### Post by Inc&#940;nus on 2007-05-12
> **ubuntuman001 said:**
> As a learning experience, I would like to make a GUI for an extremely mundane program...which I haven't thought of yet.

I don't care for the actual function of the program, I just want to be able to design a neat and preferably pleasing GUI for it.

So after I get my skills down with python, I would like to make a gui based on python, but I don't know what toolkit to use (on windows).  For linux I would use pyGTK (which I would learn later, now I want to learn how to make a python program with a GUI in windows).

** So does anybody know a good guide on designing python-GUIs under windows?** (I have windows xp).

I'm aiming for a look kinda like the current official bittorrent client (in windows), which I know is written in python, but I don't know the toolkit it uses (does anyone know?)  I know that that is probably really hard, but I'm willing to learn :)

**Also**, how do you package windows programs to make them executables (.exe) ?


Without a doubt I would say a cross-platform GUI toolkit should be your first consideration - if you get yourself running on a good toolkit then your GUI will work on windows, mac and GNU/Linux with the minimum of fuss.

You will effectively up your productivity in terms of real time and effort out of your life. Example: you write your Linux-suitable GUI to be cross-platform, you just saved yourself the hassle of writing a completely different one in windows, and of maintaining both separately.

I use Qt, and it's an absolutely great, comfortable, extensive basis against which to program - you could use pyQt. If you're writing GPL or private software I'd heartily recommend it - as I would also do for a large commercial concern that wants to license it commercially. If you don't wish to write GPL'd software, you may want to use Gtk or another toolkit.

You'll find Qt Designer to be about the easiest RAD GUI builder there is for cross-platform development. It's on a par with the GUI designer in that Visual Studio thingy ;) . Use pyuic to squodge your creations into python. :p

If you invest a little time in pyQt it really pays.

By the way - do bear in mind that a native GUI is not the same as native *widgets* -  ie text boxes, combo boxes, etc.. Neither Gtk or Qt use native widgets in windows, they use their own. wxWindows does use native widgets.

---

### Post by user1397 on 2007-05-13
> **Inc&#940 said:**
> Without a doubt I would say a cross-platform GUI toolkit should be your first consideration - if you get yourself running on a good toolkit then your GUI will work on windows, mac and GNU/Linux with the minimum of fuss.

You will effectively up your productivity in terms of real time and effort out of your life. Example: you write your Linux-suitable GUI to be cross-platform, you just saved yourself the hassle of writing a completely different one in windows, and of maintaining both separately.

I use Qt, and it's an absolutely great, comfortable, extensive basis against which to program - you could use pyQt. If you're writing GPL or private software I'd heartily recommend it - as I would also do for a large commercial concern that wants to license it commercially. If you don't wish to write GPL'd software, you may want to use Gtk or another toolkit.

You'll find Qt Designer to be about the easiest RAD GUI builder there is for cross-platform development. It's on a par with the GUI designer in that Visual Studio thingy ;) . Use pyuic to squodge your creations into python. :p

If you invest a little time in pyQt it really pays.

By the way - do bear in mind that a native GUI is not the same as native *widgets* -  ie text boxes, combo boxes, etc.. Neither Gtk or Qt use native widgets in windows, they use their own. wxWindows does use native widgets.Thank you for all that info and the recommendation.  I'll look into pyQT now...

---

### Post by H.E. Pennypacker on 2007-05-13
> **snoop said:**
> If you want to see how to make a gui with python and gtk, see this video (it explains quite a bit)

[http://www.archive.org/details/HampshireLinuxUserGroupPythonGladeGTK](http://www.archive.org/details/HampshireLinuxUserGroupPythonGladeGTK)

It would be better to use the original website instead of archive.org.  Here's the link:

[http://www.hantslug.org.uk/cgi-bin/wiki.pl?TechTalks/2ndDecember2006](http://www.hantslug.org.uk/cgi-bin/wiki.pl?TechTalks/2ndDecember2006)

---

### Post by user1397 on 2007-05-13
Okay, so imagine I made a nice little program, good enough to be used for a purpose, and hence, downloadable from a website; written in python/wxPython, so obvioulsy those 2 things would be dependencies of the program;

So now, how would Joe, a windows xp user, download this program with the necessary dependencies, without having to download them separately from the program?  Would I package python and wxPython in the program .exe file?

---

### Post by JT673 on 2007-05-13
> **ubuntuman001 said:**
> Okay, so imagine I made a nice little program, good enough to be used for a purpose, and hence, downloadable from a website; written in python/wxPython, so obvioulsy those 2 things would be dependencies of the program;

So now, how would Joe, a windows xp user, download this program with the necessary dependencies, without having to download them separately from the program?  Would I package python and wxPython in the program .exe file?

Hmms...Don't.  Just put it in big letters, "Python and wxPython needed.", with links to the download page.

That being said, I'm sure that NSIS has something to your needs.  Most Windows user have NSIS installed.

---

### Post by Hendrixski on 2007-05-13
> **ubuntuman001 said:**
> As a learning experience, I would like to make a GUI for an extremely mundane program...which I haven't thought of yet.
?

Cool. I just decided to learn Python, on a whim, and was just playing around with the the GUI a few seconds ago.  What you're looking for is Tkinter ... Tk stands for toolkit and inter is short for interface.  Wierd, eh?

When you learn how to paint, you do so by mimicking the masters.  Try to recreate the GUI for your favorite program.  :-)  how about recreating the Firefox interface (without functionality), or recreating a simple game.

BTW.  So far, python interfaces look easier to make than Java, and C++ (with Qt3) interfaces.  Though, I haven't scoped out some of the advanced functionality yet.

enjoy

---

### Post by braddcadd on 2007-07-30
(shameless plug :)  ) You are welcome to extend my project.
[http://sourceforge.net/projects/pdf-glue/](http://sourceforge.net/projects/pdf-glue/)

---

