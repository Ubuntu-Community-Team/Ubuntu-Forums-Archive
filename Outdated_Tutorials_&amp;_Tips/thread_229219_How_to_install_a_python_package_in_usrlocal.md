---
title: "How to install a python package in /usr/local/"
date: 2006-08-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Pericles on 2006-08-04
Some packages are written in python and installing them locally requires a different approach.

If you want to test a different version of an installed package you cannot install from a repository or use a .deb file as it will conflict with or remove the existing version in /usr/lib/python$VER/site-packages/ .

The solution is to install from the source.  This is not as scary as it sounds.  You need to get the source archive (probably a .tar.gz file) from the package website.  The standard way to install (after getting and unpacking the archive) is to run

   sudo python setup.py install

which will probably be mentioned in the install file, however this will also overwrite/damage your existing version.  To install in /usr/local or your home folder you must specify one of these locations as follows:

   sudo python setup.py install --prefix=/usr/local

or

   python setup.py install --home=~

However trying either of these commands with a standard Ubuntu system will probably result in an error message like:

   running install
   error: invalid Python installation: unable to open 
/usr/lib/python2.4/config/Makefile (No such file or directory)

To be able to install a python package in /usr/local you first have to install python-dev (even though you are not doing development).  After installing python-dev using synaptic or apt-get, you can use the install command to put the package under /usr/local (this is the standard location for manually installed packages).  Most package files will be put in /usr/local/lib/python$VER/site-packages/.  Executables will end up in /usr/local/bin.

Packages installed from source are not tracked by the package manager, so you will have to check dependencies yourself and delete the files manually when you want to uninstall the package.

---

