---
title: "[SOLVED] .conkyrc dissapeared?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by rideburton56 on 2008-11-09
Hello all,

Just a quick question, I spent my Saturday devoted to set up my own conky.  After many quick edits in gedit, saving, and reloading conky in the terminal, I did a restart just to be safe.  Conky works great, everything is good to go, but it seems that my .conkyrc file has left my home folder.  Where oh where did it go???

Quick Edit:  When I load conky it is using the custom config i set up, so its still out there somewhere!

---

### Post by th89 on 2008-11-09
The period before the file simply means it is a hidden file. Just open up Nautilus, and go to the folder you saved it in. Click the view on the main toolbar, and look for the "show hidden files." You should be able to see it. Hope this helps!

---

### Post by taurus on 2008-11-09
```
ls -la ~/.conkyrc
```

---

### Post by stoogiebuncho on 2008-11-09
Ctrl + H will also show you all the hidden files (when in nautilus, of course)

---

### Post by m_l17 on 2008-11-10
Once you find it make a backup. Change to your home dir and:

```
$ cp .conkyrc [COLOR="Red"]~/Documents/conkyrc[/COLOR]
```

or 

```
$ cp .conkyrc [COLOR="Red"]~/Documents/conkyrc.txt[/COLOR]
```

You can change the path where you want to save it[the red text].

---

### Post by rideburton56 on 2008-11-10
Ahh, i still very much belong in the beginner forum.. Thanks everyone!

---

