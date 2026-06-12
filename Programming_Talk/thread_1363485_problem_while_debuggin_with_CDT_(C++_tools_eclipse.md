---
title: "problem while debuggin with CDT (C++ tools eclipse)"
date: 2009-12-24
forum: Programming Talk
---

### Post by BramWillemsen on 2009-12-24
Hi everybody,

I am quite new to C++ and to CDT. I made a 2D array of integers on the heap. When i select this 2D array in the debug perspective of CDT, there is no option to display it as an array for some reason. I read some tutorials and they tell me that this option should be there.

[http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-](http://i35.photobucket.com/albums/d174/Brasempje/Screenshot-) 5.png

This picture shows a 2D array of integers called 'mat'. Right clicking on 'mat' or '*mat' does not give me the option to display as an array. It only shows the first value of the array where the pointer points to. I am using CDT 6.0.0 in eclipse Galileo. I am hoping that someone with some CDT experience can tell me if i am doing something wrong. Searching on google did not give the answer.

regards Bram

fixed! It seemed like i was using a different debugger

---

### Post by not_a_phd on 2009-12-24
Could you please give more details of how you fixed this? Especially, how did you determine which debugger you were using within Eclipse? How did you select another debugger?

I have issues with the load time of my Eclipse CDT debugger on multiple machines and Linux distros, and have been banging my head how to fix it. Maybe it is a debugger selection issue...

Thanks in advance.

---

