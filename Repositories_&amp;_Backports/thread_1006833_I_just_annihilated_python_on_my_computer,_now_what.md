---
title: "I just annihilated python on my computer, now what?"
date: 2008-12-09
forum: Repositories &amp; Backports
---

### Post by OffbeatPatriot on 2008-12-09
I was having problems with wxPython giving me an error every time I imported wx and I got pretty fed up with it.  I tried every solution I could think of and wanted to remove and install python in synaptic but that required me to remove a whole lot of other things with it and finally I came up with a brilliant idea, I would delete any mention of python and wx in /usr/ with sudo nautilus and then go into synaptic and install it again.  I've done that and the first bad sign was when synaptic still seemed to think python was on my computer, then I saw the reinstall option for the first time(wish I'd tried that first) and thought it was okay.  I reinstalled python but now there is no python executable in my usr/bin/ folder

---

### Post by bapoumba on 2008-12-10
That was quite a bad idea. Always remove with the package manager ;)
The only way I know of reinstalling packages deleted that way is to download them ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)) + dependencies, and install them back with dpkg.

---

