---
title: "moving home directory to doc or un pinning it from desktop"
date: 2023-06-26
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2023-06-26
I'm using ubuntu 23.04. The Home directory is on the desktop. Some times when I open a program it is shown in the program screen which is annoying. Can you  move to the dock or place it somewhere else? Are there ways to use a command in the terminal do that/ Thx for help.

---

### Post by tuesdaybarrett on 2023-06-26
I tried this and this in the terminal with this the result
 gsettings set org.gnome.shell.extensions.desktop-icons show-home false
No such schema &#8220;org.gnome.shell.extensions.desktop-icons&#8221;

---

### Post by tuesdaybarrett on 2023-06-26
Found solution. Went to settings then opened Ubuntu desktop.Then moved bar on show personal folder to off. Now it is gone.

---

### Post by TheFu on 2023-06-26
Please mark the thread **SOLVED** using the _thread tools button_ so the community can find your solution and people looking to help don't bother for already solved problems.

---

### Post by MAFoElffen on 2023-06-27
Adding that in the previous post, you probably got an error saying that schema did not exist. Try this to see your current value:
```

gsettings get org.gnome.shell.extensions.ding show-home

```
The default is true

---

### Post by #&amp;thj^% on 2023-06-29
Kind of a late reply but MAFoElffen code will show the current setting ie:
```
 gsettings get org.gnome.shell.extensions.ding show-home
true

```
And this will disable it:
```
 gsettings set org.gnome.shell.extensions.ding show-home false
```
Differences  are "get and set".
```
gsettings get org.gnome.shell.extensions.ding show-home
false

```
Hope this is useful to others as well.

---

