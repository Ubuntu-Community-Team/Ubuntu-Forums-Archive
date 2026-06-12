---
title: "Is mod_python really dead?"
date: 2010-08-07
forum: Programming Talk
---

### Post by bg11 on 2010-08-07
So, after the responses in [this](http://ubuntuforums.org/showthread.php?t=1542940) thread, I decided to ditch php for python for server side coding.  Mod_python was recommended and seems to work quite well.

But, take a look at [this article](http://blog.dscpl.com.au/2010/05/modpython-project-soon-to-be-officially.html), [this post](http://blog.dscpl.com.au/2010/06/modpython-project-is-now-officially.html) and [this one](http://www.charlesdietrich.com/blog/2009/02/10/mod_python-is-dead-long-live-mod_wsgi/).  These claim that mod_python is dead!  And further that mod_wsgi should be used in its place, but I've only ever heard people recommend mod_python.

People commenting on these posts claim there are terrible bugs in mod_python, apparently it destabilises apache.

Time to switch to mod_wsgi?

---

### Post by DanielWaterworth on 2010-08-07
wsgi is the way to go. It's used by most if not all python frameworks and it's quick and easy to work with. What's not to like?

---

