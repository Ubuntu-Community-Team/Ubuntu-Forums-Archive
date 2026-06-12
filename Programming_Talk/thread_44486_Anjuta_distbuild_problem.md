---
title: "Anjuta distbuild problem"
date: 2005-06-26
forum: Programming Talk
---

### Post by oldmarti on 2005-06-26
Hi, 
When I try to <Build Distribution> I receive error:
.....
.....
cp: cannot stat `./MyTest.pot': No such file or directory
make[2]: *** [dist2] Error 1


I take a look in MyTest/po directory:
ChangeLog
Makefile
Makefile.in
Makefile.in.in
POTFILES
POTFILES.in
but there isn't file MyTest.pot ;-(
Who must create this file? And with which content? I search the net and found only this:
[http://sourceforge.net/forum/message.php?msg_id=3219367](http://sourceforge.net/forum/message.php?msg_id=3219367)
and no solution. 
Thanks for any idea!

---

