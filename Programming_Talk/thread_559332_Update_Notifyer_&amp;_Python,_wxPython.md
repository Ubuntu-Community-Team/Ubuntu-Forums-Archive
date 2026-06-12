---
title: "Update Notifyer &amp; Python, wxPython"
date: 2007-09-25
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2007-09-25
The Update Notifyer offered new libs for upgrading the Linux kernel today. I've never had a problem before with those types of upgrades. What the update/restart did was wipe out all of my custom Python installs, e.g. wxWidgets, Python 2.5.1.6-cvs.

So my question: Do I...

1. Terminal --> export PYTHONPATH=$PYTHONPATH:<my pythonpath>

or, do I...

2. edit bash?

Or do I ...

3. have to ./configure from source code, (again), sudo make, sudo make install, sudo python setup.py install

==============

After spending some time looking at this problem...

I've got python vers. 2.3, 2.4, 2.5 and all because I installed a couple of GUIs using the Repositories to investigate making widgets. I wanted Python2.5 with wxPython 2.8.2 and for some reason that link is gone. wx-gtk2.8/demo.py was running yesterday and today it does not.

===================
OK, somehow, the apt-get version of 2.6 wxWidgets configured into Python 2.5. I needed the combination of wx2.8-GTK-unicode with Python2.5. The .debs from apt-get links 2.4Python with wx2.8. For now, I have to link with a header in my scripts...

import wxversion                  # part of wx 'helpful' stuff, located in /usr/share/pycentral
wxversion.select('2.8.4.2')

---

