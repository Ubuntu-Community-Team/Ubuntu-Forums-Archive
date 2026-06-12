---
title: "How to bind Enter key with any button in TCL ?"
date: 2009-05-07
forum: Programming Talk
---

### Post by tusharv on 2009-05-07
Hi All,

I am working in TCL/TK.

When I am binding "Enter" key with any button. it just invoked when i take cursor on button.

```
proc display {} {
  tk_messageBox -message "Bind is working."
}

button .btn -text "press me" -command display
pack .btn

bind . <Enter> ".btn invoke"
```

Here I have bind the "Enter" key of key-board with button but it not working but if I move my mouse cursor on button then button is getting invoked. I think I am missing some thing while binding Enter key, As if I bind any other key then it works fine.

Any solution ?

Thanks,
Tusharv

---

### Post by stevescripts on 2009-05-07
Tusharv -

You are binding to the wrong event ... ;)

Change the line:
```

bind . <Enter> ".btn invoke"

```
to read:
```

bind . <Return> ".btn invoke"

```

As I never can remember all of the correct key names, I keep a copy of this hanging around handy:
```

package require Tk

pack [text .t -bg white]

bind .t <KeyPress> {puts "You pressed the key named: %K "}

bind .t <ButtonPress> {puts "You pressed button: %b at %x %y"}


```

Always a good idea to consult either the man pages for bind 
(man n bind) or the on-line docs: [http://www.tcl.tk/man/tcl8.5/TkCmd/bind.htm](http://www.tcl.tk/man/tcl8.5/TkCmd/bind.htm)

to help ensure that you are using the correct event.

Hope this helps a bit.

EDIT:  I also find it a good idea when writing production code, to bind to key/mouse **releases**, rather than key/mouse presses - this way you don't interfere with the default Tk bindings

Steve

---

### Post by stevescripts on 2009-05-07
As a bit of an afterthought, a quick hack to demo some events other than key/mouse presses:

```

package require Tk

frame .main

foreach i {1 2 3 4} {
	grid [canvas .main.c$i -width 50 -height 50 \
          -relief groove -bd 2] -row 0 -column [expr {$i -1}]
}

bind . <Enter> {puts "Entered widget: %W"}
bind . <Leave> {puts "Left widget: %W"}

pack .main

```

Maybe somebody will find it useful...

Steve

---

