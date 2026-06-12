---
title: "desktop not loading up"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by publicladykilla on 2013-03-05
I have ubuntu and i finally updated via command line and everytime I do startx all that comes up is the backgroud .

---

### Post by Mark_in_Hollywood on 2013-03-06
try:

sudo apt-get update

you will see many lines of terminal output

and then

sudo update-grub2

if you are using grub2, which you should be.

sudo update-grub

if you have an older grub

---

### Post by Mark Phelps on 2013-03-07
What version of Ubuntu are you running?

IF it's 12.04 or 12.10, do you see a column of icons on the left side of the desktop?  Or, do you see the desktop wallpaper and nothing else?

---

