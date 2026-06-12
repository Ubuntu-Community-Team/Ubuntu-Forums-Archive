---
title: "Timelines in Python and Clutter"
date: 2010-05-30
forum: Programming Talk
---

### Post by Admiral Yi on 2010-05-30
I'm trying to learn python and clutter, and I have written a timer. However, it won't update. The code just runs once and won't loop. I have tried using while to make it loop, but it doesn't work because I'm using clutter. 

Heres my code:

```
import commands
import clutter

X = 1
Start_Time = commands.getoutput('date -u +%s')
Minutes = 0
Hours = 0
Days = 0

while X == 1:
  stage = clutter.Stage()
  stage.set_size(150,80)
  stage.set_title('Timer')
  green = clutter.Color(0,255,0,255)
  black = clutter.Color(0,0,0,255)
  stage.set_color(black)
  stage.connect("destroy", lambda q: clutter.main_quit())
  stage.show_all()

def timer():
  Time = commands.getoutput('date -u +%s')
  Seconds = int(Time) - int(Start_Time)

  if Seconds == 60:
    Minutes = Minutes + 1
    Seconds = 0
    Start_Time = commands.getoutput('date -u +%s')

  if Minutes == 60:
    Hours = Hours + 1
    Minutes = 0

  if Hours == 24:
    Days = Days + 1
    Hours = 0

  text = clutter.Text()
  text.set_position(0,60)
  text.set_color(green)
  text.set_text(str(Seconds)+' Seconds')
  stage.add(text)

  text = clutter.Text()
  text.set_position(0,40)
  text.set_color(green)
  text.set_text(str(Minutes)+' Minutes')
  stage.add(text)

  text = clutter.Text()
  text.set_position(0,20)
  text.set_color(green)
  text.set_text(str(Hours)+' Hours')
  stage.add(text)

  text = clutter.Text()
  text.set_position(0,0)
  text.set_color(green)
  text.set_text(str(Days)+' Days')
  stage.add(text)

  clutter.main()
```

How do I make it loop so that the seconds update? Apparently I need to use a 'Timeline' function. I tried follow a guide, but the code I wrote just ended up crashing the whole computer. I don't really understand it much, can anyone help?

---

### Post by gmargo on 2010-05-30
I'm just learning python, but the first thing that jumps out to me is the infinite loop (X == 1) where you are repeatedly recreating the clutter Stage.  You never call clutter.main and the timer is defined but never used  (And what if "Seconds" == 61?)  It would also help if you could point to the tutorial you were following.

---

