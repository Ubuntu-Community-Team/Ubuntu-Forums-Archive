---
title: "apt-get &quot;E: Unable to locate package X&quot;"
date: 2012-10-08
forum: New to Ubuntu
---

### Post by Iecerint on 2012-10-08
Hi everyone --

I've recently had a computer switched from RedHat to Ubuntu and an attempting to install AFNI, a brain imaging software package.  While the actual AFNI installation per se was uneventful (i.e., it is available pre-compiled), I've had trouble installing some of the recommended libraries:

sudo apt-get install libXp tcsh PyQt4 R

Only tcsh installs correctly.  For the others, I receive the message "E: Unable to locate package X" for each of libXp, PyQt4, and R.

I have a theory that this may be because the instructions I'm reviewing are optimized for Fedora rather than Ubuntu, but I'm not sure, so I thought I'd try asking here.

Thank you for whatever help you're able to provide. :P

---

### Post by oldos2er on 2012-10-08
Use ```
apt-cache search pyqt4
``` for example, to find packages you need.

---

### Post by Iecerint on 2012-10-08
> **oldos2er said:**
> Use ```
apt-cache search pyqt4
``` for example, to find packages you need.

Here's the output from that command, if it's helpful:
```
abclab@cara:~$ apt-cache search pyqt4
pyqt4-dev-tools - Development tools for PyQt4
python-pyudev - Python bindings for libudev
python-qscintilla2 - Python bindings for QScintilla 2
python-qt4 - Python bindings for Qt4
python-qt4-dbg - Python bindings for Qt4 (debug extensions)
python-qt4-dbus - DBus Support for PyQt4
python-qt4-dbus-dbg - DBus Support for PyQt4 (debug extensions)
python-qt4-dev - Development files for PyQt4
python-qt4-doc - Documentation and examples for PyQt4
python-qt4-phonon - Python bindings for Phonon
python-qt4-phonon-dbg - Python bindings for Phonon (debug extensions)
python-qt4-sql - Python bindings for PyQt4's SQL module
python-qt4-sql-dbg - Python bindings for PyQt4's SQL module (debug extension)
python3-dbus.mainloop.qt - DBus Support for PyQt4 with Python 3
python3-dbus.mainloop.qt-dbg - DBus Support for PyQt4 (debug extensions for Python 3)
python3-pyqt4 - Python3 bindings for Qt4
python3-pyqt4-dbg - Python3 bindings for Qt4 (debug extensions)
python3-pyqt4.phonon - Python3 bindings for Phonon
python3-pyqt4.phonon-dbg - Python3 bindings for Phonon (debug extensions)
python3-pyqt4.qtsql - Python3 bindings for PyQt4's SQL module
python3-pyqt4.qtsql-dbg - Python3 bindings for PyQt4's SQL module (debug extension)
python-guidata - dataset manipulation GUI generator
python-guiqwt - efficient 2D data-plotting library
python-pivy - Coin binding for Python
python-qt4-gl - Python bindings for Qt4's OpenGL module
python-qt4-gl-dbg - Python bindings for Qt4's OpenGL module (debug extension)
python-spyderlib - python IDE for scientists
python3-pyqt4.qsci - Python 3 bindings for QScintilla 2
python3-pyudev - Python3 bindings for libudev
```

---

### Post by Vaphell on 2012-10-08
it returned the list of packages that exist in repository and are related to 'pyqt4' phrase. You should try your luck with python-qt4
Do the same with the other packages that fail. apt-cache search, find something that looks like it and install it.

libXp - probably libxp6
R - probably r-base

you can also install synaptic and browse packages and their descriptions with a shiny gui

---

### Post by Iecerint on 2012-10-09
Thank you; I think my problem is solved. :)

---

