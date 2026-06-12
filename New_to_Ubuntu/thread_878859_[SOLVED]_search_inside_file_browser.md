---
title: "[SOLVED] search inside file browser"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by stoppage on 2008-08-03
Am I corrrect in assuming that the „Search“ function in Ubuntu's file browser doesn't work?

---

### Post by ConMan318 on 2008-08-03
Um, no you are not.  Maybe you should post why you think it doesn't work so we can try to solve your problem.

---

### Post by stoppage on 2008-08-03
A search for mplayer inside / file browser yields no results

---

### Post by ConMan318 on 2008-08-03
Are you sure that mplayer is installed?  Mine yields 38 results for mplayer in filesystem.

---

### Post by stoppage on 2008-08-04
Mplayer is my player of choice.

---

### Post by SunnyRabbiera on 2008-08-04
It depends on where you search from, are you searching the file system as your location?
You cant search for mplayer if you are in your home directory.

---

### Post by stoppage on 2008-08-05
Searching filesystem

---

### Post by SunnyRabbiera on 2008-08-05
hmm, well that is odd...
It should have detected it.

---

### Post by billgoldberg on 2008-08-05
The nautilus not find anything bug has been fixed a few updates ago.

Are you fully updated?

```
sudo apt-get install update
```

```
sudo apt-get install upgrade
```

---

### Post by stoppage on 2008-08-05
I have 7.04 Feisty fully updated

---

### Post by stoppage on 2008-08-12
Issue solved by installing "Beagle"

---

