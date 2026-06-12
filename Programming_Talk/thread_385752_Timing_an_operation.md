---
title: "Timing an operation"
date: 2007-03-16
forum: Programming Talk
---

### Post by Darkness3477 on 2007-03-16
Hi, I made a program today that adds +1 to i while i doesn't = 100000000 (So it counts up to 1000000000) just to see how fast it does it. And, well, it's pretty fast. 

So, I'm just wondering how I could go about timing it so I can see exactly how fast it is. 
It's not very important I do this, I was just curious as to exactly how fast (Other then extremely fast) my computer computes simple operations.

So, I know you can do this somehow, I'm just not sure how. Whether you need to write it into the program or your can time how long it takes a program to execute from the command line. Either way, some information would be useful.

Hopefully it's through the command line, and I can do this with any program (Not just executables, but python scripts) so I can compare the difference. As said, I'm interested in this and don't *need* to know it other than to satisfy my own curiosity.
Thanks for any help you guys can give.


P.S. I've tried searching google and couldn't find anything helpful, perhaps I'm asking(searcching) the wrong things. 
P.S.S My program is in C++

---

### Post by yabbadabbadont on 2007-03-16
time programname program parameters

Edit: man 1 time
for details

---

### Post by Darkness3477 on 2007-03-16
Wow, that was quick. Thanks very much!

---

### Post by hod139 on 2007-03-16
The C++ timing functions are not very accurate for values smaller than 1/100th of a second.  A much more accurate way for timing can be found at [Professor Musser's page]("http://www.cs.rpi.edu/%7Emusser/gp/timing.html").  The basic idea is to count how many times the function can be executed in one second, and then you can compute the time for a single execution.  He even provides source for his [timer class]("http://www.cs.rpi.edu/%7Emusser/stl-book/source/timer.h") and some [examples]("http://www.cs.rpi.edu/%7Emusser/stl-book/source/ex19-01a.cpp").

---

### Post by Darkness3477 on 2007-03-16
Thanks, I'll look into that in when I have a chance! I think, possibly, I'll be using these tools for my major assignment for SDD (Software Design and Development). I'm probably gonna be doing something with optimization and seeing how small changes can make pretty big difference in execution time.... Stuff like that.

---

