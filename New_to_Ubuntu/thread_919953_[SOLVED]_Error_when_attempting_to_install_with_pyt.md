---
title: "[SOLVED] Error when attempting to install with python"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-14
Hi, all:
I'm attempting to install kUWC, a conversion program for taking my Webshots images and batch converting them to jpgs.  This is the program: [http://www.kde-apps.org/content/show.php?content=43440](http://www.kde-apps.org/content/show.php?content=43440)

I was getting error messages about missing pyqt, so I installed those packages.  Now, I'm getting this error message when I run python setup.py install: 

tarahmarie@tarahmarie-desktop:~/Documents/Software/kUWC$ python setup.py install
running install
running build
running build_messages
/usr/bin/msgfmt -o po/fr.gmo po/fr.po
running checkpyqt
Your Qt version is too old. Version 3.3.0 or higher is required, found 3.3.8b.

Prima facie, this doesn't make any sense to me; how could a later version number be older than the one required?

---

### Post by jemate18 on 2008-09-14
> **tarahmarie said:**
> Hi, all:
I'm attempting to install kUWC, a conversion program for taking my Webshots images and batch converting them to jpgs.  This is the program: [http://www.kde-apps.org/content/show.php?content=43440](http://www.kde-apps.org/content/show.php?content=43440)

I was getting error messages about missing pyqt, so I installed those packages.  Now, I'm getting this error message when I run python setup.py install: 

tarahmarie@tarahmarie-desktop:~/Documents/Software/kUWC$ python setup.py install
running install
running build
running build_messages
/usr/bin/msgfmt -o po/fr.gmo po/fr.po
running checkpyqt
Your Qt version is too old. Version 3.3.0 or higher is required, found 3.3.8b.

Prima facie, this doesn't make any sense to me; how could a later version number be older than the one required?

Based on the results, you have to update your QT version..

---

### Post by tarahmarie on 2008-09-14
How do I do that?

---

