---
title: "Why can't main() return void type? C++"
date: 2009-07-02
forum: Programming Talk
---

### Post by shynthriir on 2009-07-02
This came up in another post of mine, but wanted to ask it officially in another post (so if anyone else has this question, its a lot easier for them to find).

What is the reasoning behind g++ restricting your main() function from having a void return type? I know .NET allows this, which caused a shock to me when I went from .NET on Windows to g++ on Linux. Its not a big issue for me really, but I would like to know why. Any help?

---

### Post by Simian Man on 2009-07-02
Because gcc is more strict enforcing standards than msvc is.  There are a lot of other things that fall outside of standard C++ that msvc will allow and gcc will not (mostly regarding templates).  That said, there are some gcc extensions as well.

As for why the standard says main must return an int, the reason is because C and C++ were developed alongside Unix by Bell Labs.  Unix processes use the int return codes to indicate success or failure when stringing multiple processes together in the shell with && or || operators.  It's just the way they decided to do it.

---

### Post by Nemooo on 2009-07-02
Your program should return an int to tell the OS whether it was executed succesfully or not. O tells it that everything went well and others will mean an error happened.

[http://users.aber.ac.uk/auj/voidmain.shtml](http://users.aber.ac.uk/auj/voidmain.shtml)

---

### Post by shynthriir on 2009-07-02
I figured that might be the reason for it. Microsoft tends to allow people to do sloppy work with anything and clean up for them behind the scenes -- my perspective at least. I've recently started using Linux to do my programming assignments for school and been enjoying it a lot more quite honestly, think because its more rigid on its code handling, it can help me to become a better programmer overall anyway. Thanks.

---

### Post by dwhitney67 on 2009-07-02
From my observation, if you do not explicitly return a value (an int) from your main() function in C++, a zero value will be automatically returned for you.

If you are programming in C, the same also occurs if using the gnu99 (or C99) standard; otherwise if you are using an older standard, than a random value is returned.

These may not factual statements... just what I have observed.

---

### Post by nrs on 2009-07-02
gcc/g++ allows quite a bit of stuff that is contrary, or just unspecified, to the standards. I found that out the hard way: msvc (and others) couldn't compile my code. Usually it's been the other way around. :-P 

Thankfully there is -ansi & -pendantic.

---

