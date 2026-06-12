---
title: "gdb issue: &amp;&quot;warning: GDB: Failed to set controlling terminal: Invalid argument\n&quot;"
date: 2010-09-13
forum: Programming Talk
---

### Post by crypticlynx on 2010-09-13
Hi!

I have tried Code::Blocks and the qtcreator. With both I can compile programs, but the debugger which apperantly is gdb for both doesn't work. I get the message:
p, li { white-space: pre-wrap; } &"warning: GDB: Failed to set controlling terminal: Invalid argument\n"

Does anybody here know how to solve this problem?

PS: I have already followed the advice in another forum: I created a Qt.conf in  /etc/ld.so.conf.d containing the directory of my qt libraries, i.e.:
# Qt libraries
/usr/lib/qtcreator
/usr/lib/qtcreator/gdbmacros

---

### Post by dbrinto on 2010-10-09
Hey crypticlynx,

There is an issure with GDB-7.0+ with qtcreator. You need to downgrade to gdb-6.8

a deb package for gdb-6.8 can be found here: [http://packages.ubuntu.com/jaunty/gdb]("http://packages.ubuntu.com/jaunty/gdb")

This fixed the issue for me... Although we're now using an older version of gdb. If you need a more recent version this article [http://qt.gitorious.org/qt-creator/pages/FrequentlyAskedQuestions#Debugger]("http://qt.gitorious.org/qt-creator/pages/FrequentlyAskedQuestions#Debugger") has info on getting an updated gdb-7.0.1 that should work (although I didn't test it out, and the latest version of gdb is 7.2 anyway).

Hope that helps,
Dave

---

