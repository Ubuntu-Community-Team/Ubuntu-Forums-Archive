---
title: "Please recommend some read materials about Compilation"
date: 2012-07-02
forum: Programming Talk
---

### Post by pellyhawk on 2012-07-02
Recently, while compiling my project. I met many issues (some of them are file path issue, such as cannot find out lib) and I have to look up Makefile and compilation logs. Somebody can recommend me some reading materials which make me clear about Makefile, path and compilation.

Thanks.

---

### Post by Zugzwang on 2012-07-02
For which programming language and which tool chain?

---

### Post by pellyhawk on 2012-07-02
> **Zugzwang said:**
> For which programming language and which tool chain?

c/c++, java, python

sorry, tool chain means?

Thanks.

---

### Post by 11jmb on 2012-07-02
> **pellyhawk said:**
> Recently, while compiling my project. I met many issues (some of them are file path issue, such as cannot find out lib) and I have to look up Makefile and compilation logs. Somebody can recommend me some reading materials which make me clear about Makefile, path and compilation.

Thanks.

Can you share specifics like error messages? Is the project you are trying to compile open-source? If so, what is its name/version?

> **pellyhawk said:**
> 
sorry, tool chain means?


[http://en.wikipedia.org/wiki/Toolchain](http://en.wikipedia.org/wiki/Toolchain)

---

### Post by pellyhawk on 2012-07-02
I am using Qt to build my project and got the following compilation trace. I was confused by it. Thus, I have hope to learn more about Makefile, path and compilation while I am using C/C++, Java or Python shell script to program.

By the way, what is tool chain?

Thanks.

```
mike@mike-desktop:/mnt/hgfs/VBox_Shared/SeaTools$ make
/usr/bin/uic-qt4 calccrcdialog.ui -o ui_calccrcdialog.h
/usr/bin/uic-qt4 chooseareadialog.ui -o ui_chooseareadialog.h
/usr/bin/uic-qt4 choosedatadialog.ui -o ui_choosedatadialog.h
/usr/bin/uic-qt4 choosezftabdialog.ui -o ui_choosezftabdialog.h
/usr/bin/uic-qt4 comsetdialog.ui -o ui_comsetdialog.h
/usr/bin/uic-qt4 downloaddialog.ui -o ui_downloaddialog.h
/usr/bin/uic-qt4 grouptestdialog.ui -o ui_grouptestdialog.h
/usr/bin/uic-qt4 inputdialog.ui -o ui_inputdialog.h
/usr/bin/uic-qt4 logindialog.ui -o ui_logindialog.h
/usr/bin/uic-qt4 mainwindow.ui -o ui_mainwindow.h
/usr/bin/uic-qt4 settimedialog.ui -o ui_settimedialog.h
/usr/bin/uic-qt4 transfiledialog.ui -o ui_transfiledialog.h
/usr/bin/uic-qt4 transfiledialog_js.ui -o ui_transfiledialog_js.h
/usr/bin/uic-qt4 uploaddialog.ui -o ui_uploaddialog.h
/usr/bin/uic-qt4 usrmanagedialog.ui -o ui_usrmanagedialog.h
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o addgrptabledelegate.o addgrptabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o calccrcdialog.o calccrcdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o cascadetabledelegate.o cascadetabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o chooseareadialog.o chooseareadialog.cpp
chooseareadialog.cpp:39: warning: unused parameter ‘event’
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o choosedatadialog.o choosedatadialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o choosezftabdialog.o choosezftabdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o comsetdialog.o comsetdialog.cpp
comsetdialog.cpp:22: warning: unused parameter ‘event’
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o downloaddialog.o downloaddialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o eventsortdialog.o eventsortdialog.cpp
eventsortdialog.cpp:13: warning: unused parameter ‘event’
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o grouptestdelegate.o grouptestdelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o grouptestdialog.o grouptestdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o grouptestserver.o grouptestserver.cpp
grouptestserver.cpp:269: warning: unused parameter ‘debugFlag’
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o inputdialog.o inputdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o inputtabledelegate.o inputtabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o jctabledelegate.o jctabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o logindialog.o logindialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o main.o main.cpp
myclient.h:126: warning: ‘SyncChar’ defined but not used
./include/ConstDef.h:81: warning: ‘BitMark’ defined but not used
./include/ConstDef.h:82: warning: ‘BaudRate’ defined but not used
./include/ConstDef.h:131: warning: ‘TaskNameTab’ defined but not used
./include/ConstDef.h:151: warning: ‘TaskVerTab’ defined but not used
./include/ConstDef.h:171: warning: ‘LibNameTab’ defined but not used
./include/ConstDef.h:191: warning: ‘sysVerTab’ defined but not used
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o mainwindow.o mainwindow.cpp
mainwindow.cpp:1350: warning: unused parameter ‘index’
mainwindow.cpp:3004: warning: unused parameter ‘state’
mainwindow.cpp:4213: warning: unused parameter ‘parent’
mainwindow.cpp:4213: warning: unused parameter ‘end’
mainwindow.cpp:4257: warning: unused parameter ‘parent’
mainwindow.cpp:5266: warning: unused parameter ‘zfTabModel’
mainwindow.cpp:5266: warning: unused parameter ‘updateRows’
mainwindow.cpp:5579: warning: unused parameter ‘old’
mainwindow.cpp:5579: warning: unused parameter ‘now’
myclient.h:126: warning: ‘SyncChar’ defined but not used
./include/ConstDef.h:82: warning: ‘BaudRate’ defined but not used
./include/ConstDef.h:131: warning: ‘TaskNameTab’ defined but not used
./include/ConstDef.h:151: warning: ‘TaskVerTab’ defined but not used
./include/ConstDef.h:171: warning: ‘LibNameTab’ defined but not used
./include/ConstDef.h:191: warning: ‘sysVerTab’ defined but not used
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o myclient.o myclient.cpp
myclient.cpp:594: warning: unused parameter ‘paraLen’
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o myfileprocess.o myfileprocess.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o nodetabledelegate.o nodetabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o othertabledelegate.o othertabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o pointtabledelegate.o pointtabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o porttabledelegate.o porttabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o settimedialog.o settimedialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o supporttabledelegate.o supporttabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o transfileclient.o transfileclient.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o transfileclient_js.o transfileclient_js.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o transfiledelegate.o transfiledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o transfiledelegate_js.o transfiledelegate_js.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o transfiledialog.o transfiledialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o transfiledialog_js.o transfiledialog_js.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o transmittabledelegate.o transmittabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o uploaddialog.o uploaddialog.cpp
uploaddialog.cpp:1117: warning: unused parameter ‘buf’
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o usrmanagedialog.o usrmanagedialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o zftabledelegate.o zftabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. addgrptabledelegate.h -o moc_addgrptabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_addgrptabledelegate.o moc_addgrptabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. calccrcdialog.h -o moc_calccrcdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_calccrcdialog.o moc_calccrcdialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. cascadetabledelegate.h -o moc_cascadetabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_cascadetabledelegate.o moc_cascadetabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. chooseareadialog.h -o moc_chooseareadialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_chooseareadialog.o moc_chooseareadialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. choosedatadialog.h -o moc_choosedatadialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_choosedatadialog.o moc_choosedatadialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. choosezftabdialog.h -o moc_choosezftabdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_choosezftabdialog.o moc_choosezftabdialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. comsetdialog.h -o moc_comsetdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_comsetdialog.o moc_comsetdialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. downloaddialog.h -o moc_downloaddialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_downloaddialog.o moc_downloaddialog.cpp
myclient.h:126: warning: ‘SyncChar’ defined but not used
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. eventsortdialog.h -o moc_eventsortdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_eventsortdialog.o moc_eventsortdialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. grouptestdelegate.h -o moc_grouptestdelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_grouptestdelegate.o moc_grouptestdelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. grouptestdialog.h -o moc_grouptestdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_grouptestdialog.o moc_grouptestdialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. grouptestserver.h -o moc_grouptestserver.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_grouptestserver.o moc_grouptestserver.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. inputdialog.h -o moc_inputdialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_inputdialog.o moc_inputdialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. inputtabledelegate.h -o moc_inputtabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_inputtabledelegate.o moc_inputtabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. jctabledelegate.h -o moc_jctabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_jctabledelegate.o moc_jctabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. logindialog.h -o moc_logindialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_logindialog.o moc_logindialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. mainwindow.h -o moc_mainwindow.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_mainwindow.o moc_mainwindow.cpp
myclient.h:126: warning: ‘SyncChar’ defined but not used
./include/ConstDef.h:81: warning: ‘BitMark’ defined but not used
./include/ConstDef.h:82: warning: ‘BaudRate’ defined but not used
./include/ConstDef.h:131: warning: ‘TaskNameTab’ defined but not used
./include/ConstDef.h:151: warning: ‘TaskVerTab’ defined but not used
./include/ConstDef.h:171: warning: ‘LibNameTab’ defined but not used
./include/ConstDef.h:191: warning: ‘sysVerTab’ defined but not used
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. myclient.h -o moc_myclient.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_myclient.o moc_myclient.cpp
myclient.h:126: warning: ‘SyncChar’ defined but not used
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. myfileprocess.h -o moc_myfileprocess.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_myfileprocess.o moc_myfileprocess.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. nodetabledelegate.h -o moc_nodetabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_nodetabledelegate.o moc_nodetabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. othertabledelegate.h -o moc_othertabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_othertabledelegate.o moc_othertabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. pointtabledelegate.h -o moc_pointtabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_pointtabledelegate.o moc_pointtabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. porttabledelegate.h -o moc_porttabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_porttabledelegate.o moc_porttabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. settimedialog.h -o moc_settimedialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_settimedialog.o moc_settimedialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. supporttabledelegate.h -o moc_supporttabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_supporttabledelegate.o moc_supporttabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. transfileclient.h -o moc_transfileclient.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_transfileclient.o moc_transfileclient.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. transfileclient_js.h -o moc_transfileclient_js.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_transfileclient_js.o moc_transfileclient_js.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. transfiledelegate.h -o moc_transfiledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_transfiledelegate.o moc_transfiledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. transfiledelegate_js.h -o moc_transfiledelegate_js.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_transfiledelegate_js.o moc_transfiledelegate_js.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. transfiledialog.h -o moc_transfiledialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_transfiledialog.o moc_transfiledialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. transfiledialog_js.h -o moc_transfiledialog_js.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_transfiledialog_js.o moc_transfiledialog_js.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. transmittabledelegate.h -o moc_transmittabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_transmittabledelegate.o moc_transmittabledelegate.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. uploaddialog.h -o moc_uploaddialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_uploaddialog.o moc_uploaddialog.cpp
myclient.h:126: warning: ‘SyncChar’ defined but not used
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. usrmanagedialog.h -o moc_usrmanagedialog.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_usrmanagedialog.o moc_usrmanagedialog.cpp
/usr/bin/moc-qt4 -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. zftabledelegate.h -o moc_zftabledelegate.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o moc_zftabledelegate.o moc_zftabledelegate.cpp
/usr/bin/rcc -name seatools seatools.qrc -o qrc_seatools.cpp
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Iinclude -I. -I. -o qrc_seatools.o qrc_seatools.cpp
g++ -static -Wl,-O1 -o SeaTools addgrptabledelegate.o calccrcdialog.o cascadetabledelegate.o chooseareadialog.o choosedatadialog.o choosezftabdialog.o comsetdialog.o downloaddialog.o eventsortdialog.o grouptestdelegate.o grouptestdialog.o grouptestserver.o inputdialog.o inputtabledelegate.o jctabledelegate.o logindialog.o main.o mainwindow.o myclient.o myfileprocess.o nodetabledelegate.o othertabledelegate.o pointtabledelegate.o porttabledelegate.o settimedialog.o supporttabledelegate.o transfileclient.o transfileclient_js.o transfiledelegate.o transfiledelegate_js.o transfiledialog.o transfiledialog_js.o transmittabledelegate.o uploaddialog.o usrmanagedialog.o zftabledelegate.o moc_addgrptabledelegate.o moc_calccrcdialog.o moc_cascadetabledelegate.o moc_chooseareadialog.o moc_choosedatadialog.o moc_choosezftabdialog.o moc_comsetdialog.o moc_downloaddialog.o moc_eventsortdialog.o moc_grouptestdelegate.o moc_grouptestdialog.o moc_grouptestserver.o moc_inputdialog.o moc_inputtabledelegate.o moc_jctabledelegate.o moc_logindialog.o moc_mainwindow.o moc_myclient.o moc_myfileprocess.o moc_nodetabledelegate.o moc_othertabledelegate.o moc_pointtabledelegate.o moc_porttabledelegate.o moc_settimedialog.o moc_supporttabledelegate.o moc_transfileclient.o moc_transfileclient_js.o moc_transfiledelegate.o moc_transfiledelegate_js.o moc_transfiledialog.o moc_transfiledialog_js.o moc_transmittabledelegate.o moc_uploaddialog.o moc_usrmanagedialog.o moc_zftabledelegate.o qrc_seatools.o    -L/usr/lib -lQtGui -lQtNetwork -lQtCore -lpthread 
/usr/bin/ld: cannot find -lQtGui
collect2: ld returned 1 exit status
make: *** [SeaTools] Error 1
mike@mike-desktop:/mnt/hgfs/VBox_Shared/SeaTools$ 
```> **11jmb said:**
> Can you share specifics like error messages? Is the project you are trying to compile open-source? If so, what is its name/version?



[http://en.wikipedia.org/wiki/Toolchain](http://en.wikipedia.org/wiki/Toolchain)

---

### Post by Dubslow on 2012-07-02
[http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/)

That's about gcc specifically, but it's also good for compiling and linking in general. (And your case is using g++, which is basically the same as gcc.)

Read the link for more details, but the gist is that gcc/ld couldn't find an external library required by some of your code. Try 'find / -name QtGui.a', and then read the link to figure out how to use that information.

---

### Post by Zugzwang on 2012-07-03
> **pellyhawk said:**
> By the way, what is tool chain?


11jmb provided you with a link already. Did you read it?

Note that "c/c++, java, python" is a strange answer to the questions what language you are trying to compile for, as python for example isn't compiled, so the question makes no sense.

In C/C++, compilation works totally different as in Java, so there is no common answer, and in both cases, there are different tool chains available, which again make a difference. In the example you provided, you appear to be compiling a QT application. Typically, you use "qmake" as the make system, which is part of your tool chain. There is either an error in your QMake project file or you simply didn't install the necessary packages. Could you post your qmake project file nere? Perhaps it suffices to remove the requirement that the program should be statically linked.

---

### Post by pellyhawk on 2012-07-03
Thank you all.

I have read [http://en.wikipedia.org/wiki/Toolchain](http://en.wikipedia.org/wiki/Toolchain) and know about toolchain. It seems GCC (GNU Compiler Connection) is a tool chain which includes gcc, g++, editor, linker and other tools. Is it right?

> **Zugzwang said:**
> 
Note that "c/c++, java, python" is a strange answer to the questions what language you are trying to compile for, as python for example isn't compiled, so the question makes no sense. Soon I will undertake a project which is divided into many modules. Some of them are implemented by C/C++, some are Java. We will also use python. Now I am coding by C/C++ and met some compilation issue. So I wish learn some compilation knowledge and prepared for C/C++, Java and Python.

> In C/C++, compilation works totally different as in Java, so there is no common answer, and in both cases, there are different tool chains available, which again make a difference. In the example you provided, you appear to be compiling a QT application. Typically, you use "qmake" as the make system, which is part of your tool chain. There is either an error in your QMake project file or you simply didn't install the necessary packages. Could you post your qmake project file nere? Perhaps it suffices to remove the requirement that the program should be statically linked.
I am statically compiling the project. By googling, someone told me add "CONFIG += static" in .pro file; others told me add "QMAKE_LFLAGS += -static" in .pro file; another one told me insert "-static" after "CXXFLAGS = " in Makefile. There are totally 3 ideas. I do not know which one is right, and will these 3 ideas conflict? 

Therefore I have to hope computer guru can tole me how to deal with these 3 idea and recommend me some reading materials about C/C++, Java and Python.

You told me "you use "qmake" as the make system, which is part of your tool chain." Do you mean "qmake" is part of GCC tool chain? Or "make" is part of GCC tool chain? 

Here is my .pro file> ######################################################################
# Automatically generated by qmake (2.01a) Mon Jul 2 23:36:04 2012
######################################################################

TEMPLATE = app
TARGET = 
DEPENDPATH += . debug include release translations
INCLUDEPATH += . include
QT           += network

# Input
HEADERS += addgrptabledelegate.h \
           calccrcdialog.h \
           cascadetabledelegate.h \
           chooseareadialog.h \
           choosedatadialog.h \
           choosezftabdialog.h \
           comsetdialog.h \
           dlt698_protocol.h \
           downloaddialog.h \
           eventsortdialog.h \
           grouptestdelegate.h \
           grouptestdialog.h \
           grouptestserver.h \
           inputdialog.h \
           inputtabledelegate.h \
           jctabledelegate.h \
           logindialog.h \
           mainwindow.h \
           myclient.h \
           myfileprocess.h \
           nodetabledelegate.h \
           othertabledelegate.h \
           pointtabledelegate.h \
           porttabledelegate.h \
           settimedialog.h \
           supporttabledelegate.h \
           transfileclient.h \
           transfileclient_js.h \
           transfiledelegate.h \
           transfiledelegate_js.h \
           transfiledialog.h \
           transfiledialog_js.h \
           transmittabledelegate.h \
           ui_eventsortdialog.h \
           ui_remoteupdatedialog.h \
           uploaddialog.h \
           usrmanagedialog.h \
           zftabledelegate.h \
           include/ConfigrationPara.h \
           include/ConstDef.h \
           include/RunningPara.h \
           include/SystemPara.h
FORMS += calccrcdialog.ui \
         chooseareadialog.ui \
         choosedatadialog.ui \
         choosezftabdialog.ui \
         comsetdialog.ui \
         downloaddialog.ui \
         grouptestdialog.ui \
         inputdialog.ui \
         logindialog.ui \
         mainwindow.ui \
         settimedialog.ui \
         transfiledialog.ui \
         transfiledialog_js.ui \
         uploaddialog.ui \
         usrmanagedialog.ui
SOURCES += addgrptabledelegate.cpp \
           calccrcdialog.cpp \
           cascadetabledelegate.cpp \
           chooseareadialog.cpp \
           choosedatadialog.cpp \
           choosezftabdialog.cpp \
           comsetdialog.cpp \
           downloaddialog.cpp \
           eventsortdialog.cpp \
           grouptestdelegate.cpp \
           grouptestdialog.cpp \
           grouptestserver.cpp \
           inputdialog.cpp \
           inputtabledelegate.cpp \
           jctabledelegate.cpp \
           logindialog.cpp \
           main.cpp \
           mainwindow.cpp \
           myclient.cpp \
           myfileprocess.cpp \
           nodetabledelegate.cpp \
           othertabledelegate.cpp \
           pointtabledelegate.cpp \
           porttabledelegate.cpp \
           settimedialog.cpp \
           supporttabledelegate.cpp \
           transfileclient.cpp \
           transfileclient_js.cpp \
           transfiledelegate.cpp \
           transfiledelegate_js.cpp \
           transfiledialog.cpp \
           transfiledialog_js.cpp \
           transmittabledelegate.cpp \
           uploaddialog.cpp \
           usrmanagedialog.cpp \
           zftabledelegate.cpp
RESOURCES += seatools.qrc
TRANSLATIONS += translations/nsctools_zh_CN.ts

---

### Post by pellyhawk on 2012-07-03
> **Dubslow said:**
> [http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/)

That's about gcc specifically, but it's also good for compiling and linking in general. (And your case is using g++, which is basically the same as gcc.)

Read the link for more details, but the gist is that gcc/ld couldn't find an external library required by some of your code. Try 'find / -name QtGui.a', and then read the link to figure out how to use that information.
thanks for the link you provided and it is very useful

---

### Post by 11jmb on 2012-07-03
> **pellyhawk said:**
> It seems GCC (GNU Compiler Connection) is a tool chain which includes gcc, g++, editor, linker and other tools. Is it right?


Close, but not entirely. When you run gcc, the steps that are actually run are: preprocessor, compiler, assembler, archiver (sometimes), and linker.

The preprocessor handles directives like #include, #define, #ifndef, and (as an oversimplification) performs text copying and pasting as specified by these directives. The compiler translates the preprocessed source files into assembly code. The assembler translates the assembly code into machine code, also known as object files. The archiver, if invoked, will create libraries. The linker will generate executables

You can use command line arguments to stop the process during any intermediate step.

g++ is simply a frontend to gcc to make compiling c++ projects easier.

---

### Post by HappyHoward on 2012-07-04
I think the problem is that you try to link Qt statically. As someone else said before search for QtGui.a. If you can't find it and absolutely must link statically you'll have to build Qt for static linking your self.

I can't help you with paths to QtGui, since im at work with a Windows machine right now.

Edit: I should also add that since you're probably using the free LGPL version of Qt, there are some legal issues to think about.
Read [http://stackoverflow.com/questions/2277165/qt-single-exe-with-lgpl](http://stackoverflow.com/questions/2277165/qt-single-exe-with-lgpl)
That question is from a Windows user but it's the same rules on Linux.

---

### Post by pellyhawk on 2012-07-04
> **HappyHoward said:**
> I think the problem is that you try to link Qt statically. As someone else said before search for QtGui.a. If you can't find it and absolutely must link statically you'll have to build Qt for static linking your self.

I can't help you with paths to QtGui, since im at work with a Windows machine right now.

Edit: I should also add that since you're probably using the free LGPL version of Qt, there are some legal issues to think about.
Read [http://stackoverflow.com/questions/2277165/qt-single-exe-with-lgpl](http://stackoverflow.com/questions/2277165/qt-single-exe-with-lgpl)
That question is from a Windows user but it's the same rules on Linux.

Yes, I am trying to compile my project statically, and I have already built Qt statically.

---

