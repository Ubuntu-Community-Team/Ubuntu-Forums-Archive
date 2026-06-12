---
title: "How to add separator in frame ?"
date: 2009-04-02
forum: Programming Talk
---

### Post by tusharv on 2009-04-02
Hi,
I am working on TCL/TK.

I have make one frame.
and added label in it.
Now How can I add separator in from before adding another lable ?

Thanks,
Tushar

---

### Post by stevescripts on 2009-04-02
Lacking a clearer description of exactly what you are trying to achieve, my first impression here, is that you need a group of frame widgets, with your other widgets embedded in the frames...

Hope this helps a bit.

Steve

---

### Post by tusharv on 2009-04-03
> **stevescripts said:**
> Lacking a clearer description of exactly what you are trying to achieve, my first impression here, is that you need a group of frame widgets, with your other widgets embedded in the frames...

Hope this helps a bit.

Steve

Let me give you clear idea what I am trying to do.

My code is like this ```
label .lb1 -text "The first line of test."
pack .lb1 
label .lb2 -text "The Second line of test."
pack .lb2
```

This code will generate one window with this two labels.
In between Can I add separator ?

I have seen the most example are given to add separator in the menu only.


Thanks,
Tusharv

---

### Post by stevescripts on 2009-04-03
OK, let's try starting here ...

Tk widgets have options for appearance - in this case we are going to explore the
-relief and -bd (or -borderwidth) options first.

Source the following into an interactive tclsh and experiment with it:
```

package require Tk

pack [label .l1 -text "Label 1"]

pack [label .l2 -text "Label 2"]

proc chg_style {widget relief border} {
        $widget configure -relief $relief -bd $border
	}

chg_style .l1 sunken 2

chg_style .l2 raised 3

```

If you cannot achieve a look and feel that suits you by simply configuring the labels,
you will need to use separate frames.  Frames are container widgets, and have no separator option.

Hope this helps.

Steve

---

### Post by stevescripts on 2009-04-03
As an afterthought, you may want to take a look at the labelframe widget also:

[http://www.tcl.tk/man/tcl8.5/TkCmd/labelframe.htm](http://www.tcl.tk/man/tcl8.5/TkCmd/labelframe.htm)

Run the demo script at the bottom of that page ...

Steve

---

### Post by tusharv on 2009-04-03
Hi stevescripts,

I appreciate your efforts to separate different labels.
But isn't Tk provide a separator to include in frame as we include separator in the menu, a simple one line ?

Thanks,
Tusharv

---

### Post by stevescripts on 2009-04-04
Unfortunately, no ...

You can put your widgets in separate frames, and grid the frames however.

I believe this might give you the appearance you are looking for.

EDIT:  Personally, I like to keep the on-line docs available when working on tcl/tk, rather than depending on the man pages ...

LINK:  [http://www.tcl.tk/man/tcl8.5/](http://www.tcl.tk/man/tcl8.5/)

Steve

---

### Post by stevescripts on 2009-04-04
Tushar,

Does something like this crude hack provide the sort of appearance you are looking for?

```

frame .main
frame .main.f1
frame .main.f2

label .main.f1.la -text "Label 1"
label .main.f2.lb -text "Label 2"

pack .main.f1.la
pack .main.f2.lb
pack .main.f1
pack .main.f2

pack .main

.main.f1 configure -relief raised -bd 1

.main.f2 configure -relief raised -bd 1

```

Just an ugly hack, basically copied from an interactive session,
certainly can be coded nicely - just no time and energy this am...

Steve

---

