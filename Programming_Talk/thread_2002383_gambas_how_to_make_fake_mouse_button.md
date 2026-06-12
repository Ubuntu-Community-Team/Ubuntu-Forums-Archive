---
title: "gambas how to make fake mouse button"
date: 2012-06-12
forum: Programming Talk
---

### Post by psihokiller4 on 2012-06-12
I'm using gambas 3.1.1

well I know how to do mouse move
```
mouse.move(x,y)
``` (component gb.desktop)

I know how to do key press
```
Desktop.SendKeys("a")
``` (component gb.desktop)

how go I make "fake" mouse press

how do I make "fake" key up press? - as
```
Desktop.SendKeys(Key.up)
``` - doesn't work properly

---

### Post by kalaharix on 2012-06-13
I don't know what you are trying to do but will say that it is unusual to send key events to a program which itself is event driven. Presumably after you have 'sent' the mouse event, you then want to do something. Well just do it by invoking the mouse class that you want to use.

Here is a simple example (I am assuming Gambas 2 not 3):
Drag the following onto a new projects FMain form: a TextBox, two buttons and a timer (from special tab). Leave all default object names as Gambas assigns them (TextBox1, Button1, Button2, Timer1)

Open the FMain class file. Paste the following below the two default classes (or delete the default classes [_new() and Form_open()] first.

When you run the program, the button1 class will flip the textbox. Clicking Button2 will automate this by invoking button1_mouseup() every second. I have used the mouseup events but could just as easily have used the click or mousedown events.
```

'--------------------------------------------------
PUBLIC SUB Button1_MouseUp()
  IF TextBox1.Text = "TextBox1" OR TextBox1.text = "flip" THEN 
    TextBox1.text = "flop"
  ELSE 
    TextBox1.text = "flip"
  ENDIF 
END
'--------------------------------------------------
PUBLIC SUB Button2_Click()
  IF Timer1.enabled THEN 
    Timer1.Enabled = FALSE
  ELSE 
    Timer1.Enabled = TRUE
  ENDIF 
END
'--------------------------------------------------
PUBLIC SUB Timer1_Timer()
  Button1_MouseUp()
END
'--------------------------------------------------
```

---

### Post by psihokiller4 on 2012-06-13
sorry I'm using gambas 3.1.1

no sorry it's not what I wanted this are turning on and off buttons witch doesn't matter for mouse press (except for beginning)

what I want is that program would press mousebutton
and not actually changing button or initialising button properties

I don't want to follow function that's on that button but that it presses mouse button and IF there's a function on that button that it follows it

I don't know how to explain

like autokey program but that would be written in gambas


maybe what distract you (fake)
why "fake" don't know 
> Send fake keyboard events
[http://gambasdoc.org/help/comp/gb.desktop/desktop/sendkeys](http://gambasdoc.org/help/comp/gb.desktop/desktop/sendkeys)

---

### Post by psihokiller4 on 2012-06-21
bump anyone knows how could I manage that with bypasses? system calls or whatever?

---

