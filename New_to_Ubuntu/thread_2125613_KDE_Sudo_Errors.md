---
title: "KDE Sudo Errors"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by Absolute Terror on 2013-03-14
```
kbuildsycoca4(3041) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/im-switch.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(3041) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/kde4/bluedevil-network-dun.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(3041) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/kde4/bluedevil-network-panu.desktop" is not compliant with XDG standard (missing trailing semicolon). 
"KConfigIni: In file /tmp/kde-root/kconf_updateHm3043.tmp, line 1: " Invalid entry (missing '=') 
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /root/.config/ibus/bus
```

Whenever I use ANYTHING as sudo or kdesudo, I get errors similar to this. Is there something special I need to do with KDE?

This is from kdesudo kate

---

### Post by carl4926 on 2013-03-14
Not sure but try

sudo kate

or 

kdesu kate

---

### Post by Absolute Terror on 2013-03-14
kdesu doesn't work at all and sudo behaves the same.

---

### Post by oldos2er on 2013-03-14
> **Absolute Terror said:**
> Whenever I use ANYTHING as sudo or kdesudo, I get errors similar to this. Is there something special I need to do with KDE?

This is from kdesudo kate

I get something very similar from running **kdesudo kate**, but it works fine. If it's working for you I'd just ignore all the terminal output.

---

