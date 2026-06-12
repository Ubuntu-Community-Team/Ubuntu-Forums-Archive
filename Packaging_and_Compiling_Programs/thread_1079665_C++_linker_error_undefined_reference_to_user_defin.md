---
title: "C++ linker error undefined reference to user defined function"
date: 2009-02-24
forum: Packaging and Compiling Programs
---

### Post by JebusWankel on 2009-02-24
here's my code
[http://pastebin.com/d2640019b](http://pastebin.com/d2640019b)
If you try to run it you should probably comment out the system("pause") line which doesn't seem to be liked by g++.

When I compile it I get the error   
```
[Linker error] undefined reference to `myfun(double, double&, double&, double&)' 
```

My friend tried to explain the error to me but he thought i used some sort of external header or secondary .cpp file which I don't.

Prompt help would be greatly appreciated :)

---

### Post by JebusWankel on 2009-02-24
I realize this forum isn't really for teaching noobs to program, but I had to submit this assignment electronically and I didn't have time to use anything else. In retrospect I should have posted to the main forum to get the eyes.

I submitted the non-working code and emailed the grader a working version that got around the problem by not using the void function, though using a void function was part of the assignment. Wish me luck.

To any mods: feel free to delete this thread. The link to the code will expire in a day so it won't be of much use.

---

