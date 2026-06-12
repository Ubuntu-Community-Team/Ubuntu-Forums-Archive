---
title: "Can't see GASP graphics"
date: 2010-08-09
forum: Programming Talk
---

### Post by Czarli on 2010-08-09
Hello,

I'm a beginner in using Python for programming (actually, I'm a beginner in programming.) I am self-studying Python using [http://openbookproject.net//thinkCSpy/](http://openbookproject.net//thinkCSpy/) and am currently on the topic about using GASP for creating simple graphics.

Now, my problem is that when I try to run GASP, I can't see the graphic. Here is the code I am trying to run:

```
from gasp import *

begin_graphics()                # open the graphics canvas

Box((20, 20), 100, 100)
Box((55, 20), 30, 50)
Box((40, 80), 20, 20)
Box((80, 80), 20, 20)
Line((20, 120), (70, 160))
Line((70, 160), (120, 120))

update_when('key_pressed')
end_graphics()
```I programmed this using gedit Text Editor in Ubuntu 10.04. The name of the file is house.py

I run this program in the terminal by importing it:

```
from house import *
```

Now, the GASP window opens but I can't see anything. When I tried last time, it seemed to be working fine. But when I tried it now, all I can see is a blank GASP window (See Screenshot-GASP.png)

But, according to the exercise, I should look something like this:

[IMG]http://openbookproject.net//thinkCSpy/_images/gasp02.png[/IMG]

Is there something I'm doing wrong?

I hope somebody can help. Thank you.

---

### Post by OgreProgrammer on 2010-08-09
Your code worked fine for me. It drew a little house. Not sure what the problem could be.

---

### Post by Czarli on 2010-08-09
> **OgreProgrammer said:**
> Your code worked fine for me. It drew a little house. Not sure what the problem could be.

Yes, it's kind of frustrating to me, especially I'm only a beginner. Actually, it works fine before but now, it only returns a blank window.

But I have found some kind of a solution. I found this out when I looked into the backend.py file in the GASP folder. it says:

```
# diffrent update_when values
NOTHING = "Nothing"
MOUSE_PRESSED = "Mouse_Pressed"
KEY_PRESSED = "Key_Pressed"
screen = None
```So, I changed 'key_pressed' to 'Key_Pressed' and it returned the little house that it supposed to be drawing.

However, in the python shell, although it now returns the drawing, it says:

```
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "house.py", line 12, in <module>
    update_when('Key_Pressed')
  File "/usr/lib/pymodules/python2.6/gasp/api.py", line 644, in update_when
    else: raise backend.GaspException("update_when must take of 'key_pressed', 'mouse_clicked', or 'next_tick'")
gasp.backend.GaspException: "update_when must take of 'key_pressed', 'mouse_clicked', or 'next_tick'"
```Well, this might do for me now. At least, now I can draw. :D

---

