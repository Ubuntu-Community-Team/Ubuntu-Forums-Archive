---
title: "How to show a file selection dialog(wxFileCtrl )"
date: 2010-10-17
forum: Programming Talk
---

### Post by yanes on 2010-10-17
Hi all 
I'm new to Linux coding , but i have a small knowledge in python , 
i used WxGlade to make my first dialog , but i need to use the [wxFileCtrl  ]("file:///media/BACKUP/LINUX/wx/classwx_file_ctrl.html")
in wx docs and the internet i found some documentations but i think i need a simple example 
on how to import and use this class 
or a fully detailed giude about this control 

i'm waiting for your help

---

### Post by spjackson on 2010-10-18
> **yanes said:**
> 
I'm new to Linux coding , but i have a small knowledge in python , 
i used WxGlade to make my first dialog , but i need to use the [wxFileCtrl  ]("file:///media/BACKUP/LINUX/wx/classwx_file_ctrl.html")
in wx docs and the internet i found some documentations but i think i need a simple example 
on how to import and use this class 
or a fully detailed giude about this control 

Which versions of wxGlade, wxPython are you using? I don't think that the stable 2.8 series available in the Ubuntu repositories has this control - I believe that it's new in the 2.9 development branch. I can't see any support for it in 0.6.3 wxGlade either.

---

### Post by yanes on 2010-10-18
yeah , it's true , my version you can this in the attached pic :)
do you think that i have to install wxPython 2.9 ? 
i found the control in the wxWidgets 2.9 classes list
but i didn't found wxpython or wxWidgets 2.9 in synaptic packages

is ther another way to make it ? :)

---

### Post by spjackson on 2010-10-18
> **yanes said:**
> yeah , it's true , my version you can this in the attached pic :)
do you think that i have to install wxPython 2.9 ? 
i found the control in the wxWidgets 2.9 classes list
but i didn't found wxpython or wxWidgets 2.9 in synaptic packages

is ther another way to make it ? :)
Note that wxFileDialog is already in 2.8, so if that would meet your needs, then you are OK. However, for wxFileCtrl...

It's a while since I followed wxWidgets developments. I am not aware of where you can get binaries of 2.9 for Linux in general or Ubuntu in particular - you might be able to find some by searching.

You can download the source from [http://sourceforge.net/projects/wxwindows/files_beta/2.9.1/](http://sourceforge.net/projects/wxwindows/files_beta/2.9.1/) . The current development source for wxPython has wxFileCtrl and can be obtained via svn from [http://svn.wxwidgets.org/svn/wx/wxPython/trunk/](http://svn.wxwidgets.org/svn/wx/wxPython/trunk/)

As far as I know, there's nothing in wxGlade for this control, so you would need to either add the control via code, or modify wxGlade to incorporate it.

You would need to be a bit adventurous to go down the road of building wxWidgets and wxPython from source, but if you really need wxFileCtrl then you'll need to bite the bullet as this is bleeding edge. Since you originally asked for "a simple example on how to import and use this class or a fully detailed giude about this control", I wouldn't recommend trying to do it yourself really.

---

### Post by yanes on 2010-10-18
thank you for reply friend , 
you  are really so kind
wx._windows.FileDialog exists in pydoc :) but i can not use it 
can you tell me how to instantiate it or declare it in my program ? 
IF possible i'll be so thankful if you give a code example ;)

forgive me for losing your time ;) ;) ;)

---

### Post by spjackson on 2010-10-18
> **yanes said:**
> 
wx._windows.FileDialog exists in pydoc :) but i can not use it 
can you tell me how to instantiate it or declare it in my program ? 
IF possible i'll be so thankful if you give a code example ;)

forgive me for losing your time ;) ;) ;)
You want wx.FileDialog. There is an full working example of using it here [http://wiki.wxpython.org/Getting%20Started](http://wiki.wxpython.org/Getting%20Started)

---

### Post by yanes on 2010-10-19
very nice ! 
this example is very useful 

thank you :)

---

