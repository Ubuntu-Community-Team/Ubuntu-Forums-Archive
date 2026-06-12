---
title: "GASP for python in Ubuntu  Netbook edition"
date: 2010-12-14
forum: Programming Talk
---

### Post by nervusvagus on 2010-12-14
Hello,

I'm trying to learn Python and thats the primary reason I installed Ubuntu. 

The GASP package does not currently support Windows so I think it would be smoother with Ubuntu on my netbook. Can someone running Ubuntu 10.10 and has GASP installed tell me if they can run the following code without issues:
```

from gasp import *

begin_graphics(800, 600, title="Catch", background=color.YELLOW)
set_speed(120)

ball_x = 10
ball_y = 300
ball = Circle((ball_x, ball_y), 10, filled=True)
dx = 4
dy = 1

while ball_x < 810:
    ball_x += dx
    ball_y += dy
    move_to(ball, (ball_x, ball_y))
    update_when('next_tick')

end_graphics()
```


for me, a yellow screen appears temporarily and then I get:

[I]>>> from gasptry import *
Exception in thread QueueFeederThread (most likely raised during interpreter shutdown):
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 532, in __bootstrap_inner
  File "/usr/lib/python2.6/threading.py", line 484, in run
  File "/usr/lib/python2.6/multiprocessing/queues.py", line 242, in _feed
<class 'cPickle.PicklingError'>: Can't pickle gasp.api.Circle: import of module gasp.api failed[/I]

---

### Post by siggi2 on 2011-01-30
I have not 10.10 but 10.04, and there is no problem!

---

### Post by woodygar on 2011-02-18
works fine on 

woodygar@ubuntulaptop:~/home/komo/learning python$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick
woodygar@ubuntulaptop:~/home/komo/learning python$ python
Python 2.6.6 (r266:84292, Sep 15 2010, 16:22:56) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

This may be obvious to you but i was trying to use gasp in idle and it just wouldn't work(took me a long time to realise it might be the ide). But komodo edit is compatible to use as an ide

---

