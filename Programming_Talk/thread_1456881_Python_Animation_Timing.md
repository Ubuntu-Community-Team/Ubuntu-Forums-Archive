---
title: "Python Animation Timing?"
date: 2010-04-17
forum: Programming Talk
---

### Post by cabse7en on 2010-04-17
Hey guys,

I'm a student who's been doing a lot of coding in C/C++ for about 4 years now and I'm just starting to dabble in some Python (my world was pretty much blown open when I started to do things that used to take a 100 lines of C with a single line in Python, feels *really* weird, but it's quite fun!)

Anyways, I'm currently working on sprite animation tool for an XNA game I'm working on (It's exporting information to XML for me to work with later), and I'm trying to figure out a way to time the sprite animation inside the python tool. For example, assuming I have all of my appropriate frame data and drawing functions, how would I go about coding the timing to display it at 30 frames per second (or any other arbitrary rate).

Thanks!

---

### Post by schauerlich on 2010-04-18
```
while someBoolFunc():
    drawFrame(getNextFrame())
    time.sleep(1/30)
```

---

