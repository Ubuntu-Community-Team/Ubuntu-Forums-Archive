---
title: "Weekalarm trouble"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by ucal on 2008-05-10
So I'm getting better at linux, and I love it so far.  If things continue to go this swimmingly, I may be drastically reducing my windows partition (if not removing it entirely).  My issue right now is that whenever I try and run the weekalarm amarok script, I end up with this error:

```
File "/home/me/.kde/share/apps/amarok/scripts/weekalarm/weekalarm.py",line 24, in <module>

import amarok

File "/home/me/.kde/share/aps/amarok/weekalarm/amarok.py",line 1,in <module>

from qt import *

ImportError: No module named qt 
```

Going off of a quick google search, I installed several python programs qt4 being one of them, but to no avail.  Any ideas?

---

### Post by ucal on 2008-05-10
bump

---

### Post by ucal on 2008-05-10
bump

---

### Post by ucal on 2008-05-10
Bump

---

### Post by Monicker on 2008-05-10
A bit excessive on the bumps, methinks.

That being said, you should say which python packages you installed.

The README for the application says you need PyQT as a prerequisite.  There are a couple of packages for that.  Which, if any, did you install?

---

### Post by ucal on 2008-05-10
Really?  I've just been bumping it whenever it hits the second page, because in my experience, no one ever looks there.  I'll tone it down though if its a problem.

EDIT:  

Of Pyqt, I have 
pyqt4-dev-tools.  
pyqt tools

Other than that I have

python
python qt4 sql
python qt4
python qt4 common.

---

### Post by Monicker on 2008-05-10
> **ucal said:**
> Really?  I've just been bumping it whenever it hits the second page, because in my experience, no one ever looks there.  I'll tone it down though if its a problem.

You should wait at least 24 hour before doing a bump.  Some of us actually do look beyond the first page.  I actually make a habit of searching for posts that have had no replies at all since my last visit to the forum.

---

### Post by ucal on 2008-05-11
Daily bump then.

---

### Post by ucal on 2008-05-12
Bump for the rest of the day.  There is good new though:  I think I fixed my wireless connection, so its almost as fast as vista (which is good enough for me), so as of right now this is the only thing keeping me from leaving vista a novelty on my computer.  Unless of course my wireless craps out again, but my fingers are crossed.

---

### Post by ucal on 2008-05-13
bump?

---

### Post by OldTimeTech on 2008-05-13
Run a search in Synaptic package manager....search for pyQT and then read the synopsis on the right side, don't need to load dev or debug...but anything else that doesn't sound to far away from what the error was asking for and try again.

---

### Post by ucal on 2008-05-13
No good.  Thanks though.

---

### Post by ucal on 2008-05-15
bump.

---

### Post by Monicker on 2008-05-15
You might want to consider contacting the author of the script, and seeing what he has to say about it.

[http://www.kde-apps.org/content/show.php/weekalarm?content=23160]("http://www.kde-apps.org/content/show.php/weekalarm?content=23160")

---

### Post by ucal on 2008-05-17
I'll try that out then.

---

### Post by F i L on 2008-07-06
Hi. I had the same problem.
Well i downloaded theese packages and the problem dissapeared:
memaid-pyqt
pyqt4-dev-tools
pyqt-tools

I Hope i helped ;)

Also at weekalarm abouts it says:

Dependencies:
Amarok 1.2 
Python 2.4 
PyQt Bindings

---

