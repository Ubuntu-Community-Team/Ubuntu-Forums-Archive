---
title: "prevelant linking error in natty"
date: 2010-12-15
forum: Packaging and Compiling Programs
---

### Post by mc4man on 2010-12-15
Somewhat curious if anyone has some insight to this. (why happening on natty, but not on maverick, ect.

In 3 out of 7 sources I've built in natty the below error has occurred, exact same in all three except for the lib mentioned. Have never seen this error before, in all cases these same sources build fine in maverick.
In 2 out of the 3 could resolve, the 3rd no dice.
(totem-2.26.5 w/ a LDFLAGS=-lICE
(dvdstyler-1.8.1 w/ a LIBS=-ljpeg
The error as seen in libzeitgeist-0.2.14

 > CCLD   find-events
/usr/bin/ld: find-events.o: undefined reference to symbol 'g_type_init'
/usr/bin/ld: note: 'g_type_init' is defined in DSO /usr/lib/libgobject-2.0.so.0 so try adding it to the linker command line
/usr/lib/libgobject-2.0.so.0: could not read symbols: Invalid operation


Also noticed exact same here, a fix released (source edit.?), though no info as yet to how
[https://bugs.launchpad.net/ubuntuone-client/+bug/680719](https://bugs.launchpad.net/ubuntuone-client/+bug/680719)

---

