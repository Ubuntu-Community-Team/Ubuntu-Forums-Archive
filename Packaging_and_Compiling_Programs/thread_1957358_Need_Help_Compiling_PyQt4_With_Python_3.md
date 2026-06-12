---
title: "Need Help Compiling PyQt4 With Python 3"
date: 2012-04-12
forum: Packaging and Compiling Programs
---

### Post by dniMretsaM on 2012-04-12
I first attempted to use PyQt4 with Python 3 and got an error about missing modules. So I went digging and found that you need Qt 4.7 or higher (I wos using 4.6.x). So I downloaded the latest Qt (4.8.1) and compiled it. It installed to /usr/local/Trolltech/Qt-4.8.1/. I then attempted to compile sip and PyQt4 with the commands
```
python3 configure.py
make
sudo make install
```Sip installs fine, but PyQt doesn't configure. I get this error message:
```
sip: QDBusPendingCall has not been defined
```So how can I get this to work? If at all possible, I would *really* like to avoid recompiling Qt. It took well over 12 hours. But I will do it if it's necessary.

Note that this is on a Crunchbang 10 "Statler" with backports. However, since #! and Ubuntu are very similar, I thought I might be able to get some help without having to join yet another forum.

---

### Post by dniMretsaM on 2012-04-16
Bump. Any help?

---

### Post by SevenMachines on 2012-04-16
I'd guess that its because you're installing your local qt version to /usr/local/Trolltech/Qt-4.8.1/ but then just calling the default configure python3 configure.py. In other words, the configure will use the system version of qmake, and so qt4, rather than the new version you want it to.
Try first finding the path of the new 4.8 version of qmake with
```
$ find /usr/local/Trolltech -name 'qmake'
```then send this path as a parameter to configure
```
$ python3 configure.py -q /usr/local/Trolltech/something/qmake
```In this case I imagine the combined effort would probably work too
```
$ python3 configure.py -q ` find /usr/local/Trolltech -name 'qmake' `
```

---

### Post by dniMretsaM on 2012-04-16
Thanks, testing it out now. Will report back.

---

### Post by dniMretsaM on 2012-04-16
Worked like a charm. Thanks!

---

