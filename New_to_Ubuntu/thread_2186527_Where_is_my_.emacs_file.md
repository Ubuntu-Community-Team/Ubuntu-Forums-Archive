---
title: "Where is my .emacs file?"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by zeynel2 on 2013-11-07
I used the instructions here [http://www.braveclojure.com/basic-emacs/#2__Configuration](http://www.braveclojure.com/basic-emacs/#2__Configuration) to use Clojure mode in emacs but I cannot find my .emacs file (I think it is deleted) Do I need to create a new .emacs file? If not where do I put my preferences?

---

### Post by PaulW2U on 2013-11-08
> **zeynel2 said:**
> I used the instructions here [http://www.braveclojure.com/basic-emacs/#2__Configuration](http://www.braveclojure.com/basic-emacs/#2__Configuration) to use Clojure mode in emacs but I cannot find my .emacs file (I think it is deleted) Do I need to create a new .emacs file? If not where do I put my preferences?

By default your .emacs file will be created in your home directory. Because its name starts with a dot or period it will be hidden from file managers that have not been set to show hidden files. Ctrl+H or similar might be needed to display them. Do you see other files or directories that start with a dot? Unless you have specifically deleted your .emacs file I'm sure it will still be there.

I'm not too sure what the Clojure mode is and why you want to use it but preferences can usually be set from within emacs without need to manually edit the .emacs file although some times it might be easier that way. :D

---

### Post by Nr90 on 2013-11-08
or in terminal:
cd ~
ls -A

---

