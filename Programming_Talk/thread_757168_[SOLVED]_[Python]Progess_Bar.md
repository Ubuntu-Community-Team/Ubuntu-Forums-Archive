---
title: "[SOLVED] [Python]Progess Bar"
date: 2008-04-16
forum: Programming Talk
---

### Post by themusicwave on 2008-04-16
Hey everyone,

I am thinking it would be nice to add a progress bar to a Python application I am making using TKinter.

Through some searching I foudn that TK does have a ProgressBar widget, but python's Tkinter doesn;t seem to know it exists.

Is this widget in TKinter?

[http://www.tkdocs.com/tutorial/morewidgets.html#progressbar]("http://www.tkdocs.com/tutorial/morewidgets.html#progressbar")
I suppose I could build my own if needed, but it would be nice if Tkinter just had one to use.

---

### Post by stevescripts on 2008-04-16
AFAIK, the progress bar is a part of Tile - which is in the tcl/tk 8.5 and up releases.

Also, as far as I know - Tkinter has not yet moved to tcl/tk8.5...

A Tk hack (common in days gone by... ;) )
```

#progress bar, using the scale widget

set pos 0

scale .pbar -var pos -sliderlength 10 -showvalue 0 -orient horizontal

.pbar configure -width 5 -sliderlength 7 -sliderrelief flat -troughcolor #0000ff

grid .pbar -row 5 -column 0 -columnspan 3 -sticky ew



proc setPos { } {

	global s pos

	set p [s current_position]

	if {[s length] < 1} {

		set l 1 } else {

		set l [s length]

		}

	set pos [expr int($p * 1.0 / $l * 100)]

	after 100 setPos

}

```

Don't have time to hack this out in Tkinter right now - 

Shouldn't be too difficult

Steve

---

### Post by themusicwave on 2008-04-16
I can handle making my own I think.  especially since I only plan on making a "bouncing" progress bar.

I was just curios if it had been included yet.  Thanks for the information and the hack!

If I do make one I can post the code here for others to use.

---

### Post by stevescripts on 2008-04-16
A better tk progress bar, utilizing the canvas widget:
(looks more like an ordinary progress bar)

```

#! /usr/bin/tclsh

package require Tk

wm title . "Progress Bar"

canvas .c -width 200 -height 20 -bd 2 -relief groove -highlightt 0
.c create rectangle 0 0 0 20 -tags bar -fill darkgreen
pack .c -padx 10 -pady 10
pack [label .l -textvariable i]

proc run {percent} {
	.c coords bar 0 0 [expr {int($percent * 2)}] 20 
}


proc driver {} {
	global i
	for {set i 0} {$i < 100} {incr i} {
	run $i
   	after 100 
   	update
	}
}

#comment out the next line to use in an interactive tclsh ...
driver

```
The above code slightly modified from a version on the tclers wiki.

The first post was just the first old hack I could find quickly.

Steve
(too late tonight to finish up a tkinter version :) )

---

### Post by stevescripts on 2008-04-18
Rather hackish, I fear, but ...

A progress bar using tkinter:
```

#! /usr/bin/python

from Tkinter import *

import time

root = Tk()

root.title("Progress Bar")

i = 0

def go():
	countup(50)

def countup(x):
	ctr = 1
	while ctr <= x:
		moveit(ctr)
		lblcommand()
		c.update()
		time.sleep(.1)
		ctr += 1

def lblcommand():
	temp = l.cget("text")
	temp = temp + 2
	l.configure(text=temp)

def moveit(pct):
	c.move(x, pct * .16, 0)

c = Canvas(root, width = 200, height = 20, highlightt = 0, relief = 'groove', borderwidth = 2)
x = c.create_rectangle(0, 0, -220, 20, fill="green", tags = 'bar')
l = Label(root, text = i)
b = Button(root, text = 'Run',command=go)
c.pack(padx= '10')
l.pack()
b.pack()

root.mainloop()

```

@ themusicwave - FYI - this will allow you to use the tile widets with  Tkinter  [http://tkinter.unpy.net/wiki/TileWrapper](http://tkinter.unpy.net/wiki/TileWrapper)

Python folks, feel free to critique the h* out of this... :)

Steve

---

### Post by Can+~ on 2008-04-18
> **stevescripts said:**
> Python folks, feel free to critique the h* out of this... :)

Rather difficult to critique, I don't know tk, I went directly to GTK.

But I'm guessing you grab a canvas and make a rectangle bigger according to the value?

You should consider the width of the box that contains it too, that would make it more complete.

---

### Post by stevescripts on 2008-04-18
Can+~  thx for the input - this is of course, not truly finished.

Re Tk, the syntax for tkinter is enough different to give me trouble.
(same goes for PerlTk and RubyTk... am tinkering with Ruby as well as
Python)  My *limited* expierence with Perl has a lot of rust on it too.

Steve

---

