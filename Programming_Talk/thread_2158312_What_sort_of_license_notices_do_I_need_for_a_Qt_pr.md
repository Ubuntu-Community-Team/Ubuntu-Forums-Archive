---
title: "What sort of license notices do I need for a Qt program?"
date: 2013-06-28
forum: Programming Talk
---

### Post by MythicalBeast on 2013-06-28
I wrote a program that links with Qt, and I don't know what I need to do to comply with the LGPL in terms of saying that I used that library. Do I need to say anything at all? Just put "Qt libraries copyright (c) Digia" with a link to the LGPL? Or should I provide the full text of the LGPL along with my program (which uses the BSD license btw)?

 
Konsole, for example, doesn't mention Qt at all in the "about" dialog, it just says "Using KDE development platform". Should I just put "Using Qt 4" prominently somewhere?

---

### Post by Some Penguin on 2013-06-29
You might find [http://www.slideshare.net/qtbynokia/qt-licensing-explained](http://www.slideshare.net/qtbynokia/qt-licensing-explained) quite relevant.
Also, [http://stackoverflow.com/a/919665](http://stackoverflow.com/a/919665)

Use dynamic linking, and if you need to patch the library itself then those changes need to be released as open-source, too.

And you're also nominally supposed to make available the QT library source code, too, although you don't have to assume that everybody will want it and to bundle it with the executable.

---

### Post by MythicalBeast on 2013-06-29
Thank you, it helps to have a succinct explanation. I tried reading the LGPL and immediately got swamped in all the legal terminology, haha.

---

### Post by nvteighen on 2013-06-29
Be aware that this only applies if you're distributing the binary. If you distribute just the source of your code, you don't have to credit anyone.

However, in the GPLv3 (remember that LGPLv3 works as a set of additional permissions on top of the GPLv3) there is the concept of "System library", which are not to be considered part of the licensed application. These libraries are defined in Section 3 and they amount to things like Qt, i.e. stuff whose source code is widespread, easily found, meant just to make your program work with  a certain platform (X11, in this case), etc. In that case, you wouldn't be required to treat your code to be a derivative work of Qt. If you take a look to any usual program written in Gtk, you'll see they don't even mention anything related to it.

---

