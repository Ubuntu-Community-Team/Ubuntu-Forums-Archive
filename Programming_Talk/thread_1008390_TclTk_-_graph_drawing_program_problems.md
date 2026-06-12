---
title: "Tcl/Tk - graph drawing program problems"
date: 2008-12-11
forum: Programming Talk
---

### Post by Tasma on 2008-12-11
I am fairly new to Tcl/Tk programming, but thanks to online tutorials and code examples I've managed to put together a simple program with which you can draw graphs:

```
proc buttons {f var values} {
	frame $f
	foreach value $values {
		radiobutton $f.v$value -text $value -variable $var -value $value \
		-indicatoron 0
	}
	eval pack [winfo children $f] -side left
	set ::$var [lindex $values 0]
	set f
}

proc draw(Rectangle) {x y} {
	set ::ID [.c create rect [expr $x-4] [expr $y-4] [expr $x+4] [expr $y+4] -fill black]
}

proc draw(Oval) {x y} {
	set ::ID [.c create oval [expr $x-4] [expr $y-4] [expr $x+4] [expr $y+4] -fill black]
}

proc draw(Line) {x y} {
	if [info exists ::Line] {
		set coords [.c coords $::Line]
		.c coords $::Line [concat $coords $x $y]
		unset ::Line
	} else {
		set ::Line [.c create line $x $y $x $y]
	}
}

proc draw(Move) {x y} {
	set ::ID [.c find withtag current]
	set ::X $x; set ::Y $y
}

proc move(Move) {x y} {
	.c move $::ID [expr {$x-$::X}] [expr {$y-$::Y}]
	set ::X $x; set ::Y $y
}

set modes {Rectangle Oval Line Move}
grid [buttons .1 Mode $modes] -row 0 -column 0
canvas .c -width 600 -height 600 -background white
grid .c -row 1 -column 0

bind .c <1> {draw($Mode) %x %y}
bind .c <B1-Motion> {move($Mode) %x %y}
bind .c <3> {.c delete current}
```

Problems with this program:

1)it should only be possible to draw edges between vertices.
2)it should not be possible to move edges.
3)when a vertice is being moved the edges which are linked with it should be redrawn accordingly(it should still be possible to delete vertices and edges separately).

Any tips, suggestions, code examples which help to solve the mentioned problems greatly appreciated :)

---

### Post by stevescripts on 2008-12-11
No time to look at or comment on your script just now, but this should be helpful:

[http://wiki.tcl.tk/10552](http://wiki.tcl.tk/10552)

If you haven't found the Tcler's Wiki yet, you really need to check it out,
pretty much everything you want to know is addressed there...

Hope this helps a bit.

Steve

---

### Post by Tasma on 2008-12-12
I've been browsing the Tcler's Wiki and checked the program you linked also, but it's different from what I'm doing and didn't help me. Problems 1) and 2) should be fairly easy from the looks and I've tried my own ideas to solve them, but I end up stuck behind errors(my knowledge about tcl/tk syntax is not good enough to understand much of it yet) :/

Thanks for trying to help, hopefully I'll get the issues solved eventually.

---

### Post by stevescripts on 2008-12-12
You actually have a pretty good start ...

Re-think a bit what you are doing - start as simple as possible and build on that.

I still don't have time available to work on your original post

Steve

---

### Post by Tasma on 2008-12-13
I've thought of adding tags to the drawn objects so I could use them to limit the drawing/moving possibilities mentioned earlier, but I haven't found a acceptable way of writing the code.

For example how could I write this if statement with correct syntax?

if {clickable item has the correct tag} {
    ...
}

---

### Post by stevescripts on 2008-12-15
Finding a few minutes today, the following little simple script may
prove helpful...

Button 1 to draw points - button 3 to graph the points - button 2 to toggle from straight lines to spline...

```

#!/usr/bin/tclsh

package require Tk

pack [canvas .c -width 300 -height 300 -bg white]

.c configure -cursor crosshair

set points {}

set smooth 0

proc point {x y} {
	global points
	lappend points $x $y
	.c create oval $x $y [expr {$x + 1}] [expr {$y + 1}] -tags moveable -fill red
	return points
}

proc graph {list} {
	.c create line $list -tags theline
}

bind .c <Button-1> {point %x %y}

bind . <Button-3> {graph $points}

bind . <Button-2> {toggle theline}

proc toggle {tag} {
	global smooth
	if {[string eq $smooth 0]} {
		.c itemconfigure theline -smooth 1
		set smooth 1
		} else {
		.c itemconfigure $tag -smooth 0
		set smooth 0
	}
	return $smooth
}

wm title . "Simple Graph"

if {[string eq $tcl_platform(platform) "windows"]} {
	console show
}


```

I am somewhat unsure just *what* sort of graph you really want - examples
of sine wave, etc are on the wiki.

Hope you find this somewhat helpful.

Steve

---

### Post by Tasma on 2008-12-16
Thanks =) After several hours of browsing I found some useful code pieces on the Tcler'w Wiki also so I managed to fix problems 1 and 2.

The graphs I want are random hand-drawn graphs(possibility to draw vertices and bind them with edges where needed/wanted). These are different from function-graphs(sin, cos, y=x^2 etc). The code I provided in my first post gives a good example of how it should look like(can run it with wish when adding #!/usr/bin/wish to header).

Got an idea of how to solve problem 3 also, but I don't know how to code it or if it's even possible. In case anyone knows: how can I add more tags to objects which already have some when I know the ID of the object(if this is possible)?

---

### Post by stevescripts on 2008-12-16
> **Tasma said:**
> Thanks =)
...
Got an idea of how to solve problem 3 also, but I don't know how to code it or if it's even possible. In case anyone knows: how can I add more tags to objects which already have some when I know the ID of the object(if this is possible)?

$canvas addtag "tagtoadd" withtag "ID" ,

where tagtoadd is the new tag and ID is the tag or ID of the item you wish to add a new tag to ...

Steve

---

### Post by stevescripts on 2008-12-16
Just because I continue to try to get comfortable with a bit of Python, the same
hack in Python, using Tkinter (yes, I know most of you python folks don't use Tkinter ...)

```

#!/usr/bin/python

from Tkinter import *

root = Tk()

root.title("Simple Graph")

root.resizable(0,0)

points = []

spline = 0

tag1 = "theline"

def point(event):
	c.create_oval(event.x, event.y, event.x+1, event.y+1, fill="black")
	points.append(event.x)
	points.append(event.y)
	return points

def canxy(event):
	print event.x, event.y

def graph(event):
        c.create_line(points, tags="theline")

def toggle(event):
        global spline
	if spline == 0:
		c.itemconfigure(tag1, smooth=1)
		spline = 1
	elif spline == 1:
		c.itemconfigure(tag1, smooth=0)
		spline = 0
	return spline

c = Canvas(root, bg="white", width=300, height= 300)

c.configure(cursor="crosshair")

c.pack()

c.bind("<Button-1>", point)

c.bind("<Button-3>", graph)

c.bind("<Button-2>", toggle)

root.mainloop()

```

Hopefully someone might find this interesting.

Steve

---

### Post by Tasma on 2008-12-26
Took a little break, but started working on the program again today and got the third and last problem finally solved too =)

Thanks again Steve for your help

---

