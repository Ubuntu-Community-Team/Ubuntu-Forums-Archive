---
title: "Padman!"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by kattman on 2008-07-09
This is the first Game That Im trying to install !  No mater whit I try I keep geting a "write premission error"  How Can I stop are gang access to the folders!!!!!

---

### Post by cariboo on 2008-07-09
Install your game using sudo if you are using a terminal, of gksu if you are using a gui eg:

```
sudo ./<game install>
```

Where <game install> is the game installer file. Or:

```
gksu natilus
```

and double click on the file in the window that opens.

Jim

---

### Post by tjwoosta on 2008-07-09
you gotta use sudo

**s**uper **u**ser **do**

(gives you temporary administrator privleges)


or if you need admin privleges for a graphical program use gksudo

---

