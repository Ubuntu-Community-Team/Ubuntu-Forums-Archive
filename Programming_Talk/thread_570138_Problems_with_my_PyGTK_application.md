---
title: "Problems with my PyGTK application"
date: 2007-10-07
forum: Programming Talk
---

### Post by maddog39 on 2007-10-07
Hello all,

I've been writing this programmers text editor in PyGTK (mostly for educational purposes) and I'm having some trouble debugging. Basically I am connecting a callback and passing on the instance of a class which will allow that callback to do some things. However when that callback is called it doesn't do anything. Although all the other callbacks seem to work fine and if I call this function I am trying to call from the callback, from the __init__ of the class itself, it works fine also. I've tried checking data types too, and they are fine as well. So I have no idea whats going wrong here or obviously how to fix it. Python isn't giving me any information either.

So I make the connection to the callback at  line 26 in main.py, and the callback is called in on_new_activate in callbacks.py. All the source code is available from SVN:
[http://gse.svn.sourceforge.net/viewvc/gse/branches/gsepy/](http://gse.svn.sourceforge.net/viewvc/gse/branches/gsepy/)

Help is much appreciated.

Thanks!
-maddog39

---

