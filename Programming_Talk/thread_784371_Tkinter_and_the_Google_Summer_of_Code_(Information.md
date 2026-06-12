---
title: "Tkinter and the Google Summer of Code (Informational)"
date: 2008-05-06
forum: Programming Talk
---

### Post by stevescripts on 2008-05-06
A little update on the beautification (de-uglification? ;) ) of Tkinter.

The gsoc is sponsoring Guilherme Polo to work on bringing the new tkwidgets (Tile) into Python.  [http://gpolo.ath.cx:81/projects/ttk_to_tkinter/]("http://gpolo.ath.cx:81/projects/ttk_to_tkinter/")

I have this running on my Gutsy box at home with no problems, however (for me ...) it required building tcl/tk 8.5, and Python 2.5.2 from source. (Not much trouble for me, save the Python source d/load, as I build/test tcl/tk frequently already...) 

There is still much work to be done, I thought some of you might enjoy taking a look at what is going on.  Still, (unfortunately), the Tile Widgets (ttk) are much better looking on windows XP/Vista, than on Linux by default.

There is a lot that can be done to make both Tk and Tkinter better-looking than using their defaults.  As time allows I will put together some information regarding how to do this.

I have chatted with the programmer, and he is quite knowledgeable and doing some nice work.

Hope someone finds this informative and useful.

duh... I forgot to mention what the widgets are - 

"Button", "Checkbutton", "Combobox", "Entry", "Frame", 
           "Label", "Labelframe", "LabelFrame", "Menubutton", "Notebook", 
           "Panedwindow", "PanedWindow", "Progressbar", "Radiobutton", 
           "Scrollbar", "Separator", "Sizegrip", "Style", "Treeview"

while some of these duplicate existing Tk widgets, their appearance is
updated ...


Steve

---

### Post by LaRoza on 2008-05-06
That is good news. Thanks.

---

### Post by gpolo on 2008-05-07
Hi steve, thanks for pointing it out

I'm just bringing some updates... All the Ttk functionality has been wrapped now, I've tried to do it in way (this is mostly related to styling) that Python users/developers don't need to know or understand the Tcl syntax in order to be able to use some parts, and I believe a Tcl person will not have difficulties understanding it.

The documentation in reStructuredText is way behind the current functionality, which is the next thing I will be doing together with adding new samples.

Lastly.. I haven't tested it under Windows yet, it may need some environment checking in order to find tile (not sure), it would be nice if someone could test that and tell me the results. The other option is to compile python with tcl/tk 8.5, which I don't how hard is for Windows people.

Thanks.

---

### Post by stevescripts on 2008-05-07
For those of you who may not have put it together yet, gpolo is the programmer working on the gsoc project.

I am pleased to have had the opportunity to interact with him.

Steve

---

