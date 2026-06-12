---
title: "Qjoypad compiling error"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by midasmind on 2012-12-19
I'm about 2 weeks into my first Ubuntu installation ever (Xubuntu 12.10) and am seeking the best way to emulate the keyboard with my Logitech Dual Action gamepad.  Best software I've found is Qjoypad, but it's not in the repositories (and playdeb is down) so I figured I'd try my hand at compiling it, and I'm having issues.  So first off, if you know another program that does what it does with a GUI, I'd just as well use that.

That being said, after following all instructions I could find on preparing my system for compiling and reading the installation guide that came with it, I run into this apparently old problem, and don't know how to fix it from the information I've found.

```
midasmind@midasmind-H61M-S2H:/usr/local/src/qjoypad-4.1.0/src$ ./config
Error: you need at least Qt version 4.2 to use this program
midasmind@midasmind-H61M-S2H:/usr/local/src/qjoypad-4.1.0/src$ which qmake
/usr/bin/qmake
midasmind@midasmind-H61M-S2H:/usr/local/src/qjoypad-4.1.0/src$ qmake --version
QMake version 2.01a
Using Qt version 4.8.3 in /usr/lib/x86_64-linux-gnu
midasmind@midasmind-H61M-S2H:/usr/local/src/qjoypad-4.1.0/src$ 
```This is what the INSTALL.txt that came with it says, and apparently it shows how to fix the problem, but I don't know exactly how to do it.

> If those steps don't work for you, here are some common problems:

Compilations fails with along the lines of:
axis.h:21: error: expected class-name before ‘{’ token
axis.h:22: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
axis.h:24: error: expected ‘;’ before ‘friend’
axis.h:29: error: ‘QTextStream’ has not been declared
axis.h:31: error: ‘QTextStream’ has not been declared
axis.h:40: error: ‘QString’ does not name a type
axis.h:44: error: ‘QString’ does not name a type
axis.h:89: error: ISO C++ forbids declaration of ‘QTimer’ with no type

Most likely you're using the Qt3 version of qmake; QJoyPad needs to use Qt4 to 
work properly.  The config script is supposed to detect this properly, but in
the event it fails you should find what the proper executable is (if you think
you've found it run it with the --version option to make sure it is for Qt
4.0 or greater).  Then rerun the config script with the --qmake4bin=BIN option,
where BIN is the executable name of the proper qmake binary, or a path to the
proper qmake binary.

---

### Post by lordievader on 2012-12-19
The Ikoinoba ppa has the package qjoypad available for both Precise and Quantal.
No need to compile anything, just follow these steps:
```
sudo add-apt-repository ppa:ikoinoba/ppa
sudo apt-get update
sudo apt-get install qjoypad
```Hope this helps ;)

Ikoinoba page: [https://launchpad.net/~ikoinoba](https://launchpad.net/~ikoinoba)

---

### Post by midasmind on 2012-12-19
Yup.  That works.  Thanks lordie.

---

