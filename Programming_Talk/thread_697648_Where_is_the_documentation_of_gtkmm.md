---
title: "Where is the documentation of gtkmm?"
date: 2008-02-15
forum: Programming Talk
---

### Post by Zdravko on 2008-02-15
I downloaded gtkmm, but don't know where the documentation is located. Any ideas?

---

### Post by hod139 on 2008-02-15
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/](http://www.gtkmm.org/docs/gtkmm-2.4/docs/)

If you really want it local, you have to install the package libgtkmm-2.4-doc

---

### Post by Zdravko on 2008-02-15
I installed it and that is why I am asking.

---

### Post by hod139 on 2008-02-15
usr/share/doc/libgtkmm-2.4-doc/

---

### Post by Zdravko on 2008-02-15
Couldn't find "/usr/share/doc/libgtkmm-2.4-doc".

Fedora here.

---

### Post by Zdravko on 2008-02-16
Bump!

---

### Post by dmendizabal on 2008-07-08
You need to use Devhelp to read the documentation.

install: Devhelp from the repository and you will find the documentation already there when you open it.

---

### Post by haTem on 2008-07-08
On fedora it's located at "/usr/share/gtk-doc/html/gtkmm-2.4/".

As dmendizabal said though, you should try devhelp. It's a useful tool that will make it easier to search and navigate the documentation.

---

### Post by geenux on 2008-08-07
If you use the package manager to install the doc, go into synatic, search the paquet name (gtkmm-2.4-doc), then right clic and see package informations. There is a file tab which contains all the files installed.
The path of doc is /usr/share/doc/libgtkmm-2.4-doc

Thanks for devhelp, very usefull

---

