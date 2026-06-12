---
title: "Recommend good PyGTK program to study"
date: 2008-10-08
forum: Programming Talk
---

### Post by Flimm on 2008-10-08
Can anyone recommend any good PyGTK open source programs that I could study? Specifically, the code, although GUI design also interests me.

In the past I've looked at the code of Wine-doors and update-manager, and I've learned quite a few neat tricks from doing that. I would like to study some more programs, preferably using PyGTK, but any python projects would be profitable to me.

Bonus points if the project code is hosted on Launchpad. ;)

Secondary question: how useful have you found studying other peoples' code? Do you do it at all?

---

### Post by LaRoza on 2008-10-08
sysres.

Get the source: [https://launchpad.net/sysres](https://launchpad.net/sysres)

Meet the developers: [http://laroza.19.forumer.com/index.php](http://laroza.19.forumer.com/index.php)

---

### Post by Flimm on 2008-10-20
Thanks, Sysres' code was quite interesting, it's fascinating to see how flexible python is, there's no one way to do it. For example, in my projects, I always symlink the /usr/bin/app to /usr/share/app/app.py and give app.py execute permissions, whereas you made /usr/bin/sysres an actual python file that appended to sys.path to import the other modules.
I would be very interested in knowing how you package your program into a .deb file. Previously, I just followed [this tutorial](https://help.ubuntu.com/community/PythonRecipes/DebianPackage), but it's obviously limited.
LATER: hmm, looks like somebody has turned an IRC session into a python packaging guide, I'll go and take a look at it now. ([https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python))

---

