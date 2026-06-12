---
title: "Kguitar error"
date: 2007-03-06
forum: Programming Talk
---

### Post by AbyssRock on 2007-03-06
Hi to everyone!
Excuse me if I bother here:( , I know it's not the right forum,  but no one could help me in other forums..
I'm having a little problem installing kguitar:

when I start ./configure command, it gives me this error

******************
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
********************
I'm new in Linux and I don't know where I can find these files... could anyone help me :confused: ..

Thanks
:)

---

### Post by lnostdal on 2007-03-06
you need the development-files for X and KDE installed .. i'm just guessing here, but:

```

sudo aptitude install kde-devel

```

..might install both the X and KDE-development stuff required for you to compile KGuitar

you can also use the `alien'-package to convert an .rpm-file to .deb-format .. in any case this might not work as the latest release of KGuitar seems a bit old

---

### Post by gsub on 2007-06-02
hello, everyone.

i'm trying to get kguitar to work as well, and installing kde-devel got me through the ./configure routine.

the next step seems to be 'make', but it exits giving the error messages below.

could someone please help?

thanks.


In file included from kguitar_part.cpp:9:
tabsong.h:6:19: error: qlist.h: No such file or directory
In file included from kguitar_part.cpp:18:
convertxml.h:6:21: error: qvector.h: No such file or directory
/usr/share/qt3/include/qxml.h:224: warning: 'class QXmlReader' has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:407: warning: 'class QXmlContentHandler' has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:424: warning: 'class QXmlErrorHandler' has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:433: warning: 'class QXmlDTDHandler' has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:441: warning: 'class QXmlEntityResolver' has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:448: warning: 'class QXmlLexicalHandler' has virtual functions but non-virtual destructor
/usr/share/qt3/include/qxml.h:461: warning: 'class QXmlDeclHandler' has virtual functions but non-virtual destructor
convertxml.h:85: error: ISO C++ forbids declaration of 'QVector' with no type
convertxml.h:85: error: expected ';' before '<' token
make[3]: *** [kguitar_part.lo] Error 1
make[3]: Leaving directory `/home/gsub/Desktop/kguitar-0.5/kguitar'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/gsub/Desktop/kguitar-0.5/kguitar'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gsub/Desktop/kguitar-0.5'
make: *** [all] Error 2

---

### Post by DoktorSeven on 2007-06-02
When you get " (whatever).h : no such file or directory" file errors in make (or configure), apt-file (**sudo apt-get install apt-file** then **sudo apt-file update** to set it up) helps; just do an **apt-file search (whatever.h)** for the missing header, then install the most likely candidate.

In your case, looks like either libqt3-compat-headers or libqt4-dev; not sure which is best here, but you can try either/or.

---

