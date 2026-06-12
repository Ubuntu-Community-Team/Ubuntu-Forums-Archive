---
title: "Issue with &quot;geometry&quot; in tcl."
date: 2009-04-18
forum: Programming Talk
---

### Post by tusharv on 2009-04-18
Hi All,

I am facing a bit problem while using geometry in TCL/TK.
This is my code to making window and placing a button in it.

```
wm geometry . 750x500

frame .frm 
grid .frm -row 0 -column 0 -columnspan 5

button .frm.btn -text "press"
grid .frm.btn -row 0 -column 0
```

I am placing button in 0th row and 0th column then also it is coming in the center of window.
Why is it now coming at the top left corner ?

Any Ideas 

Thanks,
Tusharv

---

### Post by tusharv on 2009-04-20
No any Ideas ?

---

### Post by claird on 2009-04-20
> **tusharv said:**
> Hi All,

I am facing a bit problem while using geometry in TCL/TK.
This is my code to making window and placing a button in it.

```
wm geometry . 750x500

frame .frm 
grid .frm -row 0 -column 0 -columnspan 5

button .frm.btn -text "press"
grid .frm.btn -row 0 -column 0
```

I am placing button in 0th row and 0th column then also it is coming in the center of window.
Why is it now coming at the top left corner ?
...

Please ask the question again.  I expect to see the 0th row and column in the upper-left, and indeed it's there for me, and apparently for you.  Apparently at some time in the past, this same code--or perhaps similar, but different, source--produced a button that appeared in the center of the window.  Do I have that right?  And so are you asking why source code that you apparently no longer have did something different from the source code you have now?

---

### Post by stevescripts on 2009-04-20
Tusharv,

It seems to me, that you may be seeking the results that place would provide, rather than pack or grid.  Both pack and grid are propagating geometry managers, and will override any width and height configuration given to the frame at time of creation.

Is *this* the sort of appearance you were expecting?

```

wm geometry . 600x400

frame .f -width 200 -height 200 -bg red

button .f.b -text "Press" -bg white

place .f -anchor nw

place .f.b -anchor nw

```

It would help me (and others) to help you, if I had a better understanding of your overall programming expierence in general, and your tcl/tk expierence in particular...

It might also help, if we knew what (if any) books/tutorials you may be using.

Hope this helps a bit.

Steve

---

### Post by tusharv on 2009-04-21
Hi stevescripts,

It is a good example.
But "place" will take the all arguments in terms of pixels.
Now if I want to place 2 buttons in a single row, by using grid I can simply place them but dont you think with the help of pixels it will be awkward ?
And again if I change the geometry I have to again change the place of that button.

Thanks,
Tushar

---

