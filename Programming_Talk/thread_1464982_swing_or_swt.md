---
title: "swing or swt"
date: 2010-04-28
forum: Programming Talk
---

### Post by Finalfantasykid on 2010-04-28
I didn't really know very much about swt until recently, so I have been using swing for a program that I am making, but I have been reading some stuff about swt which makes me think that it is better than swing, but before I rewrite large portions of the code, in your opinions, which is better swing or swt?

---

### Post by ja660k on 2010-04-29
by swt you mena awt? thats the other gui library for java.

the diffrence is that swing will inherit the look and feel of the of you are on, so if you take your app to another OS it will look like a native program.. all well and good, but awt is for custom, where swing inherits aesthetics from the os, awt is good if we want to create our own "look"

---

### Post by Finalfantasykid on 2010-04-29
> by swt you mena awt? thats the other gui library for java.

Nope, I mean this one [http://www.eclipse.org/swt/](http://www.eclipse.org/swt/)

---

### Post by kahumba on 2010-04-29
Of course Swing.
SWT has been picked up by IBM in the early days when Swing was painfully slow. Now there's no serious reason to use SWT any longer because:
1) Swing comes bundled with Java and SWT does not, hence the mere download size of the SWT version is bigger by about 2MB, for example for an applet it's probably too much of an overhead.
2) Trust me, SWT is buggier
3) With SWT you automatically create a lot of problems for yourself by having to create different builds of your app with custom SWT for every platform and architecture, plust having to write platform specific startup files for Java to find SWT.
4) With Swing you have more control over your widgets, over how they're painted because Swing is painted directly by Java while SWT is not.
5) The list goes on...

---

### Post by Drone022 on 2010-04-29
Swing it baby!

---

### Post by Finalfantasykid on 2010-04-29
Ah ok, I guess I'll stay away from swt then :P

---

### Post by mmix on 2010-04-30
[http://qt.gitorious.org/qt-jambi](http://qt.gitorious.org/qt-jambi)

---

