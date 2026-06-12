---
title: "How to solve integration of Qt Plugin in Eclipse? [java.lang.UnsatisfiedLinkError]"
date: 2009-01-15
forum: Programming Talk
---

### Post by kumar.samay on 2009-01-15
Hello Friends,

I am facing problem with opening Qt Project Editor and Qt Designer integrated in Eclipse. I can successfully create Qt Gui Project in Eclipse. It compiles as well execute without any problem. I can edit the code as well. Well first I tell about my system.

**System Information..**
OS : Ubuntu 8.04  2.6.24.23-generic
Eclipse (3.4.1) : /home/samay/eclipse/
---[installed as just extracting eclipse-SDK-3.4.1-linux-gtk.tar.gz, by the way CDT was installed as from Software Updates]
Qt (4.4.3) : /usr/local/Trolltech/Qt-4.4.3
---[installed as per instruction in Qt installation manual..]
Qt plugin : /home/samay/eclipse/plugin
---[installed as just extracting qt-eclipse-integration-linux.x86-gcc3.3-1.4.3.tar.gz and also did set the $PATH in .profile]
GCC version : 4.2.4

**Error in Eclipse IDE while opening *.pro and *.ui:**
Qt Project Editor:
An error has occurred. See error log for more details.
Could not initialize class com.trolltech.qtcppproject.pages.embedded.ProEditorView

Qt Designer:
An error has occurred. See error log for more details.
/home/samay/eclipse/plugins/com.trolltech.qtcppdesigner.linux.x86_1.4.3/lib/libqtcppdesigner.so: libstdc++.so.5: cannot open shared object file: No such file or directory


Kindly provide help if anybody knows....

Thanks for any help.
Samay

---

