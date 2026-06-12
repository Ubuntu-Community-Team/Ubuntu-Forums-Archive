---
title: "How to install most recent mesa3d using command line?"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by deri on 2013-04-23
Help.

---

### Post by cortman on 2013-04-23
Instructions [here]("http://www.mesa3d.org/install.html") (first Google result).

---

### Post by deri on 2013-04-23
I want to install the deb package, not compile itself. 

You have to do a apt-cache search and choose right package.

I have 9.1 something, but newer is 9.2 or something like that.

---

### Post by cortman on 2013-04-23
Running apt-show-versions on libgl1-mesa-glx reveals that the current package for Quantal is version 9.0.3. Usually if you want a version newer than what's available in the repositories, you need to compile it.

---

