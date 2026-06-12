---
title: "Python Gui ?"
date: 2005-11-07
forum: Programming Talk
---

### Post by Drakx on 2005-11-07
Hi, 

Im looking into the Gui side of python and want to know a good easy to use and learn gui (ie pyQT, pygtk, wxPython, etc etc), Ive done a quick search on google and like the look of wxPython but cannot find a good tutorial (yes there's one on the site but its not very good towards n00bs). So im woundering what experiance's have you had with python gui programming ? and why you choose the gui tool kit your using and was it easy to learn ? and/or failing that can some one redirect me to a good wxPython tutorial.

Thanks

---

### Post by moephan on 2005-11-07
Drakx,

I picked up Python and Gtk over the weekend, and got going with it in a matter of hours! I think I might be falling in love with Python ;)  Having used a number of other UI frameworks, I found Gtk to be intuitive, but tedious. 

[http://www.pygtk.org/dist/pygtk2tutorial.tgz](http://www.pygtk.org/dist/pygtk2tutorial.tgz)

I'm not sure if this is the tutorial that you refer to, but it is the one that I used. Let me know if you have any questions.

Cheers, Rick

---

### Post by az on 2005-11-07
Glade?

---

### Post by flower on 2005-11-09
my choice is wxPython ... and the good news is you can download `Boa consutrctor` which makes is really cool to make GUI programs, you should give it a try

---

### Post by Drakx on 2005-11-09
I've already got Boa :) what im looking for is a good tutorial on wxPython, plus i wanna here the pros and cons of the other python ui's people have used.

---

### Post by aev on 2005-11-09
try SPE . it's in the reps... I think it is very cool and easy :cool:

---

### Post by nszabolcs on 2005-11-09
i've already tried Boa, SPE, wxGlade, but i didn't like them (they feel unnecessarily bloated).

for cross platform gui development i always use wxpyhton + xrced 
(xrced is included in wx: from wx.tools.XRCed.xrced import main; main())
with xrc you can separate the layout from the logic.

unfortunately there is no real pythonic gui toolkit:

tkinter: ugly widgets and non pythonic code (eg: you cannot set value of a text box just text.delete(BEGIN,END); text.insert(END, txt) it's very ugly)

wxpython: gtk and msw implementations sometimes differ, there are inconsistencies in naming (eg: redundant names: TextCtrl.AppendText(txt)). Non pythonic (eg. you cannot iter through items in a ListCtrl)

pygtk: Pretty good, but you won't get native look on windows. I didn't played much with this.  Usually it's the second favourite after wxpython. The argument against pygtk (and the others) is usually that you can feel the underlying C implementation.

pyqt: Does not (yet) support Qt 4 so you cannot use it on windows freely.

pyfltk: I had some bad experience with fltk so i didn't tried this.

---

### Post by ssam on 2005-11-09
if you are happy with gtk then using glade is probably most sensible.

---

