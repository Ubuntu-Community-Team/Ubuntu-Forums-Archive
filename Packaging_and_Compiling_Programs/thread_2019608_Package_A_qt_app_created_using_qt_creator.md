---
title: "Package A qt app created using qt creator"
date: 2012-07-07
forum: Packaging and Compiling Programs
---

### Post by superprash2003 on 2012-07-07
Hi everyone,
     I just created a small qt app using qt creator. This app also has certain shell scripts in a folder which are called from the qt app. I was trying to create a debian package for it and even later create a PPA for it. I tried this tool called debreate to create the debian package but i got quite a few errors. 
     I was expecting this process to be simple , maybe im not doing it right. Would really appreciate some help.
Thanks,
Prashanth

---

### Post by superprash2003 on 2012-07-07
some of the errors i got are : 

E: dropboxnotifier: binary-from-other-architecture ./opt/main.o
E: dropboxnotifier: binary-from-other-architecture ./opt/mainwindow.o
E: dropboxnotifier: binary-from-other-architecture ./opt/moc_mainwindow.o
E: dropboxnotifier: binary-from-other-architecture ./opt/test2
E: dropboxnotifier: unstripped-binary-or-object ./opt/test2
E: dropboxnotifier: missing-dependency-on-libc needed by ./opt/test2

---

### Post by superprash2003 on 2012-07-08
would really appreciate some help :)

---

### Post by SevenMachines on 2012-07-10
Automatic package building never seemed to take off, you tended to be quicker and safer to learn how to package anyway. I dont know how much current work goes into them these days but if you want to make a package then the packaging guide and a bit of work and head scratching is still the way I'd recommend.
Anyway, the home of all lintian error explanations and first port of call
[http://lintian.debian.org/tags.html](http://lintian.debian.org/tags.html)

I'd need to see what kind of packaging you'd ended up with, you can upload broken source packaging to a ppa too :)

You can now upload binary blobs to ubuntu's appcentre thingy if you'd prefer to skip packaging altogether, I've no idea how but I believe the process starts here
[http://developer.ubuntu.com/](http://developer.ubuntu.com/)

---

### Post by superprash2003 on 2012-07-11
thanks a lot for your reply..will surely check those links out..

---

