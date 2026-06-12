---
title: "kubuntu touchpad settings crashes out"
date: 2011-07-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-07-14
as soon as i click touchpad in kmenu>system settings>input devices>touchpad i get a crash

this is all i get when starting systemsettings from konsole
```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ systemsettings
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/buzzmandt/.config/ibus/bus
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ QSocketNotifier: Invalid socket 11 and type 'Read', disabling...
KCrash: Application 'systemsettings' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/buzzmandt/.kde/socket-buzzmandt-Compaq-Presario-CQ60-Notebook-PC/kdeinit4__0

```

---

### Post by buzzmandt on 2011-07-14
bug report submitted as 
[https://bugs.kde.org/show_bug.cgi?id=277800](https://bugs.kde.org/show_bug.cgi?id=277800)

---

### Post by buzzmandt on 2011-07-14
ok, so kde devs listed it as dup of a kde 4.4 bug and have it listed as a downstream problem.  specifically a kubuntu only problem. they had a fix for karmic for the python-qt4 issue that was causing it.

I'm gonna bug report this one to ubuntu bugs, and i'll update this thread accordingly.

---

### Post by buzzmandt on 2011-07-14
done
[https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/810803](https://bugs.launchpad.net/ubuntu/+source/kde-workspace/+bug/810803)

---

