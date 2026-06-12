---
title: "ubuntu server 12.04"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by crashdogy on 2012-05-20
question how do you make changes to system files the save button is blacked out

---

### Post by HiImTye on 2012-05-20
you need to open your editor with either sudo (command line programs) or gksudo (graphical programs), i.e.
```
gksudo gedit
gksudo gvim
sudo nano
sudo vi
```
etc..

make sure you know what you are doing as making the *wrong* changes can damage your system

also, make sure to use gksudo for graphical programs or you could change the permissions on your users' files

---

### Post by crashdogy on 2012-05-20
thats just it can change premissions on the files all greyed out
 
i'm in su mode and tryed gedit but will not let me save or replace files

---

