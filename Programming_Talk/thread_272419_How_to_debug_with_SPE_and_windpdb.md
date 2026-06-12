---
title: "How to debug with SPE and windpdb"
date: 2006-10-06
forum: Programming Talk
---

### Post by honda on 2006-10-06
Hello, python programmers!

I'm fairly new to linux and very new to python. I thought SPE would be a good place to start, but I almost went nuts trying to use the debugger. Finally I managed to debug a script (with winpdb) by starting the script like this:

import sys
sys.path.append("/usr/lib/python2.4/site-packages/_spe/plugins/winpdb")
import rpdb2
rpdb2.start_embedded_debugger("12345")
print "hello"

.. and starting the script with 'Run' and using 'Attach' in WinPdb with password manually set to '12345'. 

This works, but surely there must be a better way. Shouldn't I be able to just press the 'debug with winpdb' button and it would just load the script and stop on the first row? If I do, WinPdb just says :"*** Debugee failed to start in a timely manner."

So, how do you debug your python scripts?

---

### Post by honda on 2006-10-09
Seems that noone here ever had to debug a python program. Python must be even better than I thought... 
Please, tell me what you are using do debug python and how. Anybody using WinPdb with Stani's python editor? If so how? If not why?

---

### Post by zan0416 on 2006-10-12
I am also interested in why we are getting the "Bebugee failed to start in a timely manner" message, anyone out there to shed some light on the subject for us?  Thanks!

---

### Post by stani on 2006-11-01
You should contact Nir Aides, the author of winpdb, about this or look at the winpdb website. If you want to use the debugger, start winpdb with python2.3 which will work fine.

---

### Post by stani on 2007-02-24
I am happy to say that this issue is fixed! Debugging in Ubuntu is again possible and it works great. The new version of SPE hit already the subversion repository, so expect a release in the near future. Follow the development of SPE on this blog:

[http://pythonide.stani.be](http://pythonide.stani.be)

Stani

---

### Post by siman on 2007-07-31
debugging with winpdb + spe is a revelation!

---

### Post by stani on 2007-08-02
Thanks!

---

### Post by maximilion on 2008-02-18
Yep, the latest version works great!

Note that you don't get the latest version via apt-get or Synaptic on Ubuntu Gutsy.

btw, did you know the .py is a lie? :D

---

### Post by stani on 2008-02-18
> **maximilion said:**
> Yep, the latest version works great!

Note that you don't get the latest version via apt-get or Synaptic on Ubuntu Gutsy.
No, but you will get on Hardy. If you like SPE, I would recommend you to always use SPE from subversion.
> 

btw, did you know the .py is a lie? :D
Can you explain?

---

### Post by siman on 2008-02-19
> 
btw, did you know the .py is a lie? 

Probably not, [http://youtube.com/watch?v=LxYfMRtun5w](http://youtube.com/watch?v=LxYfMRtun5w)

---

