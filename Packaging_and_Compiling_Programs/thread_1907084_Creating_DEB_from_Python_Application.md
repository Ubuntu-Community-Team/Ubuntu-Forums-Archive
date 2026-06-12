---
title: "Creating DEB from Python Application"
date: 2012-01-10
forum: Packaging and Compiling Programs
---

### Post by calmcl1 on 2012-01-10
Hi there,

I am currently writing an application in Python 2.7 (a radio playout system, if you're interested). It consists of a series of small modules and one central module which imports the rest. It works as it should. I have written a basic 'setup.py' and 'MyAppName.desktop' file to accompany it.

However, when I compile this into a .deb for distribution, the build is successful but the files are placed into /usr/share/pyshared. This would be fine if I was writing an extension or module, but as this is a full-blown application, I was wondering if it possible to compile the .deb in such a way that it extracts the files to /usr/share/MyAppName instead.

It would be a bonus if I could get the .desktop to extract into /usr/share/Applications, too.

It doesn't matter which build tool I use: debhelper, CDBS, stdeb - they all have the same effect. Also, dh_make does not generate a 'dirs' file, as it does in the Packaging Guide - although that does seem to have been written some time ago.

Any ideas?

Thanks in advance,

calmcl1.

UPDATE: This problem has been solved. I didn't realise that it was possible to use a Makefile to direct files to the correct installation dirs. This also holds true for the .desktop file.
Check out this awesome tutorial (though it's a little dated): [http://savetheions.com/2010/01/20/packaging-python-applicationsmodules-for-debian/](http://savetheions.com/2010/01/20/packaging-python-applicationsmodules-for-debian/)

---

