---
title: "glib!!"
date: 2005-02-02
forum: Repositories &amp; Backports
---

### Post by paradox on 2005-02-02
Hi!

I need download glib for C routines. apt-get install glib don't found it. My source_list is:

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main


Where I can found this libs?

---

### Post by mendicant on 2005-02-02
You should have done a search in your favorite front end--aptitude or synaptic.  You would have seen that any number of glib packages are available.  You probably want libglib2.0-dev or libglib1.2-dev.

---

### Post by paradox on 2005-02-02
Humm...is strange, because libglib is already installed but a application don't found glib-gettextize...glib-gettextize isn't in my system of course...

---

### Post by paradox on 2005-02-02
yes needed dev packages :D TNX!

---

