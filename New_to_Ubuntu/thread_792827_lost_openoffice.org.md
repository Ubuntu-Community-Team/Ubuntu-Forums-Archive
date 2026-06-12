---
title: "lost openoffice.org"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by bradleyporter on 2008-05-13
I have recently converted to Ubuntu so am experiencing what I hope are the usual teething problems. open office was working fine until I need to open a .pub file. this meant downloading Scibus. However I then found I couldn't open any of the other open office applications. I tried re-installing it from the synaptic package manager and later downloading it from the site - to no avail.I have since tried going to the terminal and loading the following...mv .openoffice.org2/ old.openoffice.org...which didn't work either. Any suggestions?

---

### Post by spydon on 2008-05-13
You could try:
```
sudo apt-get remove --purge openoffice.org
```
and then:
```
sudo apt-get install openoffice.org
```

---

### Post by SlappyPappy on 2008-05-13
Just curious if you downloaded via Synaptic or from their website?

Hope you get this fixed for yourself... Good luck.

---

