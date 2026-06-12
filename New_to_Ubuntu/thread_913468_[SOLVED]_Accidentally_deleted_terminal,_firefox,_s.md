---
title: "[SOLVED] Accidentally deleted terminal, firefox, synaptic manager, add/remove"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Zigon on 2008-09-07
I was trying to remove something I'd just installed from the syn manager. Anyways, I removed what I installed but I remembered it installing a lot more. I looked through the list and removed things at random that I thought it installed :eek:. Is there a way I can recover this without re-installing Ubuntu? [-o< I can't use the terminal, a web browser, or install anything.

---

### Post by ByteJuggler on 2008-09-07
Press ctrl-alt-f1, then log in.  Then try:

```
sudo apt-get install ubuntu-desktop
```

Then
```
sudo apt-get -f 
```

I think that should reinstall everything in the ubuntu-desktop and fix any broken dependencies, including terminal/firefox etc.

Press alt-f7 to get back to your GUI desktop.

---

### Post by sisco311 on 2008-09-07
Press Alt+F2 and type:
```
xterm
```
to start a terminal.

reinstall the default applications with:
```
sudo aptitude install ubuntu-desktop
```


If you removed xterm, then press Ctrl+Alt+F1, log in and
reinstall the ubuntu-desktop package from the virtual terminal.

---

### Post by stevoo on 2008-09-07
I think that should have solved your problem. 

DOnt forget to mark it as solved !

---

### Post by Zigon on 2008-09-08
Alright, thanks a lot guys. Theres a few of my apps that didn't get fixed but ill just reinstall.

---

