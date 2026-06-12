---
title: "ERROR: #2: Cannot load class 'Project':"
date: 2008-10-06
forum: Programming Talk
---

### Post by ratmandall on 2008-10-06
I have tried installing gambas2 and I keep getting this error message.
```
ERROR: #2: Cannot load class 'Project': Unable to load class file

```
I read in another thread that the folder it was trying to read didn't have the right permission's and to try this
```
sudo chmod -R o+w /usr/share/gambas2/examples
```
And that didn't work:confused:

---

### Post by ratmandall on 2008-10-07
Anyone?

---

### Post by Zugzwang on 2008-10-07
Did you try google?

[http://www.nabble.com/Unable-to-load-class-file-td14807758.html]("http://www.nabble.com/Unable-to-load-class-file-td14807758.html")

> 
That means that you must compile the project first! To do that,
run 'gbc3 -agt' inside the project directory. 


---

### Post by ratmandall on 2008-10-07
> **Zugzwang said:**
> Did you try google?

[http://www.nabble.com/Unable-to-load-class-file-td14807758.html]("http://www.nabble.com/Unable-to-load-class-file-td14807758.html")

Yea, well that didn't work so I completely removed it and decided to compile and install it again, and when I did ```
sudo ./configure -C
```
It compiled
```

THESE COMPONENTS ARE DISABLED:

- gb.corba
- gb.db.firebird
- gb.db.odbc
- gb.db.postgresql
- gb.db.sqlite2
- gb.db.sqlite3
- gb.desktop
- gb.gtk
- gb.gtk.svg
- gb.net.curl
- gb.net.smtp
- gb.opengl
- gb.pcre
- gb.pdf
- gb.qt
- gb.qt.kde
- gb.qte
- gb.sdl
- gb.sdl.sound
- gb.v4l
- gb.xml

```

EDIT: Never mind figured out how to enable them.

---

### Post by dannet on 2008-10-09
You can check the options of configure

```
./configure -help
```

For example

```
./configure --enable-bzlib2
```

---

### Post by rohitfeb14 on 2009-06-07
The very same is troubling me..
Tried building from source as well as installing from repos. 
Has anyone got a successful install???

---

