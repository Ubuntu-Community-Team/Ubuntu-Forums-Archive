---
title: "Kivy GestureStroke Question"
date: 2015-11-06
forum: Programming Talk
---

### Post by Benicio_Khan on 2015-11-06
I'm pretty much a noob at python(Just started), so I didn't know how to solve this...(I'm doing this in Android):

------------------------------
(A)


#Here we have where I imported kivy's GestureStroke as gs..


import kivy, kivy.gesture;from kivy.gesture import GestureStroke as gs

#I tried to add a new point and save as variable 'coords'


coords = gs.add_point(gs(66,-33))
 

------------------------------
I also tried:

(B)

import kivy, kivy.gesture;from kivy.gesture import GestureStroke as gs

coords = gs.add_point(66,-33)


------------------------------
In terminal I get(A) :


__init__() takes exactly 1 argument (3 given)


And(B):


Unbound method add_point must be called with GestureStroke instance as first argument(got int instance instead)



#...Any idea how to solve this? Sorry that this isn't exactly in Ubuntu , I needed help and I didn't know where to go...Any help or advice would be appreciated, thanks.

---

