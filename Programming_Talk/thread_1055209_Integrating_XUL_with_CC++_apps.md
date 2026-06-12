---
title: "Integrating XUL with C/C++ apps"
date: 2009-01-30
forum: Programming Talk
---

### Post by bluedalmatian on 2009-01-30
I've built a GUI in XUL which I can currently run using xulrunner.  The backend of my app, the bit that actually does the work, is written in C++.

What I'd like to do is have my app run as its own process, rather than the xulrunner process. I've seen references to libxul and I suspect this is what I need?

If I  link my app with that, then will libxul provide functions I can call to open xul files, pass data in from C, and get the results from the GUI back?

I cant find any documentation for libxul. The only thing I can find is:
[https://developer.mozilla.org/en/XULRunner/Deploying_XULRunner_1.8](https://developer.mozilla.org/en/XULRunner/Deploying_XULRunner_1.8)

which seems to be the start of what Im trying to do but it doesnt go into any detail.

---

