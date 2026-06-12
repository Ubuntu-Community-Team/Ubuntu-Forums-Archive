---
title: "suggest me a debugger"
date: 2006-09-21
forum: Programming Talk
---

### Post by pranith on 2006-09-21
hi ppl,
    I was wondering if there are ne graphical debuggers in c++ ...
plz suggest me some good debuggers. kdevelop and anjuta debuggers are not that good. atleast I dont like them.
thanks in anticipation
pranith

---

### Post by Angry on 2006-09-21
I too was disappointed by both the anjuta and kdevelope ide's, but after a couple of hours of learning about make files, I found that the best thing to use is gedit and the command line.

---

### Post by X.Cyclop on 2006-09-21
GDB.:) 

> I too was disappointed by both the anjuta and kdevelope ide's, but after a couple of hours of learning about make files, I found that the best thing to use is gedit and the command line.
:cool:

---

### Post by MWAAAHAAA on 2006-09-23
You should try 'ddd', the Data Display Debugger

---

### Post by Jessehk on 2006-09-23
I found a quick curses interface to gdb called cgdb in the repositories.

```

$ sudo aptitude show cgdb
Package: cgdb
State: installed
Automatically installed: no
Version: 0.5.3-2
Priority: optional
Section: universe/devel
Maintainer: Robert Lemmen <robertle@semistable.com>
Uncompressed Size: 213k
Depends: libc6 (>= 2.3.4-1), libncurses5 (>= 5.4-5), libreadline5, gdb
Description: a curses-based interface to the GNU Debugger (GDB)
 CGDB is a curses  fontend to the GNU Debugger (GDB). The goal of CGDB is to be
 lightweight and responsive; not encumbered with unnecessary features.

 The interface is designed to deliver the familiar GDB text interface, with a
 split screen showing the source as it executes. The UI is modeled on the
 classic Unix text editor, vi. Those familiar with vi should feel right at home
 using CGDB.

 Some features offered by CGDB are:
 * Syntax-highlighted source window
 * Visual breakpoint setting
 * Keyboard shortcuts for common functions
 * Searching source window (using regexp)

```

---

