---
title: "Need help compling something"
date: 2005-01-19
forum: Packaging and Compiling Programs
---

### Post by Dko on 2005-01-19
EDIT: I just realized I placed this in the wrong section.  Could this be moved please to the compiling section?
I recently downloaded a custom smaug (Dragon Ball Saga 2.5) code base and have been trying to compile it.  Im a lot more adept at using Visual C++ 6.0 to compile things so the errors here, that I get confuse me.  They are all very simmilar and probibly take a simple fix.  Possibly by editing the make file?  Well here are that last few lines I get when I compile.  As you can see there are so any the compiler bails.

mud.h:6997: error: syntax error at '@' token
mud.h:6997:987: warning: null character(s) ignored
mud.h:6997: error: stray '\2' in program
mud.h:6997:992: warning: null character(s) ignored
mud.h:6997: error: stray '\4' in program
mud.h:6997:994: warning: null character(s) ignored
mud.h:6997: error: syntax error at '@' token
mud.h:6997: error: stray '`' in program
mud.h:6997: error: stray '\32' in program
mud.h:6997: error: syntax error at '@' token
mud.h:6997:1003: warning: null character(s) ignored
mud.h:6997: error: stray '\2' in program
mud.h:6997:1012: warning: null character(s) ignored
mud.h:6997: error: stray '\2' in program
mud.h:6997:1032: warning: null character(s) ignored
mud.h:6997: error: stray '\310' in program
mud.h:6997: error: stray '\37' in program
mud.h:6997: error: syntax error at '@' token
mud.h:6997:1039: warning: null character(s) ignored
mud.h:6997: confused by earlier errors, bailing out
make[1]: *** [act_comm.o] Error 1
make[1]: Leaving directory `/mnt/windows/My Documents/C++ programs/dbsc2.5/src'
make: *** [all] Error 2
root@roc-24-169-212-6:/mnt/windows/My Documents/C++ programs/dbsc2.5/src #

Any help is appreciated thanks. ^^

---

### Post by dataw0lf on 2005-01-19
Could you give us the specific lines in question? This would help us help you out.
dataw0lf

---

