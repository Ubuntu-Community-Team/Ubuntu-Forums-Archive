---
title: "How to manage length and width of all windows ?"
date: 2009-04-02
forum: Programming Talk
---

### Post by tusharv on 2009-04-02
Hi All,

I want to make a tool in which there will be multiple windows when user press next -> next buttons.

So when user press next button in every window new window will be generate, so how can I manage the same length and width of these windows As there will be different contents in all window?

How can I set length and width of main window,the window which is generated when i run program and that I can't destroy ?

Thanks,
Tusharv

---

### Post by jiena on 2009-04-02
On the top right-hand corner of your window there are three icons:
a minus, a square, and an X.  The square lets you maximise or unmaximise your window size.  Click the square and, if the window does not shrink at all, click it again.  On one of these 'clicks' you should be able to adjust the size to your requirements by going to the edge of your window with your mouse until the shape of the cursor changes.  Press and hold the left button while you drag the edge to your preferred destination.  The quickest way is to go to the bottom right-hand corner of your window.  From there you can drag in the same way as before; only now you can adjust both height and width at the same time.

---

### Post by tusharv on 2009-04-02
> **jiena said:**
> On the top right-hand corner of your window there are three icons:
a minus, a square, and an X.  The square lets you maximise or unmaximise your window size.  Click the square and, if the window does not shrink at all, click it again.  On one of these 'clicks' you should be able to adjust the size to your requirements by going to the edge of your window with your mouse until the shape of the cursor changes.  Press and hold the left button while you drag the edge to your preferred destination.  The quickest way is to go to the bottom right-hand corner of your window.  From there you can drag in the same way as before; only now you can adjust both height and width at the same time.

I am not talking about the how to use my mouse.

I am making this tool in **TCL/TK.**

So with the help of programming how can I make sure that the windows that are generated from the program are of same length and same width.

Thanks,
Tushar

---

### Post by stevescripts on 2009-04-02
Tushar,

First a couple of quick questions...

Are you using any tutorials?  If so which one(s)?

Do you know about the tcler's wiki?  

[http://wiki.tcl.tk/](http://wiki.tcl.tk/)

I will hack out a quick example after lunch today, if I can find a few minutes.

Steve

---

### Post by stevescripts on 2009-04-02
> **tusharv said:**
> Hi All,

I want to make a tool in which there will be multiple windows when user press next -> next buttons.

So when user press next button in every window new window will be generate, so how can I manage the same length and width of these windows As there will be different contents in all window?

How can I set length and width of main window,the window which is generated when i run program and that I can't destroy ?

Thanks,Tusharv

Perhaps this little snippet will give you a starting place:

```

#! /usr/bin/tclsh

package require Tk

set width 100
set height 100

pack [button .b1 -text "Press me" -command {mycommand}]

proc mycommand {} {
	global width height
	foreach i {a b c d} {
	toplevel .$i -width $width -height $height
	}
}

```

Note, that toplevel windows, even though you have specified a height and width, are container widgets, and will normally expand/shrink to
accommodate the widgets you create inside them.

To get full control of your application you will need to look into the proper ways to control the geometry manager that your app is using (ie, pack or grid)

For information of pack or grid, type man n pack in a terminal.

Hope this helps a bit more.

You can specify the height and width of the main window by using configure:

```

. configure -width 200 -height 300

```

however again, the toplevel is a container and will normally shrink/expand to accommodate the widgets it contains...


Steve

---

