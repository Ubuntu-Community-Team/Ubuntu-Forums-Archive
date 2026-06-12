---
title: "Where to put application data (databases and other files)"
date: 2008-10-18
forum: Programming Talk
---

### Post by keeler1 on 2008-10-18
Where is the standard place to put application data in linux.  I am writing a program in python that will us a sqlite3 database.  I am going to need to write and read to this database.

Where should it be put upon installation so that the program can read to and write from the database.

Also if anyone knows of the same place to put it under windows and mac that would also be good information.

---

### Post by sokopok on 2008-10-18
Some interesting (?) reading materials:
[FHS Filesystem Hierarchy]("http://www.pathname.com/fhs/pub/fhs-2.3.html")
[XDG Filesystem Hierarchy]("http://techbase.kde.org/KDE_System_Administration/XDG_Filesystem_Hierarchy")

---

### Post by snova on 2008-10-18
I think it depends on whether you have to change it, or whether it's static installation data.

In the former case, you would create it in /var somewhere, but I don't think you can install data to that location.

For that latter, somewhere in /usr/share.

It might be different for other distros.

---

### Post by Can+~ on 2008-10-18
> **keeler1 said:**
> Where is the standard place to put application data in linux.  I am writing a program in python that will us a sqlite3 database.  I am going to need to write and read to this database.

Where should it be put upon installation so that the program can read to and write from the database.

Also if anyone knows of the same place to put it under windows and mac that would also be good information.

Depends:
-User information: (example: a playlist, his file), let them choose, depends if the data is meant to be portable (like a .odf).
-Raw user information: Interal information of your program is usually stored in the subfolders. (example ./myapp/data)
-Configuration settings: Usually stored inside /home/<user>/<.yourapp> or /usr/share/
-Temporary: /tmp/ duh.

---

### Post by keeler1 on 2008-10-18
I need to store alterable application information.  However the users of the programs should never have to alter it themselves.

Also Is there a good place to put all of the application itself.  I am writing the application in python.  Therefore it is all in scripts.  Is there a directory where I could put all of my application, custom libraries and everything?

---

### Post by keeler1 on 2008-10-18
If I were to put my application data into /var how would I have read and write access to it?  It normally requires root access doesnt it?

---

### Post by snova on 2008-10-18
Oops... If you have to read and write it I think it has to be in the user's home directory. /var is more for things like database servers (which run as root), I think.

---

