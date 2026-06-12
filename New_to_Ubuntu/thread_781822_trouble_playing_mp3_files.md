---
title: "trouble playing mp3 files"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by fignig on 2008-05-04
so i'm trying to play some music and i installed numerous programs to help such as: 

-rhythm box
-noatun
-amarok

neither of these will start to play, i don't get it, i installed them thru the add/remove progrmas under applications. i'll put the mp3 on the playlist and try to play it, but all i get is nothing, they won't even START playing...

---

### Post by ChompTheMan on 2008-05-04
Have you installed Ubuntu Restricted Extras?  You can install this through add/remove programs or through the terminal with:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SunnyRabbiera on 2008-05-04
you probably need the restricted extras packages.
Easy to solve, go up to system then go to administration and click on "synaptic package manager"
synaptic is like an advanced version of add/remove with most of the same basic function, once you type in your password and get into synaptic go to "settings" in synaptic and go to "repositories"
a little window will appear and make sure that all the little boxes except the last one are checked off, then go to the second tab labeled third party software and make sure that things are checked there too except the source code repositories.
after checking things off hit refresh and then search for ubuntu-restriced-extras
that should give you what you need.
installing things in syaptic is very easy, use this guide for more help:
[here]("http://monkeyblog.org/ubuntu/installing/")

---

