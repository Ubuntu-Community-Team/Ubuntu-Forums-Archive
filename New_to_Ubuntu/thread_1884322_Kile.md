---
title: "Kile"
date: 2011-11-21
forum: New to Ubuntu
---

### Post by mavenuparker on 2011-11-21
Kile doesn't get started and every time I try to start it shows up this window. It works fine when I open it as a root( but it is difficult to edit the files later) and also as a Guest( by logging out and signing in as a guest). 

Please help me

---

### Post by PaulW2U on 2011-11-21
Take a look at [http://ubuntuforums.org/showthread.php?p=9964457](http://ubuntuforums.org/showthread.php?p=9964457).

It suggests that one of the configuration files in your home folder might have its permissions set incorrectly which is why you can run kile as root or as another user. It has been marked as 'solved' so it might offer the solution you are looking for.

---

### Post by mavenuparker on 2011-11-21
kile when initiated through terminal gives this output, which doesnt look like a permission issue.

```
maven@maven-PIG31T:~$ kile
Connected to accessibility bus at:  "unix:abstract=/tmp/dbus-4xVgIZowho,guid=06b6502e82e049ddc7ff246d00000092" 
Registered DEC:  true 
kile(3162)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib' prefix: "libkonsolepart.so"
Invalid parent:  0x956e200 Kile(0xbfb1701c) 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Requesting child objects for an interface that is a virtual child itself. 
Invalid parent:  0x97f58a8 QToolBox(0x91fee10) 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 1 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 2 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 3 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 4 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 5 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 6 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 7 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 8 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 9 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 10 
QSpiAdaptor::getChild INVALID CHILD:  QToolBox(0x91fee10) 11 
ASSERT: "interface->childCount() == children.count()" in file adaptor.cpp, line 200
KCrash: Application 'kile' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/maven/.kde/socket-maven-PIG31T/kdeinit4__0

[1]+  Stopped                 kile
maven@maven-PIG31T:~$ QSocketNotifier: Invalid socket 23 and type 'Read', disabling...

```

---

### Post by mavenuparker on 2011-11-22
Someone please help, its really important :(

---

### Post by krige on 2011-11-30
I am having the same problem. Did you find a solution?

---

### Post by mavenuparker on 2011-12-02
No. 
I've installed TexMaker for completing my work.

---

### Post by orestesmas on 2011-12-02
> **mavenuparker said:**
> Kile doesn't get started and every time I try to start it shows up this window. It works fine when I open it as a root( but it is difficult to edit the files later) and also as a Guest9 bu logging out and signing in as a guest). 

Please help me

When you are root you are using a different user configuration, so that suggest a problem with your user's kile configuration. Try deleting it, which is located at /home/maven/.kde/share/config/kilerc

Kile will recreate it (with default values) at next start. If you made heavy customizations to kile perhaps you would like to make a backup copy of the configuration file before deleting it.

---

### Post by krige on 2011-12-05
> **orestesmas said:**
> When you are root you are using a different user configuration, so that suggest a problem with your user's kile configuration. Try deleting it, which is located at /home/maven/.kde/share/config/kilerc

Kile will recreate it (with default values) at next start. If you made heavy customizations to kile perhaps you would like to make a backup copy of the configuration file before deleting it.

I have tried that but didn't work. Kile keeps crashing at start up.

---

### Post by orestesmas on 2011-12-15
Mmm.. Well, the fact Kile works when you're logged in as a different user definitely suggests (at least to me) a configuration problem, maybe of the KDE itself.

Please, try another thing: try to rename your entire (hidden) ".kde" directory to, for instance, ".kde-backup". Then log out and log in again. KDE will create a new fresh .kde directory with default values. Sure, you are going to temporarily lose the configuration of your KDE apps, but if you are now able to start kile then the problem is a configuration one.

You can restore your configuration simply renaming ".kde-backup" to ".kde" again.

---

### Post by krige on 2011-12-16
> **orestesmas said:**
> Mmm.. Well, the fact Kile works when you're logged in as a different user definitely suggests (at least to me) a configuration problem, maybe of the KDE itself.

Please, try another thing: try to rename your entire (hidden) ".kde" directory to, for instance, ".kde-backup". Then log out and log in again. KDE will create a new fresh .kde directory with default values. Sure, you are going to temporarily lose the configuration of your KDE apps, but if you are now able to start kile then the problem is a configuration one.

You can restore your configuration simply renaming ".kde-backup" to ".kde" again.

Thanks for the help!

I am the only user of a machine with Ubuntu Desktop 64c 11.10 freshly installed (not an upgrade). I never succeeded in running Kile, I had no configuration previously stored.

I deleted the .kde/ directory. After I run Kile I see the .kde/ directory is recreated but the application keeps crashing at startup with the same error.

---

