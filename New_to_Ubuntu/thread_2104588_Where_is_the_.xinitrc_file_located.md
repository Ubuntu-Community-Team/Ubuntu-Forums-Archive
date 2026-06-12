---
title: "Where is the .xinitrc file located?"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2013-01-13
Hey!

I'm currently trying to edit the .xinitrc file to edit it so awesome can be executed. What is the route to the file? or where can it be found?

Thanks

---

### Post by audiomick on 2013-01-13
According to this
[http://manpages.ubuntu.com/manpages/hardy/man1/xinit.1.html]("http://manpages.ubuntu.com/manpages/hardy/man1/xinit.1.html")

it should be in your home directory, if it exists. It  is a hidden file, so you will need to "show hidden files" to see it. I'm not sure how that works on kbuntu, but have a look in the "view" menu of the file manager, if there is one. That is where it is on this 10.04 install.

---

### Post by Tibuda on 2013-01-13
do you use a graphical login manager (KDM?)? Maybe I'm wrong, but I think it only works when you use startx.

---

### Post by kabukiM0n0 on 2013-01-13
> **audiomick said:**
> According to this
[http://manpages.ubuntu.com/manpages/hardy/man1/xinit.1.html]("http://manpages.ubuntu.com/manpages/hardy/man1/xinit.1.html")

it should be in your home directory, if it exists. It  is a hidden file, so you will need to "show hidden files" to see it. I'm not sure how that works on kbuntu, but have a look in the "view" menu of the file manager, if there is one. That is where it is on this 10.04 install.

> **Tibuda said:**
> do you use a graphical login manager (KDM?)? Maybe I'm wrong, but I think it only works when you use startx.

It was my mistake actually, the guide I was reading was for KDE 3 and as such was putting the awesome.desktop into the wrong folder, that's why nothing worked. 
Works fine now.

startx still doesn't work, but by going into system settings> Default applications> windows manager. Works just fine

Thanks anyway.

---

