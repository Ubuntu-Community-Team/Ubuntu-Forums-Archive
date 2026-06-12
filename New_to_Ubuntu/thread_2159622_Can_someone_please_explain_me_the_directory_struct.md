---
title: "Can someone please explain me the directory structure and user hierarchy"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by enduser79 on 2013-07-03
I got Ubuntu 12.04 installed from 10.04 and things are going well.  I figured out how to share files with my Windows terminal, how to install software etc.

I'm just curious about the user hierarchy....I understand ***root*** is the highest.

When I installed 12.04, I chose ***bob*** as my username. bob is an Administrator, is admin under root privilege wise?

---

### Post by VMC on 2013-07-03
Something like this view:
[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

Also here is some [more views]("https://www.google.com/search?q=linux+directory+structure&sa=X&tbm=isch&tbo=u&source=univ&ei=ndLUUZruH6GIiwKrr4CYDA&ved=0CD0QsAQ&biw=1255&bih=797#facrc=_&imgdii=_&imgrc=ie2d2T_l2xXxxM%3A%3BHDbR4bozNUFDpM%3Bhttp%253A%252F%252Fhealpix.jpl.nasa.gov%252Fhtml%252Fdir_tree.png%3Bhttp%253A%252F%252Fhealpix.jpl.nasa.gov%252Fhtml%252Finstall.htm%3B562%3B478"). Just click on anyone and it will take you to the web page for further explanation:

---

### Post by oldos2er on 2013-07-03
Also ```
man hier
``` and [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

### Post by grahammechanical on 2013-07-03
Bob might be listed as Administrator but he is using the OS as a standard user until he needs to authenticate an administrative task. Then he puts in his password and for the duration of the task Bob has become the administrator. when the task ends Bob reverts back automatically to being a standard user. What is wise is Ubuntu use of sudo and not root.

This explains it

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards.

---

