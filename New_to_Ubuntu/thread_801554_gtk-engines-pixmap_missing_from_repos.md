---
title: "gtk-engines-pixmap missing from repos"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by kevCast on 2008-05-20
I can't find this package anywhere. What happened to it?

---

### Post by EXCiD3 on 2008-05-20
Do you have universe and/or multiverse repositories enabled? It shows that its available for hardy: [https://launchpad.net/ubuntu/hardy/+package/gtk-engines-pixmap](https://launchpad.net/ubuntu/hardy/+package/gtk-engines-pixmap)

---

### Post by kevCast on 2008-05-20
No, I've got nothing.

Here's a shot.

---

### Post by y-lee on 2008-05-20
Be sure [Universe is enable]("https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096")

```
 sudo apt-get install  gtk-engines-pixmap
```


Edit I think that link is a bit dated but ya get the idea, note repos can be added in synaptic.

---

### Post by EXCiD3 on 2008-05-20
System > Administration > Software sources and check the boxes to enable the universe and multiverse repositories. Then reload the package list and you should  be able to download it.

---

### Post by kevCast on 2008-05-21
I've unchecked and checked again all the sources, the reloaded. The search is still showing the same thing. Is it anyone else's repos?

---

### Post by EXCiD3 on 2008-05-21
A quick search on [http://packages.ubuntu.com](http://packages.ubuntu.com) shows that it **isn't **available for hardy: [http://packages.ubuntu.com/search?keywords=gtk-engines-pixmap&searchon=names&suite=hardy&section=all](http://packages.ubuntu.com/search?keywords=gtk-engines-pixmap&searchon=names&suite=hardy&section=all)

On launchpad.net it shows that the package has been superseded, or replaced in normal terms. What are you trying to install? Nothing for hardy should require that package unless what you are trying to install is quite outdated.

---

### Post by kevCast on 2008-05-21
I'm trying to install a theme.

---

### Post by alvareznelson on 2008-10-01
Same problem here! I'm trying to install a theme that requires pixmap, but it's not available for Hardy. And it's a new theme, not outdated. What could be done? I tried to install the gtk-engines-pixmap package for Gutsy, but it didn't install. :(

---

### Post by kerry_s on 2008-10-01
gtk-engines-pixmap is for gtk 1.2, most everything is now gtk2, so gtk 1.2 programs are slowly being dropped as there not developed any more.

if your theme requires it,  then it is a very old theme and most likely will not function correctly in gtk2.

---

### Post by OrangeVixen on 2009-10-14
> **kerry_s said:**
> gtk-engines-pixmap is for gtk 1.2, most everything is now gtk2, so gtk 1.2 programs are slowly being dropped as there not developed any more.

if your theme requires it,  then it is a very old theme and most likely will not function correctly in gtk2.

Well there are a **lot** of gtk 1.2 apps still out there and being used, gtk-engines-pixmap should still be around.

Incidentally, gtk-engines-pixmap is not available for Ubuntu 9.04 Jaunty either.

---

