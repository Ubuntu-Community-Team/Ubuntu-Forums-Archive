---
title: "Compiling lcd module for gpsim"
date: 2009-04-30
forum: Packaging and Compiling Programs
---

### Post by zcx2007 on 2009-04-30
Has anyone managed to successfully compile the lcd module for gpsim?

[http://www.dattalo.com/gnupic/lcd.html](http://www.dattalo.com/gnupic/lcd.html)

I have successfully compiled gpsim-0.23.0 using sources from...

[http://sourceforge.net/project/showfiles.php?group_id=2341&package_id=2303&release_id=669748](http://sourceforge.net/project/showfiles.php?group_id=2341&package_id=2303&release_id=669748)

But have had no luck compiling lcd-0.2.1 from...

[http://www.dattalo.com/gnupic/lcd-0.2.1.tar.gz](http://www.dattalo.com/gnupic/lcd-0.2.1.tar.gz)

./configure seems to work OK but make fails...

In file included from lcdgui.cc:24:
lcd.h:64: error: expected class-name before ‘{’ token
lcd.h:77: error: expected class-name before ‘{’ token
lcd.h:109: error: expected class-name before ‘{’ token
lcd.h:114: error: expected `)' before ‘*’ token
lcd.h:124: error: expected `)' before ‘*’ token
lcd.h:223: error: expected class-name before ‘{’ token
lcd.h:342: error: ISO C++ forbids declaration of ‘ExternalModule’ with no type
lcd.h:342: error: expected ‘;’ before ‘*’ token
lcd.h:394: error: ISO C++ forbids declaration of ‘ExternalModule’ with no type
lcd.h:394: error: expected ‘;’ before ‘*’ token
make[1]: *** [lcdgui.lo] Error 1

Any ideas?

zcx

---

### Post by zcx2007 on 2009-05-01
Solved.

Got lcd-0.2.10 from svn which compiles correctly and runs.

zcx

---

