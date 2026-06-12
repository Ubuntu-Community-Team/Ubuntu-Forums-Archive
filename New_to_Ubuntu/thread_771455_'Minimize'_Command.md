---
title: "'Minimize' Command?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by capleton on 2008-04-27
I've got this code:
```
#!/bin/bash

if ! pgrep $1 ; then
   $@
else
   pkill $1
fi
```
I would like to have something like this:
```
#!/bin/bash

if ! pgrep $1 ; then
   [MINIMIZE WINDOW] $@
else
   [MAXIMIZE WINDOW] $1
fi
```

Is it even possible?

---

### Post by capleton on 2008-04-28
anybody?

---

### Post by nsche on 2008-04-28
Given the right conditions and the requisite information it is possible.  You may have to write esentially a window manager to do it though.  The window state is something that is completely controlled by the window manager.  What you can do depends on the window manager that is used.  Personally I would start by reading up on the ICCCM (the document that specifies how inter client communication works).  I assume you can find it at the Xorg web site.

The other possibility is that some window manager might have a simple interface that you could use to do something like this.  Generally something like that is not easy to do.

There is no simple command to do it (AFAIK).

---

### Post by KIAaze on 2008-04-28
With KDE applications, you can use [DCOP]("http://developer.kde.org/documentation/other/dcop.html").

I haven't found an equivalent of it for Gnome apps yet. :/

But DCOP also works in a Gnome environment (altough only for KDE apps offering support for it). :)

_Example with the KDE text editor Kate:_
First, you need to get the ID of the window:
```
KATE_DCOPID=`dcop | grep kate`
```
Now to minimize:
```
dcop KATE_DCOPID __KateMainWindow#1 minimize
```
And maximize:
```
dcop KATE_DCOPID __KateMainWindow#1 maximize
```

_How to learn the available DCOP commands:_
```
[1][~]$  dcop
yakuake
karm-9006
kded
knotify
klauncher
kate-24311
[2][~]$  dcop kate-24311
qt
BlockSelectionInterface#1
BlockSelectionInterface#3
...
KateMainWindow#1
...
ViewStatusMsgInterface#1-1
__KateMainWindow#1
ksycoca
[3][~]$  dcop kate-24311 __KateMainWindow#1
QCStringList interfaces()
QCStringList functions()
QVariant property(QCString property)
...
void maximize()
void minimize()
...
void restore()
void show()
void close()

```
As you can see, it's pretty easy to figure out commands without using any documentation. :)
Arguments are passed to functions the same way as on a command-line:
ex:
```
dcop $KARM_DCOPID KarmDCOPIface addTask UltimateGame
```
will add a new task named "UltimateGame" to the KArm program.

[SIZE="1"]P.S: My command-prompt string if anybody was wondering how to do it:
PS1="\[\e[0;1;33;41m\][\#][\w]\$ \[\e[m\] "
The "#" gives the command number.[/SIZE]

---

