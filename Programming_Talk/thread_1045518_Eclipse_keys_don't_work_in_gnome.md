---
title: "Eclipse keys don't work in gnome"
date: 2009-01-20
forum: Programming Talk
---

### Post by pwaldo on 2009-01-20
Hi all,

I am just starting out with Eclipse in gnome.  I'm trying to use Eclipse's keystrokes, but apparently gnome is intercepting them.  For example, when I hit Ctrl+Space for Content Assist, gnome just beeps at me!  Any ideas?  Thanks!

---

### Post by jespdj on 2009-01-20
Strange. Ctrl + Space works normally for me in Eclipse.

Check with System > Preferences > Keyboard Shortcuts (in GNOME) if Ctrl + Space is mapped to something else.

In Eclipse, look at General > Keys to see what keyboard shortcuts are defined in Eclipse.

Are you running Compiz (desktop effects)? Install Compiz Config Settings Manager (if you don't already have it) and go to System > Preferences > Advanced Desktop Effects Settings and look around there if Ctrl + Space is mapped to a Compiz function.

---

### Post by pwaldo on 2009-01-20
Thanks for the reply!  I delved further and it turns out that the reason for the beeping is that Content Assist can't find a match.

I'm using a PyDev project in eclipse and the django framework.  For some reason, eclipse is not finding the django python files.  I added /var/lib/python-support/python2.5 to Eclipse's PYTHONPATH.  django is installed under this directory, but Eclipse won't Assist on it....

---

