---
title: "Open up a folder?"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by thelildrummabot on 2013-04-05
How do I open up a folder in the terminal that is in my downloads called "multicd"?

---

### Post by savi3000 on 2013-04-05
cd /path/to/folder

---

### Post by thelildrummabot on 2013-04-05
do I include /username/home/download?

---

### Post by thelildrummabot on 2013-04-05
I get no such directory

---

### Post by savi3000 on 2013-04-05
When you open up terminal, you're likely in "~", which is the same thing as /home/*yourusername*. Assuming the folder you want in in ~/Downloads/multicd, You can just do *cd ~/Downloads/multicd*, or if you are in ~, cd Downloads/multicd.

Whichever works for you

---

### Post by savi3000 on 2013-04-05
Also, here's a probably helpful resource for you: [http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)

---

