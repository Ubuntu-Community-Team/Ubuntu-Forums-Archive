---
title: "what is the vnc running in background"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by aradaj on 2008-11-14
I was looking at the running processes running in the background. I found VNC running on a default install for both ubuntu and xubuntu.

Running the command on any version of ubuntu and xubuntu
```
ps aux | grep vnc
```

I get the output:
```
user       16648  0.0  0.0   5164   832 pts/1    R+   22:25   0:00 grep vnc

```

Does anybody know what kind of vnc is running and why is it running?

---

### Post by jamesrl on 2008-11-14
you don't have vnc running.  What you are seeing is your search for 'grep vnc'.   E.g., try searching for DUFHASIFJHASPIFJASFPOASJFASF with
```
ps aux | grep DUFHASIFJHASPIFJASFPOASJFASF
username   9143  0.0  0.0   7452   900 pts/1    S+   01:47   0:00 grep DUFHASIFJHASPIFJASFPOASJFASF

```
I guess if you don't want that to show up you could do something like:
```
ps aux | grep bash | grep -v grep
```
(e.g. list all processes, and only show lines with the output having the word bash in them, and then suppress all of those lines that have the word grep in them).

---

### Post by aradaj on 2008-11-14
OOOOHHH!!! I did not see the grep before the vnc on the running app. Thank you!

---

