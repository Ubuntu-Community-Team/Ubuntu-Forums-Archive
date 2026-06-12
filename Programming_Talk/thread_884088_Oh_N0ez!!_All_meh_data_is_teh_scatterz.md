---
title: "Oh N0ez!! All meh data is teh scatterz"
date: 2008-08-08
forum: Programming Talk
---

### Post by ChazZeromus on 2008-08-08
Hello, I'd like to know the linking commands to put all the code and data separately.  When I link my object files together, the data and code sections are in the order of which they where linked.  So an object file had code and then data, and in the final image I have it in the following order: code, data, code, data, code, data.
What are the command line options to put all the section types in individual groups so that the object files are linked this: code, code, code, code, data, data, data, etc.?

---

### Post by Zugzwang on 2008-08-11
I don't think there is any command since there is no real necessity for this. If there is one that could be tweaked to perform your task, it is likely to be in the binutils package.

BTW: Why do you want to do this?

---

