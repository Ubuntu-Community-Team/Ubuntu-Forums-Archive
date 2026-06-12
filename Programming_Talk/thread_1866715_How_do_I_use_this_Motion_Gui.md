---
title: "How do I use this Motion Gui"
date: 2011-10-21
forum: Programming Talk
---

### Post by esc1 on 2011-10-21
Here is a [link]("http://sourceforge.net/projects/motiongui/") to the project on source forge. The tar.gz file doesn't have a makefile.. might be able to use it if that was there, but I'm a total newb. Sorry if this isn't really the right section for the post as well. Appreciate the help. Already have motion installed of course Thanks.

---

### Post by esc1 on 2011-10-22
Bump

---

### Post by esc1 on 2011-11-06
Anybody?

---

### Post by rockorequin on 2012-01-14
In case you were still wondering... it's a qt project, so you can load and build it with qtcreator (sudo apt-get install qtcreator). I needed to install libqtwebkit-dev as well to get it to build properly, and I had to configure the build directory (in the Projects tab) because when I opened the project (motion-Gui.pro) the qtcreator configured the default build directory to one that didn't exist.

---

### Post by SevenMachines on 2012-01-15
```
$qmake ./
$make
$./Motion-Gui
```would also work

---

