---
title: "[SOLVED] Good file manager?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Markstar on 2008-10-20
Hi,
I am new to Ubuntu and I'm looking for a good file manager. I started with Norton Commander in DOS 5 and eventually ended up with [xplorer2]("http://www.zabkat.com/") in Windows which is imho far superior to any other application of that category (like Total Commander).

Anyways, now I'm looking for a similar program in Linux and hope you can recommend me a suitable alternative. Something like NC would be a start, but I really do hope to find something that also has a tree-view as a third window so that I can easily jump between folders (I do a lot of file-copying, moving, etc). 

Thanks in advance, I am anxious to try out your suggestions!

Kind regards
  Markstar

---

### Post by jyaan on 2008-10-20
midnight commander? if youre looking for an old school console fm that would be the one.

---

### Post by jyaan on 2008-10-20
oh its called 'mc' in the repos btw

---

### Post by Markstar on 2008-10-20
> **jyaan said:**
> midnight commander? if youre looking for an old school console fm that would be the one.Thank you, jyaan! I installed both MC and the Gnome Commander, which on first glace seems to be the superior program. 

However, I am hoping to find a file manager that also has a tree view so I can jump between folder much faster (bookmarks are only of limited use and constantly moving up and down several levels is really annoying over time). 

xplorer2 even had the possibility to have several tabs per pane, which means I could use bookmarks, the tree or the tabs (I usually have 4 tabs on either pane => 8 folders on my fingertip at any given moment).

---

### Post by a0u on 2008-10-20
> **Markstar said:**
> Thank you, jyaan! I installed both MC and the Gnome Commander, which on first glace seems to be the superior program. 

However, I am hoping to find a file manager that also has a tree view so I can jump between folder much faster (bookmarks are only of limited use and constantly moving up and down several levels is really annoying over time). 


Check with the documentation; it seems Midnight Commander does have a tree view option.
Quoted from the [manual]("http://www.chm.tu-dresden.de/edv/mc/mc4.5/manual1.html"):
> The Directory Tree command shows a tree figure of the directories. You can select a directory from the figure and the Midnight Commander will change to that directory. 
There are two ways to invoke the tree. The real directory tree command is available from Commands menu. The other way is to select tree view from the Left or Right menu. 
To get rid of long delays the Midnight Commander creates the tree figure by scanning only a small subset of all the directories. If the directory which you want to see is missing, move to its parent directory and press C-r (or F2). 


Admittedly, I have never used MC, so I can't say whether it has the third pane you are looking for.

---

### Post by kerry_s on 2008-10-20
xfe it can do all the views, all at once or what ever you want.

sudo apt-get install xfe

pics:
[http://roland65.free.fr/xfe/index.php?page=screenshots](http://roland65.free.fr/xfe/index.php?page=screenshots)

---

### Post by Markstar on 2008-10-21
> **kerry_s said:**
> xfe it can do all the views, all at once or what ever you want.

sudo apt-get install xfe

pics:
[http://roland65.free.fr/xfe/index.php?page=screenshots](http://roland65.free.fr/xfe/index.php?page=screenshots)
[SIZE="5"]Awesome!!![/SIZE]

Thank you!!!! This is pretty much exactly what I have been looking for. Even though it has fewer options than xplorer2 and I have noticed (in all file managers under Ubuntu) that the lines are bigger in detailed mode, it should still be good enough for now. :guitar:

Thanks again!

Cheers
  Markstar

---

### Post by steveneddy on 2008-10-31
Another alternative would be Thunar.

I believe that it has a tree view.

---

