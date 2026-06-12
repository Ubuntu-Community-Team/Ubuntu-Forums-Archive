---
title: "Screen recording question"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by pqwoerituytrueiwoq on 2013-04-07
is there a program that can show what mouse clicks i make and what keys are pressed, like a on screen keyboard and mouse that will have there keys flash blue when i press a key/button?

i record using kazam

---

### Post by deadflowr on 2013-04-07
What about something like keymon?

---

### Post by pqwoerituytrueiwoq on 2013-04-07
using raring 13.04 xubuntu
```
test@M4A79XTD-EVO:~$ sudo dpkg-reconfigure keymon
test@M4A79XTD-EVO:~$ key-mon
The program 'key-mon' is currently not installed. You can install it by typing:
sudo apt-get install keymon
test@M4A79XTD-EVO:~$ sudo apt-get install keymon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
keymon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
test@M4A79XTD-EVO:~$ key-mon
The program 'key-mon' is currently not installed. You can install it by typing:
sudo apt-get install keymon
test@M4A79XTD-EVO:~$
```

edit made a bug report
[https://bugs.launchpad.net/ubuntu/+source/key-mon/+bug/1165875](https://bugs.launchpad.net/ubuntu/+source/key-mon/+bug/1165875)

edit:
got it from here and it works great :)
[http://code.google.com/p/key-mon/downloads/detail?name=key-mon-1.16.zip](http://code.google.com/p/key-mon/downloads/detail?name=key-mon-1.16.zip)

---

### Post by deadflowr on 2013-04-07
Nevermind my earlier post, keymon doesn't do what you'd want.
It does show the mouse clicks, but lt show the keys being pressed textually.(example, press enter and the word enter pops up)
It doesn't have a keyboard layed out that responds to the buttons being pressed.

---

### Post by pqwoerituytrueiwoq on 2013-04-07
it is good enough to show keyboard shortcuts like ctrl+h in the file manager, that is really the main point
that is probally better than a full layout since it saves screen space, i marked the thread as solved

---

