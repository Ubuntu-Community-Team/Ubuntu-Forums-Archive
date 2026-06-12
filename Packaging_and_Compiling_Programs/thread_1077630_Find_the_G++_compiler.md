---
title: "Find the G++ compiler"
date: 2009-02-22
forum: Packaging and Compiling Programs
---

### Post by wolfman1221 on 2009-02-22
I believe I have installed the build essential package, but I am having trouble finding the G++ compiler. 


If someone could help me with this, it would be much appreciated.

---

### Post by deepclutch on 2009-02-22
obviously ,you have to install g++ seperately.it is another package.

---

### Post by wolfman1221 on 2009-02-22
I apologize, I'm a newbie. Just how exactly do I do that?

---

### Post by zekopeko on 2009-02-22
open synaptic package manager and look for g++ (read the description) and simply right click install.

---

### Post by wolfman1221 on 2009-02-22
Okay, I did that. So how do I find so I can use it now?

---

### Post by deepclutch on 2009-02-22
if you have installed ,then open a terminal and start using it  :) 
-
I hope you know g++ usage?
[http://www.usna.edu/Users/cs/needham/courses/si221/spr07/WEBgppIntro.ppt](http://www.usna.edu/Users/cs/needham/courses/si221/spr07/WEBgppIntro.ppt)
--
you may be knowing about environment variables;right?(since you are into programming). this means simply invoking g++ is enough.above link shows.

---

### Post by Leo Dragonheart on 2009-02-22
I am guessing you are trying to compile something so here goes.

open the terminal and go the the folder of the file you want to compile..

then type in the following commands...

```
g++ -Wall "Filetocompile.cpp" -o executable

chmod u+x executable

./executable
```

That's it...I hope that helps and good luck.

---

