---
title: "C / C++ gui to console commands?"
date: 2009-02-12
forum: Programming Talk
---

### Post by StOoZ on 2009-02-12
just wondering , not that im looking to create something like that... 

Is it possible to create a GUI using C / C++ , to a console command??

If so , how do you 'grab' its output???
for example , lets assume we create a gui for the 'ls' command , so how to I 'grab' the output of 'ls -lh' for example , and show it in a text box?


(I've already programmed in wxwidgets.... but nothing similar to this)

---

### Post by stevescripts on 2009-02-12
StOoZ - some reason you require C/C++ ?

Things like this real simple in scripting languages.

Tcl/Tk example:

```

#! /usr/bin/tclsh

package require Tk

pack [text .t]

set result [exec ls -l]

.t insert 1.0 $result

```

Scrollbar left as an exercise ... ;)

Were I to *need* such a thing in C/C++, I would simply embed tcl/tk, and the little script, FWIW

Steve

---

### Post by PaulM1985 on 2009-02-12
I think the example you gave for listing files in a directory is OS dependent and it seems after looking on google that specific .h files have to be included.  

As far as console commands to be done in a GUI, I am not sure how exactly to go about doing it, but I would look at trying to display the information you require possibly by including specific header files and libraries rather than taking a command line output and manipulating it.

Sorry I couldn't be more specific.  I am more Java programming than C.

Paul

---

### Post by stevescripts on 2009-02-12
yep the ls is OS dependent, was the OP's question - to do this cross-platform I would have used tcls glob ...

Steve

---

### Post by jimi_hendrix on 2009-02-12
> **stevescripts said:**
> StOoZ - some reason you require C/C++ ?

Things like this real simple in scripting languages.

Tcl/Tk example:

```

#! /usr/bin/tclsh

package require Tk

pack [text .t]

set result [exec ls -l]

.t insert 1.0 $result

```

Scrollbar left as an exercise ... ;)

Were I to *need* such a thing in C/C++, I would simply embed tcl/tk, and the little script, FWIW

Steve

i love tcl and gui's...its so elegent </OT>

---

### Post by stevescripts on 2009-02-12
> **jimi_hendrix said:**
> i love tcl and gui's...its so elegent </OT>

Me too ;)

There was I time, when I beat my head bloody on the wall, using M$ MFC
(Many Fine Classes ...) LOL

For many years now, I just use whatever flavor of Tk is available for GUI stuff...

Steve

---

