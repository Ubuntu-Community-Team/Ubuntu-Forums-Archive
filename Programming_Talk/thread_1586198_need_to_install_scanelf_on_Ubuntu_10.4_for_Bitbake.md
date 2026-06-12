---
title: "need to install scanelf on Ubuntu 10.4 for Bitbake"
date: 2010-10-01
forum: Programming Talk
---

### Post by bertszoghy on 2010-10-01
Hello,

Am trying out Open Embedded for a board.

I have been able to cross-compile a simple C program on my x86 Ubuntu desktop and run it on my ARM Angstrom board.

I am now trying the Bitbake getting started examples and I seem to be missing a dependency:

ERROR: Can not check RPATH, scanelf (part of pax-utils-native) not found

There seems to be no such on Ubuntu 10.4. I already pax-utils installed.

Any help is greatly appreciated.

Best regards,
Bert

---

### Post by PC-XT on 2010-10-02
I found this thread: [http://comments.gmane.org/gmane.comp.handhelds.openembedded/15494](http://comments.gmane.org/gmane.comp.handhelds.openembedded/15494)

The second post has the error, and it takes a few posts to resolve it by editing the conf file. I don't know if it will help, and if you try any edits, you might want to make a copy in case you need to put it back later.

---

