---
title: "How do you compile source code (sleepyhead src from Sourceforge)?"
date: 2012-03-10
forum: Packaging and Compiling Programs
---

### Post by rocksockdoc on 2012-03-10
I've never compiled before.
I tried the following to [compile SleepyHead from SourceForge bulld instructions]("http://sourceforge.net/apps/mediawiki/sleepyhead/index.php?title=Build_from_source") but failed miserably on Ubuntu 10.04. 

**Request:[COLOR=DarkRed] If you're on Ubuntu 10.04, can you just tell me (yay or nay) if this works for you to install sleepyhead?[/COLOR]**

0. Read about SleepyHead open-source freeware from the [SleepyHead Web Site]("http://sleepyhead.sourceforge.net/").

1. Install the GIT program so as to be able to 'git' the source code:
$ sudo apt-get install git-core 

2. Download the source code using that newly installed GIT protocol:
$ git clone  git://sleepyhead.git.sourceforge.net/gitroot/sleepyhead/sleepyhead 

3. Install QT development tools, if needed: 
$ sudo apt-get install qt4-dev-tools libqt4-opengl-dev 

4. Run the make command (that's all it says in the README): 
qmake 
make

Does it work for you?
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214050&stc=1&d=1331389855[/IMG]

It didn't work for me:
- [**Tutorial for installing SourceForge SleepyHead CPAP/BiPAP (Sleep Apnea) software**]("http://ubuntuforums.org/showthread.php?t=1937358")

PS: The *.deb is already known to fail on Ubuntu 10.04, which it predictably did.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214051&stc=1&d=1331389852[/IMG]

---

### Post by oldos2er on 2012-03-10
Moved to Packaging and Compiling Programs.

---

### Post by MadCow108 on 2012-03-10
what error do you get?

it works fine in lucid setup, the only thing missing from the instructions is *apt-get install zlib1g-dev* for zlib.h

---

### Post by rocksockdoc on 2012-03-11
> **MadCow108 said:**
> it works fine in lucid setup, the only thing missing from the instructions is *apt-get install zlib1g-dev* for zlib.h

Thank you very much to taking the time to help me out! 
(I realize you don't have to help me!)

I have never compiled before so I'm at a disadvantage when it comes to figuring out what I need. 

I am most concerned that others (who need this type of medical software!) on Ubuntu Lucid 10.04 can more easily compile the program, so, would you please take a look at these commands below to say if that's what you ran to install on Lucid 10.04? 

Below is my take on [the developer's instructions]("http://sourceforge.net/apps/mediawiki/sleepyhead/index.php?title=Main_Page") from a page called [Building From Source Code]("http://sourceforge.net/apps/mediawiki/sleepyhead/index.php?title=Build_from_source") for Ubuntu 10.04 which references this "[Build From Source]("http://sourceforge.net/apps/mediawiki/sleepyhead/index.php?title=Build_from_source")" web page (with your hint above added):
```

1. Install C++ development tools and the GIT client:
$ sudo apt-get install git-core qt4-dev-tools libqt4-opengl-dev libqtwebkit-dev zlib1g-dev 

2. Obtain SleepyHead source code:
$ git clone git://sleepyhead.git.sourceforge.net/gitroot/sleepyhead/sleepyhead

3. Create a Makefile in the local directory:
$ qmake

4. Create the "SleepyHead" executable:
$ make

5. Run the SleepyHead software:
$ ./SleepyHead

```How does that look for easy instructions for Ubuntu Lucid 10.04 users?

> **MadCow108 said:**
> what error do you get?

You don't really want to know! 
I get VERY MANY errors & warnings when I run 'make'.
```

$ make
Makefile:1856: warning: overriding commands for target `moc_daily.cpp'
Makefile:1820: warning: ignoring old commands for target `moc_daily.cpp'
Makefile:1859: warning: overriding commands for target `moc_overview.cpp'
Makefile:1823: warning: ignoring old commands for target `moc_overview.cpp'
Makefile:1862: warning: overriding commands for target `moc_mainwindow.cpp'
Makefile:1826: warning: ignoring old commands for target `moc_mainwindow.cpp'
Makefile:1865: warning: overriding commands for target `moc_oximetry.cpp'
Makefile:1817: warning: ignoring old commands for target `moc_oximetry.cpp'
Makefile:1868: warning: overriding commands for target `moc_preferencesdialog.cpp'
Makefile:1835: warning: ignoring old commands for target `moc_preferencesdialog.cpp'
Makefile:1874: warning: overriding commands for target `moc_profileselect.cpp'
Makefile:1841: warning: ignoring old commands for target `moc_profileselect.cpp'
Makefile:1877: warning: overriding commands for target `moc_newprofile.cpp'
Makefile:1844: warning: ignoring old commands for target `moc_newprofile.cpp'
Makefile:1880: warning: overriding commands for target `moc_exportcsv.cpp'
Makefile:1847: warning: ignoring old commands for target `moc_exportcsv.cpp'
Makefile:1883: warning: overriding commands for target `moc_UpdaterWindow.cpp'
Makefile:1853: warning: ignoring old commands for target `moc_UpdaterWindow.cpp'
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DGIT_BRANCH=\\\"master -D\\\" -DGIT_REVISION=\\\"c7b66c52671a1a487580392eaa5b1d56647bd48e -D\\\" -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -o main.o main.cpp
<command-line>: warning: missing terminating " character
<command-line>: error: macro names must be identifiers
<command-line>: warning: missing terminating " character
<command-line>: warning: missing terminating " character
<command-line>: error: macro names must be identifiers
<command-line>: warning: missing terminating " character
main.cpp:8:30: error: QtGui/QApplication: No such file or directory
main.cpp:9:23: error: QMessageBox: No such file or directory
main.cpp:10:25: error: QFontDatabase: No such file or directory
main.cpp:11:23: error: QStringList: No such file or directory
main.cpp:12:18: error: QDebug: No such file or directory
main.cpp:13:23: error: QPushButton: No such file or directory
main.cpp:14:21: error: QWebFrame: No such file or directory
main.cpp:15:20: error: QWebView: No such file or directory
In file included from main.cpp:17:
SleepLib/schema.h:10:18: error: QColor: No such file or directory
SleepLib/schema.h:11:17: error: QHash: No such file or directory
SleepLib/schema.h:12:20: error: QVariant: No such file or directory
SleepLib/schema.h:13:19: error: QString: No such file or directory
In file included from SleepLib/schema.h:14,
                 from main.cpp:17:
SleepLib/machine_common.h:12:19: error: QVector: No such file or directory
In file included from main.cpp:18:
mainwindow.h:10:23: error: QMainWindow: No such file or directory
mainwindow.h:11:22: error: QGLContext: No such file or directory
mainwindow.h:12:33: error: QNetworkAccessManager: No such file or directory
mainwindow.h:13:25: error: QNetworkReply: No such file or directory
mainwindow.h:14:27: error: QSystemTrayIcon: No such file or directory
In file included from mainwindow.h:17,
                 from main.cpp:18:
daily.h:11:17: error: QMenu: No such file or directory
daily.h:12:19: error: QAction: No such file or directory
daily.h:13:19: error: QWidget: No such file or directory
daily.h:14:23: error: QTreeWidget: No such file or directory
daily.h:15:23: error: QHBoxLayout: No such file or directory
daily.h:17:18: error: QLabel: No such file or directory
daily.h:18:31: error: QtOpenGL/QGLContext: No such file or directory
daily.h:19:22: error: QScrollBar: No such file or directory
daily.h:20:28: error: QTableWidgetItem: No such file or directory
In file included from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/profiles.h:14:30: error: QCryptographicHash: No such file or directory
./SleepLib/profiles.h:15:19: error: QThread: No such file or directory
In file included from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/machine.h:13:21: error: QDateTime: No such file or directory
./SleepLib/machine.h:15:18: error: QMutex: No such file or directory
./SleepLib/machine.h:16:22: error: QSemaphore: No such file or directory
In file included from ./SleepLib/machine.h:22,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/preferences.h:16:23: error: QDomElement: No such file or directory
./SleepLib/preferences.h:17:24: error: QDomDocument: No such file or directory
In file included from ./SleepLib/day.h:10,
                 from ./SleepLib/machine.h:28,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/common.h:5:19: error: QObject: No such file or directory
./SleepLib/common.h:7:35: error: missing binary operator before token "("
In file included from Graphs/gSummaryChart.h:11,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gGraphView.h:10:21: error: QGLWidget: No such file or directory
Graphs/gGraphView.h:12:24: error: QResizeEvent: No such file or directory
Graphs/gGraphView.h:17:26: error: QWaitCondition: No such file or directory
Graphs/gGraphView.h:18:19: error: QPixmap: No such file or directory
In file included from Graphs/gGraphView.h:19,
                 from Graphs/gSummaryChart.h:11,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./Graphs/glcommon.h:10:26: error: QtOpenGL/qgl.h: No such file or directory
In file included from mainwindow.h:18,
                 from main.cpp:18:
overview.h:13:21: error: QDateEdit: No such file or directory
In file included from mainwindow.h:19,
                 from main.cpp:18:
oximetry.h:13:21: error: QSplitter: No such file or directory
In file included from ./qextserialport/qextserialport.h:5,
                 from oximetry.h:14,
                 from mainwindow.h:19,
                 from main.cpp:18:
./qextserialport/qextserialport_global.h:6:28: error: QtCore/qglobal.h: No such file or directory
In file included from oximetry.h:14,
                 from mainwindow.h:19,
                 from main.cpp:18:
./qextserialport/qextserialport.h:123:21: error: QIODevice: No such file or directory
./qextserialport/qextserialport.h:133:27: error: QSocketNotifier: No such file or directory
In file included from mainwindow.h:20,
                 from main.cpp:18:
preferencesdialog.h:10:19: error: QDialog: No such file or directory
preferencesdialog.h:11:23: error: QModelIndex: No such file or directory
preferencesdialog.h:12:27: error: QListWidgetItem: No such file or directory
preferencesdialog.h:13:28: error: QStringListModel: No such file or directory
preferencesdialog.h:14:33: error: QSortFilterProxyModel: No such file or directory
preferencesdialog.h:15:30: error: QStandardItemModel: No such file or directory
In file included from main.cpp:29:
SleepLib/loader_plugins/icon_loader.h:14:21: error: QMultiMap: No such file or directory
In file included from SleepLib/schema.h:14,
                 from main.cpp:17:
SleepLib/machine_common.h:19: error: &#8216;quint32&#8217; does not name a type
SleepLib/machine_common.h:23: error: &#8216;qint16&#8217; does not name a type
SleepLib/machine_common.h:31: error: &#8216;quint32&#8217; does not name a type
SleepLib/machine_common.h:37: error: &#8216;qint64&#8217; does not name a type
In file included from SleepLib/schema.h:14,
                 from main.cpp:17:
SleepLib/machine_common.h:86: error: &#8216;ChannelID&#8217; does not name a type
SleepLib/machine_common.h:87: error: &#8216;ChannelID&#8217; does not name a type
SleepLib/machine_common.h:96: error: &#8216;ChannelID&#8217; does not name a type
SleepLib/machine_common.h:97: error: &#8216;ChannelID&#8217; does not name a type
SleepLib/machine_common.h:98: error: &#8216;ChannelID&#8217; does not name a type
SleepLib/machine_common.h:102: error: &#8216;ChannelID&#8217; does not name a type
SleepLib/machine_common.h:104: error: &#8216;ChannelID&#8217; does not name a type
SleepLib/machine_common.h:106: error: &#8216;ChannelID&#8217; does not name a type
SleepLib/machine_common.h:108: error: &#8216;ChannelID&#8217; does not name a type
In file included from main.cpp:17:
SleepLib/schema.h:17: error: &#8216;quint32&#8217; does not name a type
SleepLib/schema.h:18: error: &#8216;quint32&#8217; does not name a type
SleepLib/schema.h:19: error: &#8216;quint32&#8217; does not name a type
SleepLib/schema.h:20: error: &#8216;quint32&#8217; does not name a type
SleepLib/schema.h:21: error: &#8216;quint32&#8217; does not name a type
SleepLib/schema.h:22: error: &#8216;quint32&#8217; does not name a type
SleepLib/schema.h:51: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:51: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:51: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:51: error: &#8216;QString&#8217; has not been declared
In file included from main.cpp:17:
SleepLib/schema.h:51: error: &#8216;QColor&#8217; has not been declared
SleepLib/schema.h:52: error: &#8216;QColor&#8217; has not been declared
SleepLib/schema.h:53: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:57: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
SleepLib/schema.h:57: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
SleepLib/schema.h:58: error: expected &#8216;;&#8217; before &#8216;const&#8217;
SleepLib/schema.h:58: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
SleepLib/schema.h:58: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
SleepLib/schema.h:59: error: expected &#8216;;&#8217; before &#8216;const&#8217;
SleepLib/schema.h:59: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
SleepLib/schema.h:59: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
SleepLib/schema.h:60: error: expected &#8216;;&#8217; before &#8216;const&#8217;
SleepLib/schema.h:60: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
SleepLib/schema.h:60: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
SleepLib/schema.h:62: error: expected &#8216;;&#8217; before &#8216;void&#8217;
SleepLib/schema.h:62: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:63: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:64: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:65: error: &#8216;QString&#8217; does not name a type
SleepLib/schema.h:70: error: ISO C++ forbids declaration of &#8216;QColor&#8217; with no type
SleepLib/schema.h:70: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
SleepLib/schema.h:71: error: expected &#8216;;&#8217; before &#8216;void&#8217;
SleepLib/schema.h:71: error: &#8216;QColor&#8217; has not been declared
SleepLib/schema.h:72: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
SleepLib/schema.h:72: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
SleepLib/schema.h:73: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
SleepLib/schema.h:73: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
SleepLib/schema.h:74: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
SleepLib/schema.h:74: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
SleepLib/schema.h:80: error: &#8216;QString&#8217; does not name a type
SleepLib/schema.h:81: error: &#8216;QString&#8217; does not name a type
SleepLib/schema.h:82: error: &#8216;QString&#8217; does not name a type
SleepLib/schema.h:83: error: &#8216;QString&#8217; does not name a type
SleepLib/schema.h:85: error: &#8216;QColor&#8217; does not name a type
SleepLib/schema.h:51: error: &#8216;Qt&#8217; has not been declared
SleepLib/schema.h: In member function &#8216;void schema::Channel::addColor(schema::Function, int)&#8217;:
SleepLib/schema.h:52: error: &#8216;m_colors&#8217; was not declared in this scope
SleepLib/schema.h: In member function &#8216;void schema::Channel::addOption(int, int)&#8217;:
SleepLib/schema.h:53: error: &#8216;m_options&#8217; was not declared in this scope
SleepLib/schema.h: In member function &#8216;void schema::Channel::setLabel(int)&#8217;:
SleepLib/schema.h:62: error: &#8216;m_label&#8217; was not declared in this scope
SleepLib/schema.h: In member function &#8216;void schema::Channel::setUnit(int)&#8217;:
SleepLib/schema.h:63: error: &#8216;m_unit&#8217; was not declared in this scope
SleepLib/schema.h: In member function &#8216;void schema::Channel::setDescription(int)&#8217;:
SleepLib/schema.h:64: error: &#8216;m_description&#8217; was not declared in this scope
SleepLib/schema.h: In member function &#8216;void schema::Channel::setDefaultColor(int)&#8217;:
SleepLib/schema.h:71: error: &#8216;m_defaultcolor&#8217; was not declared in this scope
SleepLib/schema.h: At global scope:
SleepLib/schema.h:100: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:103: error: &#8216;QString&#8217; has not been declared
SleepLib/schema.h:106: error: declaration of &#8216;operator[]&#8217; as non-function
SleepLib/schema.h:106: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
SleepLib/schema.h:113: error: expected &#8216;;&#8217; before &#8216;Channel&#8217;
SleepLib/schema.h:113: error: declaration of &#8216;operator[]&#8217; as non-function
SleepLib/schema.h:113: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
SleepLib/schema.h:121: error: expected &#8216;;&#8217; before &#8216;QHash&#8217;
SleepLib/schema.h:121: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
SleepLib/schema.h:121: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
SleepLib/schema.h:124: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
SleepLib/schema.h:124: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
SleepLib/schema.h:127: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
SleepLib/schema.h:127: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
SleepLib/schema.h:128: error: &#8216;QString&#8217; does not name a type
In file included from mainwindow.h:16,
                 from main.cpp:18:
version.h:11: error: &#8216;QString&#8217; does not name a type
version.h:12: error: &#8216;QString&#8217; does not name a type
version.h:14: error: &#8216;QString&#8217; does not name a type
version.h:21: error: &#8216;QString&#8217; does not name a type
In file included from ./SleepLib/machine.h:22,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/preferences.h:21: error: &#8216;QString&#8217; does not name a type
./SleepLib/preferences.h:22: error: &#8216;QString&#8217; does not name a type
./SleepLib/preferences.h:24: error: expected initializer before &#8216;&&#8217; token
./SleepLib/preferences.h:26: error: &#8216;QString&#8217; does not name a type
./SleepLib/preferences.h:32: error: expected initializer before &#8216;&&#8217; token
./SleepLib/preferences.h:43: error: expected &#8216;)&#8217; before &#8216;name&#8217;
./SleepLib/preferences.h:48: error: &#8216;QString&#8217; does not name a type
In file included from ./SleepLib/machine.h:22,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/preferences.h:51: error: ISO C++ forbids declaration of &#8216;QVariant&#8217; with no type
./SleepLib/preferences.h:51: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SleepLib/preferences.h:56: error: expected &#8216;;&#8217; before &#8216;void&#8217;
./SleepLib/preferences.h:56: error: &#8216;QString&#8217; has not been declared
./SleepLib/preferences.h:56: error: &#8216;QVariant&#8217; has not been declared
./SleepLib/preferences.h:61: error: &#8216;QString&#8217; has not been declared
./SleepLib/preferences.h:66: error: &#8216;QString&#8217; has not been declared
./SleepLib/preferences.h:73: error: &#8216;QString&#8217; has not been declared
./SleepLib/preferences.h:80: error: &#8216;QDomElement&#8217; has not been declared
./SleepLib/preferences.h:84: error: &#8216;QDomElement&#8217; does not name a type
./SleepLib/preferences.h:89: error: &#8216;QString&#8217; has not been declared
./SleepLib/preferences.h:94: error: &#8216;QString&#8217; has not been declared
./SleepLib/preferences.h:97: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
./SleepLib/preferences.h:97: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
./SleepLib/preferences.h:103: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/preferences.h:103: error: &#8216;QHash&#8217; declared as an &#8216;inline&#8217; field
./SleepLib/preferences.h:103: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/preferences.h:106: error: expected &#8216;;&#8217; before &#8216;inline&#8217;
./SleepLib/preferences.h:106: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/preferences.h:106: error: &#8216;QHash&#8217; declared as an &#8216;inline&#8217; field
./SleepLib/preferences.h:106: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/preferences.h:109: error: expected &#8216;;&#8217; before &#8216;inline&#8217;
./SleepLib/preferences.h:109: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/preferences.h:109: error: &#8216;QHash&#8217; declared as an &#8216;inline&#8217; field
./SleepLib/preferences.h:109: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/preferences.h:114: error: expected &#8216;;&#8217; before &#8216;QHash&#8217;
./SleepLib/preferences.h:114: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/preferences.h:114: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/preferences.h:118: error: &#8216;QString&#8217; does not name a type
./SleepLib/preferences.h:119: error: &#8216;QString&#8217; does not name a type
./SleepLib/preferences.h:120: error: &#8216;QString&#8217; does not name a type
./SleepLib/preferences.h:121: error: &#8216;QString&#8217; does not name a type
./SleepLib/preferences.h:89: error: default argument for parameter of type &#8216;int&#8217; has type &#8216;const char [1]&#8217;
./SleepLib/preferences.h:94: error: default argument for parameter of type &#8216;int&#8217; has type &#8216;const char [1]&#8217;
./SleepLib/preferences.h: In member function &#8216;void Preferences::Set(int, int)&#8217;:
./SleepLib/preferences.h:57: error: &#8216;p_preferences&#8217; was not declared in this scope
./SleepLib/preferences.h: In member function &#8216;bool Preferences::contains(int)&#8217;:
./SleepLib/preferences.h:62: error: &#8216;p_preferences&#8217; was not declared in this scope
./SleepLib/preferences.h: In member function &#8216;bool Preferences::ExistsAndTrue(int)&#8217;:
./SleepLib/preferences.h:67: error: &#8216;QHash&#8217; was not declared in this scope
./SleepLib/preferences.h:67: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/preferences.h:67: error: &#8216;QVariant&#8217; was not declared in this scope
./SleepLib/preferences.h:67: error: missing template arguments before &#8216;i&#8217;
./SleepLib/preferences.h:67: error: expected &#8216;;&#8217; before &#8216;i&#8217;
./SleepLib/preferences.h:68: error: &#8216;i&#8217; was not declared in this scope
./SleepLib/preferences.h:68: error: &#8216;p_preferences&#8217; was not declared in this scope
./SleepLib/preferences.h:69: error: &#8216;i&#8217; was not declared in this scope
./SleepLib/preferences.h: At global scope:
./SleepLib/preferences.h:66: warning: unused parameter &#8216;name&#8217;
./SleepLib/preferences.h: In member function &#8216;void Preferences::Erase(int)&#8217;:
./SleepLib/preferences.h:74: error: &#8216;QHash&#8217; was not declared in this scope
./SleepLib/preferences.h:74: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/preferences.h:74: error: &#8216;QVariant&#8217; was not declared in this scope
./SleepLib/preferences.h:74: error: missing template arguments before &#8216;i&#8217;
./SleepLib/preferences.h:74: error: expected &#8216;;&#8217; before &#8216;i&#8217;
./SleepLib/preferences.h:75: error: &#8216;i&#8217; was not declared in this scope
./SleepLib/preferences.h:75: error: &#8216;p_preferences&#8217; was not declared in this scope
./SleepLib/preferences.h: At global scope:
./SleepLib/preferences.h:73: warning: unused parameter &#8216;name&#8217;
./SleepLib/preferences.h: In member function &#8216;void Preferences::SetComment(int)&#8217;:
./SleepLib/preferences.h:98: error: &#8216;p_comment&#8217; was not declared in this scope
./SleepLib/preferences.h:98: error: &#8216;str&#8217; was not declared in this scope
./SleepLib/preferences.h: At global scope:
./SleepLib/preferences.h:97: warning: unused parameter &#8216;QString&#8217;
In file included from ./SleepLib/machine.h:25,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/event.h:30: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:30: error: &#8216;EventStoreType&#8217; has not been declared
./SleepLib/event.h:31: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:31: error: &#8216;EventStoreType&#8217; has not been declared
./SleepLib/event.h:31: error: &#8216;EventStoreType&#8217; has not been declared
./SleepLib/event.h:32: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:32: error: &#8216;qint16&#8217; has not been declared
./SleepLib/event.h:32: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:33: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:33: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:34: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:34: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:37: error: ISO C++ forbids declaration of &#8216;quint32&#8217; with no type
./SleepLib/event.h:37: error: &#8216;quint32&#8217; declared as an &#8216;inline&#8217; field
./SleepLib/event.h:37: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SleepLib/event.h:40: error: expected &#8216;;&#8217; before &#8216;void&#8217;
./SleepLib/event.h:40: error: &#8216;quint32&#8217; has not been declared
./SleepLib/event.h:43: error: &#8216;EventStoreType&#8217; does not name a type
./SleepLib/event.h:46: error: &#8216;EventStoreType&#8217; does not name a type
./SleepLib/event.h:49: error: &#8216;quint32&#8217; has not been declared
./SleepLib/event.h:52: error: &#8216;quint32&#8217; has not been declared
./SleepLib/event.h:55: error: &#8216;qint64&#8217; does not name a type
./SleepLib/event.h:61: error: ISO C++ forbids declaration of &#8216;qint64&#8217; with no type
./SleepLib/event.h:61: error: &#8216;qint64&#8217; declared as an &#8216;inline&#8217; field
./SleepLib/event.h:61: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SleepLib/event.h:64: error: expected &#8216;;&#8217; before &#8216;inline&#8217;
./SleepLib/event.h:64: error: ISO C++ forbids declaration of &#8216;qint64&#8217; with no type
./SleepLib/event.h:64: error: &#8216;qint64&#8217; declared as an &#8216;inline&#8217; field
./SleepLib/event.h:64: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SleepLib/event.h:67: error: expected &#8216;;&#8217; before &#8216;inline&#8217;
./SleepLib/event.h:67: error: &#8216;qint64&#8217; does not name a type
./SleepLib/event.h:70: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:72: error: &#8216;qint64&#8217; has not been declared
./SleepLib/event.h:129: error: &#8216;QString&#8217; does not name a type
./SleepLib/event.h:132: error: &#8216;QString&#8217; has not been declared
./SleepLib/event.h:135: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/event.h:135: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/event.h:138: error: expected &#8216;;&#8217; before &#8216;QVector&#8217;
./SleepLib/event.h:138: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/event.h:138: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/event.h:141: error: expected &#8216;;&#8217; before &#8216;QVector&#8217;
./SleepLib/event.h:141: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/event.h:141: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/event.h:144: error: expected &#8216;;&#8217; before &#8216;void&#8217;
./SleepLib/event.h:144: error: &#8216;quint32&#8217; has not been declared
./SleepLib/event.h:145: error: &#8216;quint32&#8217; has not been declared
./SleepLib/event.h:146: error: &#8216;quint32&#8217; has not been declared
./SleepLib/event.h:147: error: ISO C++ forbids declaration of &#8216;EventStoreType&#8217; with no type
./SleepLib/event.h:147: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./SleepLib/event.h:148: error: expected &#8216;;&#8217; before &#8216;EventStoreType&#8217;
./SleepLib/event.h:148: error: ISO C++ forbids declaration of &#8216;EventStoreType&#8217; with no type
./SleepLib/event.h:148: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./SleepLib/event.h:149: error: expected &#8216;;&#8217; before &#8216;quint32&#8217;
./SleepLib/event.h:149: error: ISO C++ forbids declaration of &#8216;quint32&#8217; with no type
./SleepLib/event.h:149: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./SleepLib/event.h:150: error: expected &#8216;;&#8217; before &#8216;protected&#8217;
./SleepLib/event.h:153: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/event.h:153: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/event.h:156: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/event.h:156: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/event.h:159: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/event.h:159: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/event.h:166: error: &#8216;quint32&#8217; does not name a type
./SleepLib/event.h:174: error: &#8216;QString&#8217; does not name a type
./SleepLib/event.h:176: error: &#8216;qint64&#8217; does not name a type
./SleepLib/event.h: In member function &#8216;void EventList::setCount(int)&#8217;:
./SleepLib/event.h:40: error: &#8216;m_count&#8217; was not declared in this scope
./SleepLib/event.h: In member function &#8216;void EventList::setFirst(int)&#8217;:
./SleepLib/event.h:70: error: &#8216;m_first&#8217; was not declared in this scope
./SleepLib/event.h: In member function &#8216;void EventList::setLast(int)&#8217;:
./SleepLib/event.h:72: error: &#8216;m_last&#8217; was not declared in this scope
./SleepLib/event.h: In member function &#8216;void EventList::setDimension(int)&#8217;:
./SleepLib/event.h:132: error: &#8216;m_dimension&#8217; was not declared in this scope
./SleepLib/event.h: In member function &#8216;void EventList::rawDataResize(int)&#8217;:
./SleepLib/event.h:144: error: &#8216;m_data&#8217; was not declared in this scope
./SleepLib/event.h:144: error: &#8216;m_count&#8217; was not declared in this scope
./SleepLib/event.h: In member function &#8216;void EventList::rawData2Resize(int)&#8217;:
./SleepLib/event.h:145: error: &#8216;m_data2&#8217; was not declared in this scope
./SleepLib/event.h:145: error: &#8216;m_count&#8217; was not declared in this scope
./SleepLib/event.h: In member function &#8216;void EventList::rawTimeResize(int)&#8217;:
./SleepLib/event.h:146: error: &#8216;m_time&#8217; was not declared in this scope
./SleepLib/event.h:146: error: &#8216;m_count&#8217; was not declared in this scope
In file included from ./SleepLib/machine.h:26,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/session.h: At global scope:
./SleepLib/session.h:37: error: &#8216;QString&#8217; has not been declared
./SleepLib/session.h:40: error: &#8216;QString&#8217; has not been declared
./SleepLib/session.h:43: error: &#8216;QString&#8217; has not been declared
./SleepLib/session.h:48: error: &#8216;QString&#8217; has not been declared
./SleepLib/session.h:51: error: &#8216;QString&#8217; has not been declared
./SleepLib/session.h:60: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:60: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:60: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:74: error: &#8216;qint64&#8217; does not name a type
./SleepLib/session.h:77: error: &#8216;qint64&#8217; does not name a type
./SleepLib/session.h:80: error: &#8216;qint64&#8217; does not name a type
./SleepLib/session.h:90: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:93: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:96: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:98: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:102: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:129: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:129: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:132: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:132: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:135: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:135: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:136: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:136: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:137: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:137: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:138: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:138: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:139: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:139: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:140: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:140: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:141: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:141: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:142: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:142: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:143: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:143: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:144: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:144: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:146: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:146: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:147: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:147: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:148: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/session.h:148: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/session.h:151: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:154: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:157: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:158: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:159: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:160: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:161: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:162: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:166: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:167: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:168: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:168: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:169: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:169: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:171: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:174: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:174: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:174: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:177: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:177: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:177: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:180: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:180: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:180: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:183: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:183: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:183: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:187: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:190: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:193: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:196: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:199: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:202: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:205: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:208: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:211: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:214: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:217: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:220: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:223: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/session.h:231: error: &#8216;QString&#8217; has not been declared
./SleepLib/session.h:234: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:237: error: &#8216;qint64&#8217; has not been declared
./SleepLib/session.h:240: error: &#8216;qint64&#8217; does not name a type
./SleepLib/session.h:243: error: &#8216;qint64&#8217; does not name a type
./SleepLib/session.h:249: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
In file included from ./SleepLib/machine.h:26,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/session.h:257: error: &#8216;qint64&#8217; does not name a type
./SleepLib/session.h:258: error: &#8216;qint64&#8217; does not name a type
./SleepLib/session.h:266: error: &#8216;QString&#8217; does not name a type
In file included from ./SleepLib/machine.h:26,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/session.h: In member function &#8216;void Session::really_set_first(int)&#8217;:
./SleepLib/session.h:93: error: &#8216;s_first&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::really_set_last(int)&#8217;:
./SleepLib/session.h:96: error: &#8216;s_last&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::set_first(int)&#8217;:
./SleepLib/session.h:99: error: &#8216;s_first&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::set_last(int)&#8217;:
./SleepLib/session.h:103: error: &#8216;s_first&#8217; was not declared in this scope
/usr/include/qt3/qglobal.h:978: error: too few arguments to function &#8216;void qWarning(const char*, ...)&#8217;
./SleepLib/session.h:104: error: at this point in file
./SleepLib/session.h:107: error: &#8216;s_last&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;double Session::hours()&#8217;:
./SleepLib/session.h:113: error: &#8216;s_last&#8217; was not declared in this scope
./SleepLib/session.h:113: error: &#8216;s_first&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setCount(int, int)&#8217;:
./SleepLib/session.h:157: error: &#8216;m_cnt&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setSum(int, EventDataType)&#8217;:
./SleepLib/session.h:158: error: &#8216;m_sum&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setMin(int, EventDataType)&#8217;:
./SleepLib/session.h:159: error: &#8216;m_min&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setMax(int, EventDataType)&#8217;:
./SleepLib/session.h:160: error: &#8216;m_max&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setAvg(int, EventDataType)&#8217;:
./SleepLib/session.h:161: error: &#8216;m_avg&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setWavg(int, EventDataType)&#8217;:
./SleepLib/session.h:162: error: &#8216;m_wavg&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setCph(int, EventDataType)&#8217;:
./SleepLib/session.h:166: error: &#8216;m_cph&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setSph(int, EventDataType)&#8217;:
./SleepLib/session.h:167: error: &#8216;m_sph&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setFirst(int, int)&#8217;:
./SleepLib/session.h:168: error: &#8216;m_firstchan&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::setLast(int, int)&#8217;:
./SleepLib/session.h:169: error: &#8216;m_lastchan&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::SetEventFile(int&)&#8217;:
./SleepLib/session.h:231: error: &#8216;s_eventfile&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::updateFirst(int)&#8217;:
./SleepLib/session.h:234: error: &#8216;s_first&#8217; was not declared in this scope
./SleepLib/session.h: In member function &#8216;void Session::updateLast(int)&#8217;:
./SleepLib/session.h:237: error: &#8216;s_last&#8217; was not declared in this scope
In file included from ./SleepLib/day.h:10,
                 from ./SleepLib/machine.h:28,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/common.h: At global scope:
./SleepLib/common.h:25: error: &#8216;qint64&#8217; does not name a type
./SleepLib/common.h: In constructor &#8216;ValueCount::ValueCount()&#8217;:
./SleepLib/common.h:18: error: &#8216;count&#8217; was not declared in this scope
./SleepLib/common.h: In copy constructor &#8216;ValueCount::ValueCount(const ValueCount&)&#8217;:
./SleepLib/common.h:21: error: &#8216;count&#8217; was not declared in this scope
./SleepLib/common.h:21: error: &#8216;const struct ValueCount&#8217; has no member named &#8216;count&#8217;
./SleepLib/common.h: At global scope:
./SleepLib/common.h:35: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:38: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
./SleepLib/common.h:38: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
./SleepLib/common.h:41: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:42: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:43: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:44: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:45: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:46: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:47: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:48: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:50: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:51: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:53: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:54: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:55: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:56: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:57: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:58: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:60: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:61: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:63: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:65: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:66: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:67: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:68: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:69: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:70: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:71: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:72: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:73: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:75: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:76: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:77: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:78: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:79: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:80: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:81: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:82: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:84: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:85: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:86: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:87: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:88: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:89: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:90: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:92: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:93: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:94: error: &#8216;QString&#8217; does not name a type
./SleepLib/common.h:96: error: &#8216;QString&#8217; does not name a type
In file included from ./SleepLib/machine.h:28,
                 from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/day.h:42: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:45: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:48: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:51: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:54: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:57: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:60: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:63: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:66: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:69: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:72: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:75: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:78: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:81: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:84: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:87: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:90: error: &#8216;qint64&#8217; does not name a type
./SleepLib/day.h:93: error: &#8216;qint64&#8217; does not name a type
./SleepLib/day.h:102: error: &#8216;qint64&#8217; does not name a type
./SleepLib/day.h:105: error: &#8216;qint64&#8217; does not name a type
./SleepLib/day.h:108: error: &#8216;qint64&#8217; does not name a type
./SleepLib/day.h:120: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/day.h:120: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/day.h:122: error: expected &#8216;;&#8217; before &#8216;QVector&#8217;
./SleepLib/day.h:122: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/day.h:122: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/day.h:125: error: expected &#8216;;&#8217; before &#8216;int&#8217;
./SleepLib/day.h:141: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/day.h:141: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/day.h:144: error: expected &#8216;;&#8217; before &#8216;bool&#8217;
./SleepLib/day.h:144: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:150: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:153: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/day.h:157: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
./SleepLib/day.h:157: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/day.h:158: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/day.h:158: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/day.h: In member function &#8216;EventDataType Day::hours()&#8217;:
./SleepLib/day.h:114: error: &#8216;total_time&#8217; was not declared in this scope
./SleepLib/day.h: In member function &#8216;Session* Day::operator[](int)&#8217;:
./SleepLib/day.h:117: error: &#8216;sessions&#8217; was not declared in this scope
./SleepLib/day.h: In member function &#8216;int Day::find(Session*)&#8217;:
./SleepLib/day.h:125: error: &#8216;sessions&#8217; was not declared in this scope
./SleepLib/day.h: In member function &#8216;int Day::size()&#8217;:
./SleepLib/day.h:130: error: &#8216;sessions&#8217; was not declared in this scope
In file included from ./SleepLib/profiles.h:16,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/machine.h: At global scope:
./SleepLib/machine.h:40: error: expected class-name before &#8216;{&#8217; token
./SleepLib/machine.h:41: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
./SleepLib/machine.h:42: error: expected &#8216;;&#8217; before &#8216;public&#8217;
./SleepLib/machine.h:46: error: expected &#8216;;&#8217; before &#8216;static&#8217;
./SleepLib/machine.h:52: error: &#8216;QString&#8217; does not name a type
./SleepLib/machine.h:55: error: expected primary-expression before &#8216;void&#8217;
./SleepLib/machine.h:55: error: ISO C++ forbids declaration of &#8216;signals&#8217; with no type
./SleepLib/machine.h:55: error: expected &#8216;;&#8217; before &#8216;void&#8217;
./SleepLib/machine.h: In static member function &#8216;static void SaveThread::msleep(long unsigned int)&#8217;:
./SleepLib/machine.h:46: error: &#8216;QThread&#8217; has not been declared
./SleepLib/machine.h: At global scope:
./SleepLib/machine.h:86: error: ISO C++ forbids declaration of &#8216;QMap&#8217; with no type
./SleepLib/machine.h:86: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/machine.h:89: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/machine.h:89: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/machine.h:92: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/machine.h:92: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/machine.h:98: error: &#8216;QDate&#8217; does not name a type
./SleepLib/machine.h:101: error: &#8216;QDate&#8217; does not name a type
./SleepLib/machine.h:104: error: &#8216;QString&#8217; has not been declared
./SleepLib/machine.h:110: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
./SleepLib/machine.h:110: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SleepLib/machine.h:113: error: expected &#8216;;&#8217; before &#8216;const&#8217;
./SleepLib/machine.h:116: error: &#8216;QString&#8217; does not name a type
./SleepLib/machine.h:126: error: ISO C++ forbids declaration of &#8216;QDate&#8217; with no type
./SleepLib/machine.h:126: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SleepLib/machine.h:129: error: expected &#8216;;&#8217; before &#8216;const&#8217;
./SleepLib/machine.h:129: error: ISO C++ forbids declaration of &#8216;QDate&#8217; with no type
./SleepLib/machine.h:129: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SleepLib/machine.h:132: error: expected &#8216;;&#8217; before &#8216;Session&#8217;
./SleepLib/machine.h:135: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
./SleepLib/machine.h:135: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/machine.h:139: error: &#8216;QMutex&#8217; does not name a type
./SleepLib/machine.h:140: error: ISO C++ forbids declaration of &#8216;QSemaphore&#8217; with no type
./SleepLib/machine.h:140: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
./SleepLib/machine.h:143: error: &#8216;QDate&#8217; does not name a type
./SleepLib/machine.h:146: error: &#8216;QString&#8217; does not name a type
./SleepLib/machine.h:148: error: &#8216;QString&#8217; does not name a type
./SleepLib/machine.h: In member function &#8216;void Machine::SetClass(int)&#8217;:
./SleepLib/machine.h:104: error: &#8216;m_class&#8217; was not declared in this scope
In file included from ./SleepLib/profiles.h:17,
                 from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/machine_loader.h: At global scope:
./SleepLib/machine_loader.h:36: error: &#8216;QString&#8217; has not been declared
./SleepLib/machine_loader.h:42: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
./SleepLib/machine_loader.h:42: error: &#8216;QString&#8217; declared as a &#8216;virtual&#8217; field
./SleepLib/machine_loader.h:42: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
./SleepLib/machine_loader.h:44: error: &#8216;QString&#8217; has not been declared
./SleepLib/machine_loader.h:44: error: &#8216;QString&#8217; has not been declared
./SleepLib/machine_loader.h:69: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
./SleepLib/machine_loader.h:69: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/machine_loader.h:70: error: &#8216;QString&#8217; does not name a type
./SleepLib/machine_loader.h:44: error: default argument for parameter of type &#8216;int&#8217; has type &#8216;const char [1]&#8217;
./SleepLib/machine_loader.h:78: error: expected constructor, destructor, or type conversion before &#8216;<&#8217; token
In file included from Graphs/gSummaryChart.h:10,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./SleepLib/profiles.h:47: error: expected &#8216;)&#8217; before &#8216;name&#8217;
./SleepLib/profiles.h:53: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:56: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:61: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
./SleepLib/profiles.h:61: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/profiles.h:78: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:84: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:87: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
./SleepLib/profiles.h:90: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
./SleepLib/profiles.h:94: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
./SleepLib/profiles.h:94: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/profiles.h:97: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:103: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:105: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:105: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:106: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:106: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:106: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:107: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:107: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:107: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:108: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:108: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:109: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:109: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:109: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:110: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:110: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:110: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:111: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:111: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:111: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:112: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:112: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:112: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:113: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:113: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:113: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:115: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:117: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:117: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:117: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:118: error: &#8216;ChannelID&#8217; has not been declared
./SleepLib/profiles.h:118: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:118: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:120: error: &#8216;QDomElement&#8217; has not been declared
./SleepLib/profiles.h:121: error: &#8216;QDomElement&#8217; does not name a type
./SleepLib/profiles.h:123: error: ISO C++ forbids declaration of &#8216;QMap&#8217; with no type
./SleepLib/profiles.h:123: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
./SleepLib/profiles.h:124: error: &#8216;QDate&#8217; does not name a type
./SleepLib/profiles.h:125: error: &#8216;QDate&#8217; does not name a type
./SleepLib/profiles.h:127: error: &#8216;QDate&#8217; does not name a type
./SleepLib/profiles.h:128: error: &#8216;QDate&#8217; does not name a type
./SleepLib/profiles.h:130: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:142: error: &#8216;QDate&#8217; does not name a type
./SleepLib/profiles.h:53: error: default argument for parameter of type &#8216;int&#8217; has type &#8216;const char [1]&#8217;
./SleepLib/profiles.h:56: error: default argument for parameter of type &#8216;int&#8217; has type &#8216;const char [1]&#8217;
./SleepLib/profiles.h:105: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:105: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:106: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:106: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:107: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:107: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:108: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:108: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:109: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:109: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:110: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:110: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:111: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:111: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:112: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:112: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:113: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:113: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:117: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:117: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:118: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:118: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool Profile::contains(int)&#8217;:
./SleepLib/profiles.h:103: error: &#8216;p_preferences&#8217; was not declared in this scope
./SleepLib/profiles.h: At global scope:
./SleepLib/profiles.h:147: warning: &#8216;GetLoader&#8217; initialized and declared &#8216;extern&#8217;
./SleepLib/profiles.h:147: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:159: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:160: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:161: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:162: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:163: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:164: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:167: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:168: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:169: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:170: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:171: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:172: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:173: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:174: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:175: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:176: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:177: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:178: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:179: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:180: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:183: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:184: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:185: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:186: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:187: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:188: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:189: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:190: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:193: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:194: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:195: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:196: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:197: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:198: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:199: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:200: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:201: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:202: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:203: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:204: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:205: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:206: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:207: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:208: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:209: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:210: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:211: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:214: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:215: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:216: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:217: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:218: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:219: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:220: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:221: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:224: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:225: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:226: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:227: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:228: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:229: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:232: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:233: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:234: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:235: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:236: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:237: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:238: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:239: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:240: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:241: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:242: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:260: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:261: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:262: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:263: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:264: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:265: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:267: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:268: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:269: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:270: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:271: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:272: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h: In constructor &#8216;DoctorInfo::DoctorInfo(Profile*)&#8217;:
./SleepLib/profiles.h:250: error: &#8216;STR_DI_Name&#8217; was not declared in this scope
./SleepLib/profiles.h:250: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:251: error: &#8216;STR_DI_Phone&#8217; was not declared in this scope
./SleepLib/profiles.h:251: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:252: error: &#8216;STR_DI_Email&#8217; was not declared in this scope
./SleepLib/profiles.h:252: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:253: error: &#8216;STR_DI_Practice&#8217; was not declared in this scope
./SleepLib/profiles.h:253: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:254: error: &#8216;STR_DI_Address&#8217; was not declared in this scope
./SleepLib/profiles.h:254: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:255: error: &#8216;STR_DI_PatientID&#8217; was not declared in this scope
./SleepLib/profiles.h:255: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void DoctorInfo::setName(int)&#8217;:
./SleepLib/profiles.h:267: error: &#8216;STR_DI_Name&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void DoctorInfo::setPhone(int)&#8217;:
./SleepLib/profiles.h:268: error: &#8216;STR_DI_Phone&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void DoctorInfo::setEmail(int)&#8217;:
./SleepLib/profiles.h:269: error: &#8216;STR_DI_Email&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void DoctorInfo::setPracticeName(int)&#8217;:
./SleepLib/profiles.h:270: error: &#8216;STR_DI_Practice&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void DoctorInfo::setAddress(int)&#8217;:
./SleepLib/profiles.h:271: error: &#8216;STR_DI_Address&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void DoctorInfo::setPatientID(int)&#8217;:
./SleepLib/profiles.h:272: error: &#8216;STR_DI_PatientID&#8217; was not declared in this scope
./SleepLib/profiles.h: At global scope:
./SleepLib/profiles.h:307: error: &#8216;QDate&#8217; does not name a type
./SleepLib/profiles.h:308: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:309: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:310: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:311: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:312: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:313: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:315: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:317: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:318: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:321: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:322: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:323: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:324: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:325: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:326: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:327: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:329: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:331: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:332: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:338: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:342: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h: In constructor &#8216;UserInfo::UserInfo(Profile*)&#8217;:
./SleepLib/profiles.h:287: error: &#8216;STR_UI_DOB&#8217; was not declared in this scope
./SleepLib/profiles.h:287: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:288: error: &#8216;STR_UI_FirstName&#8217; was not declared in this scope
./SleepLib/profiles.h:288: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:289: error: &#8216;STR_UI_LastName&#8217; was not declared in this scope
./SleepLib/profiles.h:289: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:290: error: &#8216;STR_UI_UserName&#8217; was not declared in this scope
./SleepLib/profiles.h:290: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:291: error: &#8216;STR_UI_Password&#8217; was not declared in this scope
./SleepLib/profiles.h:291: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:292: error: &#8216;STR_UI_Address&#8217; was not declared in this scope
./SleepLib/profiles.h:292: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:293: error: &#8216;STR_UI_Phone&#8217; was not declared in this scope
./SleepLib/profiles.h:293: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:294: error: &#8216;STR_UI_EmailAddress&#8217; was not declared in this scope
./SleepLib/profiles.h:294: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:295: error: &#8216;STR_UI_Country&#8217; was not declared in this scope
./SleepLib/profiles.h:295: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:296: error: &#8216;STR_UI_Height&#8217; was not declared in this scope
./SleepLib/profiles.h:297: error: &#8216;STR_UI_Gender&#8217; was not declared in this scope
./SleepLib/profiles.h:298: error: &#8216;STR_UI_TimeZone&#8217; was not declared in this scope
./SleepLib/profiles.h:298: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:299: error: &#8216;STR_UI_Language&#8217; was not declared in this scope
./SleepLib/profiles.h:300: error: &#8216;STR_UI_DST&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double UserInfo::height()&#8217;:
./SleepLib/profiles.h:314: error: &#8216;STR_UI_Height&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;Gender UserInfo::gender()&#8217;:
./SleepLib/profiles.h:316: error: &#8216;STR_UI_Gender&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserInfo::daylightSaving()&#8217;:
./SleepLib/profiles.h:319: error: &#8216;STR_UI_DST&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setDOB(int)&#8217;:
./SleepLib/profiles.h:321: error: &#8216;STR_UI_DOB&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setFirstName(int)&#8217;:
./SleepLib/profiles.h:322: error: &#8216;STR_UI_FirstName&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setLastName(int)&#8217;:
./SleepLib/profiles.h:323: error: &#8216;STR_UI_LastName&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setUserName(int)&#8217;:
./SleepLib/profiles.h:324: error: &#8216;STR_UI_UserName&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setAddress(int)&#8217;:
./SleepLib/profiles.h:325: error: &#8216;STR_UI_Address&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setPhone(int)&#8217;:
./SleepLib/profiles.h:326: error: &#8216;STR_UI_Phone&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setEmail(int)&#8217;:
./SleepLib/profiles.h:327: error: &#8216;STR_UI_EmailAddress&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setHeight(double)&#8217;:
./SleepLib/profiles.h:328: error: &#8216;STR_UI_Height&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setCountry(int)&#8217;:
./SleepLib/profiles.h:329: error: &#8216;STR_UI_Country&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setGender(Gender)&#8217;:
./SleepLib/profiles.h:330: error: &#8216;STR_UI_Gender&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setTimeZone(int)&#8217;:
./SleepLib/profiles.h:331: error: &#8216;STR_UI_TimeZone&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setLanguage(int)&#8217;:
./SleepLib/profiles.h:332: error: &#8216;STR_UI_Language&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setDaylightSaving(bool)&#8217;:
./SleepLib/profiles.h:333: error: &#8216;STR_UI_DST&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserInfo::hasPassword()&#8217;:
./SleepLib/profiles.h:336: error: &#8216;STR_UI_Password&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserInfo::checkPassword(int)&#8217;:
./SleepLib/profiles.h:339: error: &#8216;QByteArray&#8217; was not declared in this scope
./SleepLib/profiles.h:339: error: expected &#8216;;&#8217; before &#8216;ba&#8217;
./SleepLib/profiles.h:340: error: &#8216;STR_UI_Password&#8217; was not declared in this scope
./SleepLib/profiles.h:340: error: &#8216;QCryptographicHash&#8217; has not been declared
./SleepLib/profiles.h:340: error: &#8216;ba&#8217; was not declared in this scope
./SleepLib/profiles.h:340: error: &#8216;QCryptographicHash&#8217; has not been declared
./SleepLib/profiles.h:340: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h: At global scope:
./SleepLib/profiles.h:338: warning: unused parameter &#8216;password&#8217;
./SleepLib/profiles.h: In member function &#8216;void UserInfo::setPassword(int)&#8217;:
./SleepLib/profiles.h:343: error: &#8216;QByteArray&#8217; was not declared in this scope
./SleepLib/profiles.h:343: error: expected &#8216;;&#8217; before &#8216;ba&#8217;
./SleepLib/profiles.h:345: error: &#8216;STR_UI_Password&#8217; was not declared in this scope
./SleepLib/profiles.h:345: error: &#8216;QCryptographicHash&#8217; has not been declared
./SleepLib/profiles.h:345: error: &#8216;ba&#8217; was not declared in this scope
./SleepLib/profiles.h:345: error: &#8216;QCryptographicHash&#8217; has not been declared
./SleepLib/profiles.h:345: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h: At global scope:
./SleepLib/profiles.h:342: warning: unused parameter &#8216;password&#8217;
./SleepLib/profiles.h:376: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:385: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h: In constructor &#8216;OxiSettings::OxiSettings(Profile*)&#8217;:
./SleepLib/profiles.h:361: error: &#8216;STR_OS_EnableOximetry&#8217; was not declared in this scope
./SleepLib/profiles.h:362: error: &#8216;STR_OS_SyncOximetry&#8217; was not declared in this scope
./SleepLib/profiles.h:363: error: &#8216;STR_OS_OximeterType&#8217; was not declared in this scope
./SleepLib/profiles.h:364: error: &#8216;STR_OS_OxiDiscardThreshold&#8217; was not declared in this scope
./SleepLib/profiles.h:365: error: &#8216;STR_OS_SPO2DropDuration&#8217; was not declared in this scope
./SleepLib/profiles.h:366: error: &#8216;STR_OS_SPO2DropPercentage&#8217; was not declared in this scope
./SleepLib/profiles.h:367: error: &#8216;STR_OS_PulseChangeDuration&#8217; was not declared in this scope
./SleepLib/profiles.h:368: error: &#8216;STR_OS_PulseChangeBPM&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool OxiSettings::oximetryEnabled()&#8217;:
./SleepLib/profiles.h:374: error: &#8216;STR_OS_EnableOximetry&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool OxiSettings::syncOximetry()&#8217;:
./SleepLib/profiles.h:375: error: &#8216;STR_OS_SyncOximetry&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double OxiSettings::oxiDiscardThreshold()&#8217;:
./SleepLib/profiles.h:377: error: &#8216;STR_OS_OxiDiscardThreshold&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double OxiSettings::spO2DropDuration()&#8217;:
./SleepLib/profiles.h:378: error: &#8216;STR_OS_SPO2DropDuration&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double OxiSettings::spO2DropPercentage()&#8217;:
./SleepLib/profiles.h:379: error: &#8216;STR_OS_SPO2DropPercentage&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double OxiSettings::pulseChangeDuration()&#8217;:
./SleepLib/profiles.h:380: error: &#8216;STR_OS_PulseChangeDuration&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double OxiSettings::pulseChangeBPM()&#8217;:
./SleepLib/profiles.h:381: error: &#8216;STR_OS_PulseChangeBPM&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void OxiSettings::setOximetryEnabled(bool)&#8217;:
./SleepLib/profiles.h:383: error: &#8216;STR_OS_EnableOximetry&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void OxiSettings::setSyncOximetry(bool)&#8217;:
./SleepLib/profiles.h:384: error: &#8216;STR_OS_SyncOximetry&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void OxiSettings::setOximeterType(int)&#8217;:
./SleepLib/profiles.h:385: error: &#8216;STR_OS_OximeterType&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void OxiSettings::setOxiDiscardThreshold(double)&#8217;:
./SleepLib/profiles.h:386: error: &#8216;STR_OS_OxiDiscardThreshold&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void OxiSettings::setSpO2DropDuration(double)&#8217;:
./SleepLib/profiles.h:387: error: &#8216;STR_OS_SPO2DropDuration&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void OxiSettings::setSpO2DropPercentage(double)&#8217;:
./SleepLib/profiles.h:388: error: &#8216;STR_OS_SPO2DropPercentage&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void OxiSettings::setPulseChangeDuration(double)&#8217;:
./SleepLib/profiles.h:389: error: &#8216;STR_OS_PulseChangeDuration&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void OxiSettings::setPulseChangeBPM(double)&#8217;:
./SleepLib/profiles.h:390: error: &#8216;STR_OS_PulseChangeBPM&#8217; was not declared in this scope
./SleepLib/profiles.h: At global scope:
./SleepLib/profiles.h:434: error: &#8216;QDate&#8217; does not name a type
./SleepLib/profiles.h:435: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:441: error: &#8216;QString&#8217; does not name a type
./SleepLib/profiles.h:442: error: &#8216;QDate&#8217; does not name a type
./SleepLib/profiles.h:456: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h:457: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:461: error: &#8216;QDate&#8217; has not been declared
./SleepLib/profiles.h:462: error: &#8216;QString&#8217; has not been declared
./SleepLib/profiles.h: In constructor &#8216;CPAPSettings::CPAPSettings(Profile*)&#8217;:
./SleepLib/profiles.h:404: error: &#8216;STR_CS_ComplianceHours&#8217; was not declared in this scope
./SleepLib/profiles.h:405: error: &#8216;STR_CS_ShowCompliance&#8217; was not declared in this scope
./SleepLib/profiles.h:406: error: &#8216;STR_CS_ShowLeaksMode&#8217; was not declared in this scope
./SleepLib/profiles.h:408: error: &#8216;STR_CS_MaskStartDate&#8217; was not declared in this scope
./SleepLib/profiles.h:408: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:409: error: &#8216;STR_CS_MaskDescription&#8217; was not declared in this scope
./SleepLib/profiles.h:409: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:410: error: &#8216;STR_CS_MaskType&#8217; was not declared in this scope
./SleepLib/profiles.h:411: error: &#8216;STR_CS_PrescribedMode&#8217; was not declared in this scope
./SleepLib/profiles.h:412: error: &#8216;STR_CS_PrescribedMinPressure&#8217; was not declared in this scope
./SleepLib/profiles.h:413: error: &#8216;STR_CS_PrescribedMaxPressure&#8217; was not declared in this scope
./SleepLib/profiles.h:414: error: &#8216;STR_CS_UntreatedAHI&#8217; was not declared in this scope
./SleepLib/profiles.h:415: error: &#8216;STR_CS_Notes&#8217; was not declared in this scope
./SleepLib/profiles.h:415: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:416: error: &#8216;STR_CS_DateDiagnosed&#8217; was not declared in this scope
./SleepLib/profiles.h:416: error: &#8216;QDate&#8217; was not declared in this scope
./SleepLib/profiles.h:417: error: &#8216;STR_CS_UserFlowRestriction&#8217; was not declared in this scope
./SleepLib/profiles.h:418: error: &#8216;STR_CS_UserEventDuration&#8217; was not declared in this scope
./SleepLib/profiles.h:419: error: &#8216;STR_CS_UserEventDuplicates&#8217; was not declared in this scope
./SleepLib/profiles.h:420: error: &#8216;STR_CS_UserEventFlagging&#8217; was not declared in this scope
./SleepLib/profiles.h:421: error: &#8216;STR_CS_AHIWindow&#8217; was not declared in this scope
./SleepLib/profiles.h:422: error: &#8216;STR_CS_AHIReset&#8217; was not declared in this scope
./SleepLib/profiles.h:423: error: &#8216;STR_CS_ClockDrift&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double CPAPSettings::complianceHours()&#8217;:
./SleepLib/profiles.h:431: error: &#8216;STR_CS_ComplianceHours&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool CPAPSettings::showComplianceInfo()&#8217;:
./SleepLib/profiles.h:432: error: &#8216;STR_CS_ShowCompliance&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;int CPAPSettings::leakMode()&#8217;:
./SleepLib/profiles.h:433: error: &#8216;STR_CS_ShowLeaksMode&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;MaskType CPAPSettings::maskType()&#8217;:
./SleepLib/profiles.h:436: error: &#8216;STR_CS_MaskType&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;CPAPMode CPAPSettings::mode()&#8217;:
./SleepLib/profiles.h:437: error: &#8216;STR_CS_PrescribedMode&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double CPAPSettings::minPressure()&#8217;:
./SleepLib/profiles.h:438: error: &#8216;STR_CS_PrescribedMinPressure&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double CPAPSettings::maxPressure()&#8217;:
./SleepLib/profiles.h:439: error: &#8216;STR_CS_PrescribedMaxPressure&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double CPAPSettings::untreatedAHI()&#8217;:
./SleepLib/profiles.h:440: error: &#8216;STR_CS_UntreatedAHI&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double CPAPSettings::userFlowRestriction()&#8217;:
./SleepLib/profiles.h:443: error: &#8216;STR_CS_UserFlowRestriction&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double CPAPSettings::userEventDuration()&#8217;:
./SleepLib/profiles.h:444: error: &#8216;STR_CS_UserEventDuration&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool CPAPSettings::userEventDuplicates()&#8217;:
./SleepLib/profiles.h:445: error: &#8216;STR_CS_UserEventDuplicates&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double CPAPSettings::AHIWindow()&#8217;:
./SleepLib/profiles.h:446: error: &#8216;STR_CS_AHIWindow&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool CPAPSettings::AHIReset()&#8217;:
./SleepLib/profiles.h:447: error: &#8216;STR_CS_AHIReset&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool CPAPSettings::userEventFlagging()&#8217;:
./SleepLib/profiles.h:448: error: &#8216;STR_CS_UserEventFlagging&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;int CPAPSettings::clockDrift()&#8217;:
./SleepLib/profiles.h:449: error: &#8216;STR_CS_ClockDrift&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setMode(CPAPMode)&#8217;:
./SleepLib/profiles.h:452: error: &#8216;STR_CS_PrescribedMode&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setMinPressure(double)&#8217;:
./SleepLib/profiles.h:453: error: &#8216;STR_CS_PrescribedMinPressure&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setMaxPressure(double)&#8217;:
./SleepLib/profiles.h:454: error: &#8216;STR_CS_PrescribedMaxPressure&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setUntreatedAHI(double)&#8217;:
./SleepLib/profiles.h:455: error: &#8216;STR_CS_UntreatedAHI&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setNotes(int)&#8217;:
./SleepLib/profiles.h:456: error: &#8216;STR_CS_Notes&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setDateDiagnosed(int)&#8217;:
./SleepLib/profiles.h:457: error: &#8216;STR_CS_DateDiagnosed&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setComplianceHours(double)&#8217;:
./SleepLib/profiles.h:458: error: &#8216;STR_CS_ComplianceHours&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setShowComplianceInfo(bool)&#8217;:
./SleepLib/profiles.h:459: error: &#8216;STR_CS_ShowCompliance&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setLeakMode(int)&#8217;:
./SleepLib/profiles.h:460: error: &#8216;STR_CS_ShowLeaksMode&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setMaskStartDate(int)&#8217;:
./SleepLib/profiles.h:461: error: &#8216;STR_CS_MaskStartDate&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setMaskDescription(int)&#8217;:
./SleepLib/profiles.h:462: error: &#8216;STR_CS_MaskDescription&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setMaskType(MaskType)&#8217;:
./SleepLib/profiles.h:463: error: &#8216;STR_CS_MaskType&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setUserFlowRestriction(double)&#8217;:
./SleepLib/profiles.h:464: error: &#8216;STR_CS_UserFlowRestriction&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setUserEventDuration(double)&#8217;:
./SleepLib/profiles.h:465: error: &#8216;STR_CS_UserEventDuration&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setAHIWindow(double)&#8217;:
./SleepLib/profiles.h:466: error: &#8216;STR_CS_AHIWindow&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setAHIReset(bool)&#8217;:
./SleepLib/profiles.h:467: error: &#8216;STR_CS_AHIReset&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setUserEventFlagging(bool)&#8217;:
./SleepLib/profiles.h:468: error: &#8216;STR_CS_UserEventFlagging&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setUserEventDuplicates(bool)&#8217;:
./SleepLib/profiles.h:469: error: &#8216;STR_CS_UserEventDuplicates&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void CPAPSettings::setClockDrift(int)&#8217;:
./SleepLib/profiles.h:470: error: &#8216;STR_CS_ClockDrift&#8217; was not declared in this scope
./SleepLib/profiles.h: At global scope:
./SleepLib/profiles.h:497: error: &#8216;QTime&#8217; does not name a type
./SleepLib/profiles.h:506: error: &#8216;QTime&#8217; has not been declared
./SleepLib/profiles.h: In constructor &#8216;SessionSettings::SessionSettings(Profile*)&#8217;:
./SleepLib/profiles.h:484: error: &#8216;STR_IS_DaySplitTime&#8217; was not declared in this scope
./SleepLib/profiles.h:484: error: &#8216;QTime&#8217; was not declared in this scope
./SleepLib/profiles.h:485: error: &#8216;STR_IS_CacheSessions&#8217; was not declared in this scope
./SleepLib/profiles.h:486: error: &#8216;STR_IS_CombineCloseSessions&#8217; was not declared in this scope
./SleepLib/profiles.h:487: error: &#8216;STR_IS_IgnoreShorterSessions&#8217; was not declared in this scope
./SleepLib/profiles.h:488: error: &#8216;STR_IS_Multithreading&#8217; was not declared in this scope
./SleepLib/profiles.h:488: error: &#8216;QThread&#8217; has not been declared
./SleepLib/profiles.h:489: error: &#8216;STR_IS_BackupCardData&#8217; was not declared in this scope
./SleepLib/profiles.h:490: error: &#8216;STR_IS_CompressBackupData&#8217; was not declared in this scope
./SleepLib/profiles.h:491: error: &#8216;STR_IS_CompressSessionData&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool SessionSettings::cacheSessions()&#8217;:
./SleepLib/profiles.h:498: error: &#8216;STR_IS_CacheSessions&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double SessionSettings::combineCloseSessions()&#8217;:
./SleepLib/profiles.h:499: error: &#8216;STR_IS_CombineCloseSessions&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double SessionSettings::ignoreShortSessions()&#8217;:
./SleepLib/profiles.h:500: error: &#8216;STR_IS_IgnoreShorterSessions&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool SessionSettings::multithreading()&#8217;:
./SleepLib/profiles.h:501: error: &#8216;STR_IS_Multithreading&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool SessionSettings::compressSessionData()&#8217;:
./SleepLib/profiles.h:502: error: &#8216;STR_IS_CompressSessionData&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool SessionSettings::compressBackupData()&#8217;:
./SleepLib/profiles.h:503: error: &#8216;STR_IS_CompressBackupData&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool SessionSettings::backupCardData()&#8217;:
./SleepLib/profiles.h:504: error: &#8216;STR_IS_BackupCardData&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void SessionSettings::setDaySplitTime(int)&#8217;:
./SleepLib/profiles.h:506: error: &#8216;STR_IS_DaySplitTime&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void SessionSettings::setCacheSessions(bool)&#8217;:
./SleepLib/profiles.h:507: error: &#8216;STR_IS_CacheSessions&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void SessionSettings::setCombineCloseSessions(double)&#8217;:
./SleepLib/profiles.h:508: error: &#8216;STR_IS_CombineCloseSessions&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void SessionSettings::setIgnoreShortSessions(double)&#8217;:
./SleepLib/profiles.h:509: error: &#8216;STR_IS_IgnoreShorterSessions&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void SessionSettings::setMultithreading(bool)&#8217;:
./SleepLib/profiles.h:510: error: &#8216;STR_IS_Multithreading&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void SessionSettings::setBackupCardData(bool)&#8217;:
./SleepLib/profiles.h:511: error: &#8216;STR_IS_BackupCardData&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void SessionSettings::setCompressBackupData(bool)&#8217;:
./SleepLib/profiles.h:512: error: &#8216;STR_IS_CompressBackupData&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void SessionSettings::setCompressSessionData(bool)&#8217;:
./SleepLib/profiles.h:513: error: &#8216;STR_IS_CompressSessionData&#8217; was not declared in this scope
./SleepLib/profiles.h: In constructor &#8216;AppearanceSettings::AppearanceSettings(Profile*)&#8217;:
./SleepLib/profiles.h:527: error: &#8216;STR_AS_GraphHeight&#8217; was not declared in this scope
./SleepLib/profiles.h:528: error: &#8216;STR_AS_AntiAliasing&#8217; was not declared in this scope
./SleepLib/profiles.h:529: error: &#8216;STR_AS_GraphSnapshots&#8217; was not declared in this scope
./SleepLib/profiles.h:530: error: &#8216;STR_AS_Animations&#8217; was not declared in this scope
./SleepLib/profiles.h:531: error: &#8216;STR_AS_SquareWave&#8217; was not declared in this scope
./SleepLib/profiles.h:532: error: &#8216;STR_AS_OverlayType&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;int AppearanceSettings::graphHeight()&#8217;:
./SleepLib/profiles.h:539: error: &#8216;STR_AS_GraphHeight&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool AppearanceSettings::antiAliasing()&#8217;:
./SleepLib/profiles.h:541: error: &#8216;STR_AS_AntiAliasing&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool AppearanceSettings::graphSnapshots()&#8217;:
./SleepLib/profiles.h:543: error: &#8216;STR_AS_GraphSnapshots&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool AppearanceSettings::animations()&#8217;:
./SleepLib/profiles.h:545: error: &#8216;STR_AS_Animations&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool AppearanceSettings::squareWavePlots()&#8217;:
./SleepLib/profiles.h:547: error: &#8216;STR_AS_SquareWave&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;OverlayDisplayType AppearanceSettings::overlayType()&#8217;:
./SleepLib/profiles.h:549: error: &#8216;STR_AS_OverlayType&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void AppearanceSettings::setGraphHeight(int)&#8217;:
./SleepLib/profiles.h:552: error: &#8216;STR_AS_GraphHeight&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void AppearanceSettings::setAntiAliasing(bool)&#8217;:
./SleepLib/profiles.h:554: error: &#8216;STR_AS_AntiAliasing&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void AppearanceSettings::setGraphSnapshots(bool)&#8217;:
./SleepLib/profiles.h:556: error: &#8216;STR_AS_GraphSnapshots&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void AppearanceSettings::setAnimations(bool)&#8217;:
./SleepLib/profiles.h:558: error: &#8216;STR_AS_Animations&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void AppearanceSettings::setSquareWavePlots(bool)&#8217;:
./SleepLib/profiles.h:560: error: &#8216;STR_AS_SquareWave&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void AppearanceSettings::setOverlayType(OverlayDisplayType)&#8217;:
./SleepLib/profiles.h:562: error: &#8216;STR_AS_OverlayType&#8217; was not declared in this scope
./SleepLib/profiles.h: In constructor &#8216;UserSettings::UserSettings(Profile*)&#8217;:
./SleepLib/profiles.h:576: error: &#8216;STR_US_UnitSystem&#8217; was not declared in this scope
./SleepLib/profiles.h:577: error: &#8216;STR_US_EventWindowSize&#8217; was not declared in this scope
./SleepLib/profiles.h:578: error: &#8216;STR_US_SkipEmptyDays&#8217; was not declared in this scope
./SleepLib/profiles.h:579: error: &#8216;STR_US_RebuildCache&#8217; was not declared in this scope
./SleepLib/profiles.h:580: error: &#8216;STR_US_ShowDebug&#8217; was not declared in this scope
./SleepLib/profiles.h:581: error: &#8216;STR_US_LinkGroups&#8217; was not declared in this scope
./SleepLib/profiles.h:582: error: &#8216;STR_US_CalculateRDI&#8217; was not declared in this scope
./SleepLib/profiles.h:583: error: &#8216;STR_US_ShowSerialNumbers&#8217; was not declared in this scope
./SleepLib/profiles.h:584: error: &#8216;STR_US_PrefCalcMiddle&#8217; was not declared in this scope
./SleepLib/profiles.h:585: error: &#8216;STR_US_PrefCalcPercentile&#8217; was not declared in this scope
./SleepLib/profiles.h:586: error: &#8216;STR_US_PrefCalcMax&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;UnitSystem UserSettings::unitSystem()&#8217;:
./SleepLib/profiles.h:592: error: &#8216;STR_US_UnitSystem&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double UserSettings::eventWindowSize()&#8217;:
./SleepLib/profiles.h:593: error: &#8216;STR_US_EventWindowSize&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserSettings::skipEmptyDays()&#8217;:
./SleepLib/profiles.h:594: error: &#8216;STR_US_SkipEmptyDays&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserSettings::rebuildCache()&#8217;:
./SleepLib/profiles.h:595: error: &#8216;STR_US_RebuildCache&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserSettings::showDebug()&#8217;:
./SleepLib/profiles.h:596: error: &#8216;STR_US_ShowDebug&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserSettings::linkGroups()&#8217;:
./SleepLib/profiles.h:597: error: &#8216;STR_US_LinkGroups&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserSettings::calculateRDI()&#8217;:
./SleepLib/profiles.h:598: error: &#8216;STR_US_CalculateRDI&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;bool UserSettings::showSerialNumbers()&#8217;:
./SleepLib/profiles.h:599: error: &#8216;STR_US_ShowSerialNumbers&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;int UserSettings::prefCalcMiddle()&#8217;:
./SleepLib/profiles.h:600: error: &#8216;STR_US_PrefCalcMiddle&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;double UserSettings::prefCalcPercentile()&#8217;:
./SleepLib/profiles.h:601: error: &#8216;STR_US_PrefCalcPercentile&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;int UserSettings::prefCalcMax()&#8217;:
./SleepLib/profiles.h:602: error: &#8216;STR_US_PrefCalcMax&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setUnitSystem(UnitSystem)&#8217;:
./SleepLib/profiles.h:605: error: &#8216;STR_US_UnitSystem&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setEventWindowSize(double)&#8217;:
./SleepLib/profiles.h:606: error: &#8216;STR_US_EventWindowSize&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setSkipEmptyDays(bool)&#8217;:
./SleepLib/profiles.h:607: error: &#8216;STR_US_SkipEmptyDays&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setRebuildCache(bool)&#8217;:
./SleepLib/profiles.h:608: error: &#8216;STR_US_RebuildCache&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setShowDebug(bool)&#8217;:
./SleepLib/profiles.h:609: error: &#8216;STR_US_ShowDebug&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setLinkGroups(bool)&#8217;:
./SleepLib/profiles.h:610: error: &#8216;STR_US_LinkGroups&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setCalculateRDI(bool)&#8217;:
./SleepLib/profiles.h:611: error: &#8216;STR_US_CalculateRDI&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setShowSerialNumbers(bool)&#8217;:
./SleepLib/profiles.h:612: error: &#8216;STR_US_ShowSerialNumbers&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setPrefCalcMiddle(int)&#8217;:
./SleepLib/profiles.h:613: error: &#8216;STR_US_PrefCalcMiddle&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setPrefCalcPercentile(double)&#8217;:
./SleepLib/profiles.h:614: error: &#8216;STR_US_PrefCalcPercentile&#8217; was not declared in this scope
./SleepLib/profiles.h: In member function &#8216;void UserSettings::setPrefCalcMax(int)&#8217;:
./SleepLib/profiles.h:615: error: &#8216;STR_US_PrefCalcMax&#8217; was not declared in this scope
./SleepLib/profiles.h: At global scope:
./SleepLib/profiles.h:624: error: expected initializer before &#8216;<&#8217; token
./SleepLib/profiles.h:628: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:629: error: &#8216;QString&#8217; was not declared in this scope
./SleepLib/profiles.h:630: error: &#8216;Profile* Profiles::Get()&#8217; redeclared as different kind of symbol
./SleepLib/profiles.h:629: error: previous declaration of &#8216;Profile* Profiles::Get&#8217;
In file included from Graphs/gGraphView.h:19,
                 from Graphs/gSummaryChart.h:11,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
./Graphs/glcommon.h:18: error: &#8216;QColor&#8217; has not been declared
./Graphs/glcommon.h:24: error: ISO C++ forbids declaration of &#8216;QColor&#8217; with no type
./Graphs/glcommon.h:24: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;color&#8217;
In file included from Graphs/gSummaryChart.h:11,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gGraphView.h:34: error: expected initializer before &#8216;*&#8217; token
Graphs/gGraphView.h:35: error: expected initializer before &#8216;*&#8217; token
Graphs/gGraphView.h:36: error: expected initializer before &#8216;*&#8217; token
Graphs/gGraphView.h:38: error: expected initializer before &#8216;<&#8217; token
Graphs/gGraphView.h:46: error: variable or field &#8216;GetTextExtent&#8217; declared void
Graphs/gGraphView.h:46: error: &#8216;QString&#8217; was not declared in this scope
Graphs/gGraphView.h:46: error: expected primary-expression before &#8216;int&#8217;
Graphs/gGraphView.h:46: error: expected primary-expression before &#8216;int&#8217;
Graphs/gGraphView.h:46: error: &#8216;QFont&#8217; was not declared in this scope
Graphs/gGraphView.h:46: error: &#8216;font&#8217; was not declared in this scope
Graphs/gGraphView.h:46: error: &#8216;defaultfont&#8217; was not declared in this scope
Graphs/gGraphView.h:49: error: &#8216;QFont&#8217; was not declared in this scope
Graphs/gGraphView.h:49: error: &#8216;font&#8217; was not declared in this scope
Graphs/gGraphView.h:49: error: &#8216;defaultfont&#8217; was not declared in this scope
Graphs/gGraphView.h:56: error: &#8216;quint32&#8217; does not name a type
Graphs/gGraphView.h:72: error: expected &#8216;)&#8217; before &#8216;_x&#8217;
Graphs/gGraphView.h:73: error: &#8216;GLshort&#8217; does not name a type
Graphs/gGraphView.h:74: error: &#8216;GLshort&#8217; does not name a type
Graphs/gGraphView.h:75: error: &#8216;RGBA&#8217; does not name a type
Graphs/gGraphView.h:88: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:88: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:88: error: &#8216;RGBA&#8217; has not been declared
Graphs/gGraphView.h:89: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:89: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:89: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:89: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:89: error: &#8216;RGBA&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:90: error: &#8216;RGBA&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;RGBA&#8217; has not been declared
Graphs/gGraphView.h:91: error: &#8216;RGBA&#8217; has not been declared
In file included from Graphs/gSummaryChart.h:11,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gGraphView.h:93: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:93: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:94: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:94: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:94: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:94: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:95: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:95: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:95: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:95: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:95: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:95: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:95: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:95: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:97: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:97: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:98: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:98: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:98: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:98: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:99: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:99: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:99: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:99: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:99: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:99: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:99: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:99: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:103: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:103: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:103: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:103: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:108: error: &#8216;GLuint&#8217; does not name a type
Graphs/gGraphView.h:115: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:117: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:118: error: &#8216;GLuint&#8217; has not been declared
Graphs/gGraphView.h:118: error: &#8216;GLuint&#8217; has not been declared
Graphs/gGraphView.h:124: error: &#8216;GLuint&#8217; does not name a type
Graphs/gGraphView.h:138: error: &#8216;GLshort&#8217; does not name a type
Graphs/gGraphView.h:140: error: &#8216;GLuint&#8217; does not name a type
Graphs/gGraphView.h:142: error: &#8216;GLshort&#8217; does not name a type
Graphs/gGraphView.h:144: error: &#8216;GLuint&#8217; does not name a type
Graphs/gGraphView.h:146: error: &#8216;GLuint&#8217; does not name a type
In file included from Graphs/gSummaryChart.h:11,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gGraphView.h:85: error: &#8216;GL_LINES&#8217; was not declared in this scope
In file included from Graphs/gSummaryChart.h:11,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gGraphView.h: In member function &#8216;void gVertexBuffer::scissor(int, int, int, int)&#8217;:
Graphs/gGraphView.h:103: error: &#8216;s_x&#8217; was not declared in this scope
Graphs/gGraphView.h:103: error: &#8216;s_y&#8217; was not declared in this scope
Graphs/gGraphView.h:103: error: &#8216;s_width&#8217; was not declared in this scope
Graphs/gGraphView.h:103: error: &#8216;s_height&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void gVertexBuffer::setStipple(int)&#8217;:
Graphs/gGraphView.h:115: error: &#8216;m_stipple&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void gVertexBuffer::setBlendFunc(int, int)&#8217;:
Graphs/gGraphView.h:118: error: &#8216;m_blendfunc1&#8217; was not declared in this scope
Graphs/gGraphView.h:118: error: &#8216;m_blendfunc2&#8217; was not declared in this scope
Graphs/gGraphView.h: At global scope:
Graphs/gGraphView.h:157: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:157: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:157: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:157: error: &#8216;GLshort&#8217; has not been declared
Graphs/gGraphView.h:168: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:169: error: &#8216;GLuint&#8217; has not been declared
Graphs/gGraphView.h:169: error: &#8216;GLuint&#8217; has not been declared
Graphs/gGraphView.h:175: error: &#8216;QColor&#8217; does not name a type
Graphs/gGraphView.h:181: error: &#8216;QMutex&#8217; does not name a type
Graphs/gGraphView.h:183: error: &#8216;GLuint&#8217; does not name a type
Graphs/gGraphView.h:155: error: &#8216;GL_LINES&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void GLBuffer::setColor(int)&#8217;:
Graphs/gGraphView.h:168: error: &#8216;m_color&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void GLBuffer::setBlendFunc(int, int)&#8217;:
Graphs/gGraphView.h:169: error: &#8216;m_blendfunc1&#8217; was not declared in this scope
Graphs/gGraphView.h:169: error: &#8216;m_blendfunc2&#8217; was not declared in this scope
Graphs/gGraphView.h: At global scope:
Graphs/gGraphView.h:223: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:223: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:223: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:224: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:224: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:224: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:224: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:224: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:225: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:226: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;GLfloat&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:227: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:231: error: ISO C++ forbids declaration of &#8216;GLfloat&#8217; with no type
Graphs/gGraphView.h:231: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Graphs/gGraphView.h:232: error: ISO C++ forbids declaration of &#8216;GLubyte&#8217; with no type
Graphs/gGraphView.h:232: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Graphs/gGraphView.h:220: error: &#8216;GL_LINES&#8217; was not declared in this scope
Graphs/gGraphView.h:247: error: &#8216;QString&#8217; does not name a type
Graphs/gGraphView.h:249: error: &#8216;QColor&#8217; does not name a type
Graphs/gGraphView.h:251: error: ISO C++ forbids declaration of &#8216;QFont&#8217; with no type
Graphs/gGraphView.h:251: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Graphs/gGraphView.h:258: error: expected class-name before &#8216;{&#8217; token
Graphs/gGraphView.h:260: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
Graphs/gGraphView.h:261: error: &#8216;QWheelEvent&#8217; has not been declared
Graphs/gGraphView.h:273: error: expected &#8216;)&#8217; before &#8216;code&#8217;
Graphs/gGraphView.h:280: error: &#8216;ChannelID&#8217; has not been declared
Graphs/gGraphView.h:282: error: ISO C++ forbids declaration of &#8216;ChannelID&#8217; with no type
Graphs/gGraphView.h:282: error: expected &#8216;;&#8217; before &#8216;&&#8217; token
Graphs/gGraphView.h:285: error: expected &#8216;;&#8217; before &#8216;virtual&#8217;
Graphs/gGraphView.h:294: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:297: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:309: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:312: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:372: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:374: error: &#8216;ChannelID&#8217; does not name a type
Graphs/gGraphView.h:383: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gGraphView.h:383: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:384: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gGraphView.h:384: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:387: error: &#8216;QWheelEvent&#8217; has not been declared
Graphs/gGraphView.h:389: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:391: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:393: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:395: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:397: error: &#8216;QKeyEvent&#8217; has not been declared
Graphs/gGraphView.h: In member function &#8216;virtual void Layer::SetCode(int)&#8217;:
Graphs/gGraphView.h:280: error: &#8216;m_code&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;virtual void Layer::setMinX(int)&#8217;:
Graphs/gGraphView.h:309: error: &#8216;m_minx&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;virtual void Layer::setMaxX(int)&#8217;:
Graphs/gGraphView.h:312: error: &#8216;m_maxx&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void Layer::addGLBuf(GLBuffer*)&#8217;:
Graphs/gGraphView.h:366: error: &#8216;mgl_buffers&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void Layer::addVertexBuffer(gVertexBuffer*)&#8217;:
Graphs/gGraphView.h:367: error: &#8216;mv_buffers&#8217; was not declared in this scope
Graphs/gGraphView.h: At global scope:
Graphs/gGraphView.h:413: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:416: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:434: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gGraphView.h:434: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:436: error: expected &#8216;;&#8217; before &#8216;protected&#8217;
Graphs/gGraphView.h:438: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gGraphView.h:438: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:449: error: expected class-name before &#8216;{&#8217; token
Graphs/gGraphView.h:459: error: &#8216;QMutex&#8217; does not name a type
Graphs/gGraphView.h:469: error: expected class-name before &#8216;{&#8217; token
Graphs/gGraphView.h:470: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
Graphs/gGraphView.h:471: error: expected &#8216;;&#8217; before &#8216;public&#8217;
Graphs/gGraphView.h:479: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:491: error: ISO C++ forbids declaration of &#8216;QTimer&#8217; with no type
Graphs/gGraphView.h:491: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Graphs/gGraphView.h:492: error: &#8216;QPoint&#8217; does not name a type
Graphs/gGraphView.h:494: error: &#8216;QString&#8217; does not name a type
Graphs/gGraphView.h:497: error: expected &#8216;:&#8217; before &#8216;slots&#8217;
Graphs/gGraphView.h:500: error: expected primary-expression before &#8216;void&#8217;
Graphs/gGraphView.h:500: error: ISO C++ forbids declaration of &#8216;slots&#8217; with no type
Graphs/gGraphView.h:500: error: expected &#8216;;&#8217; before &#8216;void&#8217;
Graphs/gGraphView.h:507: error: expected class-name before &#8216;{&#8217; token
Graphs/gGraphView.h:508: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
Graphs/gGraphView.h:509: error: expected &#8216;;&#8217; before &#8216;public&#8217;
Graphs/gGraphView.h:518: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:518: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:539: error: &#8216;QPixmap&#8217; does not name a type
Graphs/gGraphView.h:578: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:581: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:581: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:581: error: &#8216;QFont&#8217; has not been declared
Graphs/gGraphView.h:590: error: &#8216;QString&#8217; does not name a type
Graphs/gGraphView.h:593: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
Graphs/gGraphView.h:593: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;title&#8217;
Graphs/gGraphView.h:596: error: &#8216;QString&#8217; does not name a type
Graphs/gGraphView.h:599: error: ISO C++ forbids declaration of &#8216;QString&#8217; with no type
Graphs/gGraphView.h:599: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;units&#8217;
Graphs/gGraphView.h:607: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:607: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:610: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:613: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:622: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:625: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:655: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:689: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:729: error: &#8216;QRect&#8217; does not name a type
Graphs/gGraphView.h:730: error: ISO C++ forbids declaration of &#8216;QTimer&#8217; with no type
Graphs/gGraphView.h:730: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Graphs/gGraphView.h:733: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gGraphView.h:733: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:735: error: expected &#8216;;&#8217; before &#8216;short&#8217;
Graphs/gGraphView.h:740: error: &#8216;QWheelEvent&#8217; has not been declared
Graphs/gGraphView.h:743: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:746: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:749: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:752: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:755: error: &#8216;QKeyEvent&#8217; has not been declared
Graphs/gGraphView.h:762: error: &#8216;QString&#8217; does not name a type
Graphs/gGraphView.h:763: error: &#8216;QString&#8217; does not name a type
Graphs/gGraphView.h:766: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gGraphView.h:766: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:773: error: &#8216;QRect&#8217; does not name a type
Graphs/gGraphView.h:775: error: &#8216;QPoint&#8217; does not name a type
Graphs/gGraphView.h:785: error: expected primary-expression before &#8216;protected&#8217;
Graphs/gGraphView.h:785: error: ISO C++ forbids declaration of &#8216;signals&#8217; with no type
Graphs/gGraphView.h:785: error: expected &#8216;;&#8217; before &#8216;protected&#8217;
Graphs/gGraphView.h:518: error: default argument for parameter of type &#8216;int&#8217; has type &#8216;const char [1]&#8217;
Graphs/gGraphView.h:518: error: default argument for parameter of type &#8216;int&#8217; has type &#8216;const char [1]&#8217;
Graphs/gGraphView.h:581: error: &#8216;Qt&#8217; has not been declared
Graphs/gGraphView.h:581: error: &#8216;defaultfont&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void gGraph::setTitle(int)&#8217;:
Graphs/gGraphView.h:593: error: &#8216;m_title&#8217; was not declared in this scope
Graphs/gGraphView.h:593: error: &#8216;title&#8217; was not declared in this scope
Graphs/gGraphView.h: At global scope:
Graphs/gGraphView.h:593: warning: unused parameter &#8216;QString&#8217;
Graphs/gGraphView.h: In member function &#8216;void gGraph::setUnits(int)&#8217;:
Graphs/gGraphView.h:599: error: &#8216;m_units&#8217; was not declared in this scope
Graphs/gGraphView.h:599: error: &#8216;units&#8217; was not declared in this scope
Graphs/gGraphView.h: At global scope:
Graphs/gGraphView.h:599: warning: unused parameter &#8216;QString&#8217;
Graphs/gGraphView.h:802: error: expected class-name before &#8216;{&#8217; token
Graphs/gGraphView.h:803: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
Graphs/gGraphView.h:804: error: expected &#8216;;&#8217; before &#8216;public&#8217;
Graphs/gGraphView.h:836: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:836: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:839: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:839: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:845: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:845: error: &#8216;qint64&#8217; has not been declared
Graphs/gGraphView.h:848: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:851: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:854: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
Graphs/gGraphView.h:867: error: &#8216;QPoint&#8217; does not name a type
Graphs/gGraphView.h:868: error: &#8216;QPoint&#8217; does not name a type
Graphs/gGraphView.h:869: error: &#8216;QPoint&#8217; has not been declared
Graphs/gGraphView.h:870: error: &#8216;QPoint&#8217; has not been declared
Graphs/gGraphView.h:886: error: ISO C++ forbids declaration of &#8216;QTimer&#8217; with no type
Graphs/gGraphView.h:886: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Graphs/gGraphView.h:892: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:892: error: &#8216;QColor&#8217; has not been declared
Graphs/gGraphView.h:892: error: &#8216;QFont&#8217; has not been declared
Graphs/gGraphView.h:924: error: &#8216;QString&#8217; has not been declared
Graphs/gGraphView.h:926: error: &#8216;QImage&#8217; has not been declared
Graphs/gGraphView.h:929: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gGraphView.h:929: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:930: error: &#8216;GLuint&#8217; does not name a type
Graphs/gGraphView.h:980: error: &#8216;QResizeEvent&#8217; has not been declared
Graphs/gGraphView.h:989: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:991: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:993: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:995: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gGraphView.h:997: error: &#8216;QWheelEvent&#8217; has not been declared
Graphs/gGraphView.h:999: error: &#8216;QKeyEvent&#8217; has not been declared
Graphs/gGraphView.h:1005: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
Graphs/gGraphView.h:1005: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:1011: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gGraphView.h:1011: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:1014: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
Graphs/gGraphView.h:1014: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gGraphView.h:1029: error: &#8216;QPoint&#8217; does not name a type
Graphs/gGraphView.h:1030: error: &#8216;QPoint&#8217; does not name a type
Graphs/gGraphView.h:1031: error: &#8216;QPoint&#8217; does not name a type
Graphs/gGraphView.h:1035: error: ISO C++ forbids declaration of &#8216;QTimer&#8217; with no type
Graphs/gGraphView.h:1035: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
Graphs/gGraphView.h:1046: error: &#8216;QString&#8217; does not name a type
Graphs/gGraphView.h:1049: error: &#8216;qint64&#8217; does not name a type
Graphs/gGraphView.h:1052: error: &#8216;QPixmap&#8217; does not name a type
Graphs/gGraphView.h:1053: error: &#8216;QPixmap&#8217; does not name a type
Graphs/gGraphView.h:1061: error: &#8216;QPoint&#8217; does not name a type
Graphs/gGraphView.h:1063: error: &#8216;QTime&#8217; does not name a type
Graphs/gGraphView.h:1069: error: expected primary-expression before &#8216;public&#8217;
Graphs/gGraphView.h:1069: error: ISO C++ forbids declaration of &#8216;signals&#8217; with no type
Graphs/gGraphView.h:1069: error: expected &#8216;;&#8217; before &#8216;public&#8217;
Graphs/gGraphView.h:892: error: &#8216;Qt&#8217; has not been declared
Graphs/gGraphView.h:892: error: &#8216;defaultfont&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void gGraphView::setPointClicked(int)&#8217;:
Graphs/gGraphView.h:869: error: &#8216;m_point_clicked&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void gGraphView::setGlobalPointClicked(int)&#8217;:
Graphs/gGraphView.h:870: error: &#8216;m_global_point_clicked&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;int gGraphView::size()&#8217;:
Graphs/gGraphView.h:898: error: &#8216;m_graphs&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;gGraph* gGraphView::operator[](int)&#8217;:
Graphs/gGraphView.h:901: error: &#8216;m_graphs&#8217; was not declared in this scope
Graphs/gGraphView.h: In member function &#8216;void gGraphView::setEmptyText(int)&#8217;:
Graphs/gGraphView.h:924: error: &#8216;m_emptytext&#8217; was not declared in this scope
In file included from Graphs/gSummaryChart.h:12,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gXAxis.h: At global scope:
Graphs/gXAxis.h:16: error: expected &#8216;)&#8217; before &#8216;col&#8217;
In file included from Graphs/gSummaryChart.h:12,
                 from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gXAxis.h:39: error: &#8216;QColor&#8217; does not name a type
Graphs/gXAxis.h:40: error: &#8216;QColor&#8217; does not name a type
Graphs/gXAxis.h:41: error: &#8216;QColor&#8217; does not name a type
Graphs/gXAxis.h:42: error: &#8216;QColor&#8217; does not name a type
Graphs/gXAxis.h:44: error: &#8216;qint64&#8217; does not name a type
In file included from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gSummaryChart.h:28: error: expected &#8216;)&#8217; before &#8216;label&#8217;
In file included from daily.h:21,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gSummaryChart.h:41: error: &#8216;ChannelID&#8217; has not been declared
Graphs/gSummaryChart.h:41: error: &#8216;QColor&#8217; has not been declared
Graphs/gSummaryChart.h:65: error: &#8216;Qt&#8217; has not been declared
Graphs/gSummaryChart.h:65: error: ISO C++ forbids declaration of &#8216;Orientation&#8217; with no type
Graphs/gSummaryChart.h:65: error: expected &#8216;;&#8217; before &#8216;m_orientation&#8217;
Graphs/gSummaryChart.h:67: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gSummaryChart.h:67: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:68: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gSummaryChart.h:68: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:69: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gSummaryChart.h:69: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:71: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gSummaryChart.h:71: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:72: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gSummaryChart.h:72: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:73: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
Graphs/gSummaryChart.h:73: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:74: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
Graphs/gSummaryChart.h:74: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:75: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
Graphs/gSummaryChart.h:75: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:76: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
Graphs/gSummaryChart.h:76: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gSummaryChart.h:82: error: &#8216;QString&#8217; does not name a type
Graphs/gSummaryChart.h:85: error: &#8216;qint64&#8217; does not name a type
Graphs/gSummaryChart.h:89: error: &#8216;qint64&#8217; does not name a type
Graphs/gSummaryChart.h:98: error: &#8216;QKeyEvent&#8217; has not been declared
Graphs/gSummaryChart.h:101: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gSummaryChart.h:104: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gSummaryChart.h:107: error: &#8216;QMouseEvent&#8217; has not been declared
Graphs/gSummaryChart.h: In member function &#8216;void SummaryChart::addSlice(int, int, SummaryType, EventDataType)&#8217;:
Graphs/gSummaryChart.h:43: error: &#8216;m_codes&#8217; was not declared in this scope
Graphs/gSummaryChart.h:44: error: &#8216;m_colors&#8217; was not declared in this scope
Graphs/gSummaryChart.h:45: error: &#8216;m_type&#8217; was not declared in this scope
Graphs/gSummaryChart.h:47: error: &#8216;m_typeval&#8217; was not declared in this scope
In file included from daily.h:27,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gLineChart.h: At global scope:
Graphs/gLineChart.h:23: error: ISO C++ forbids declaration of &#8216;QColor&#8217; with no type
Graphs/gLineChart.h:23: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;col&#8217;
Graphs/gLineChart.h:44: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gLineChart.h:44: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gLineChart.h:47: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gLineChart.h:47: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gLineChart.h:51: error: &#8216;QColor&#8217; does not name a type
Graphs/gLineChart.h: In member function &#8216;virtual bool AHIChart::isEmpty()&#8217;:
Graphs/gLineChart.h:40: error: &#8216;m_data&#8217; was not declared in this scope
Graphs/gLineChart.h: At global scope:
Graphs/gLineChart.h:67: error: expected &#8216;)&#8217; before &#8216;code&#8217;
Graphs/gLineChart.h:105: error: &#8216;ChannelID&#8217; has not been declared
Graphs/gLineChart.h:105: error: &#8216;QColor&#8217; has not been declared
In file included from daily.h:27,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gLineChart.h:108: error: &#8216;ChannelID&#8217; has not been declared
Graphs/gLineChart.h:111: error: &#8216;ChannelID&#8217; has not been declared
Graphs/gLineChart.h:117: error: &#8216;QColor&#8217; does not name a type
Graphs/gLineChart.h:127: error: &#8216;QPoint&#8217; does not name a type
Graphs/gLineChart.h:131: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gLineChart.h:131: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gLineChart.h:132: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gLineChart.h:132: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gLineChart.h:133: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
Graphs/gLineChart.h:133: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
Graphs/gLineChart.h:134: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
Graphs/gLineChart.h:134: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
In file included from daily.h:27,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gLineChart.h: In member function &#8216;void gLineChart::addPlot(int, int, bool)&#8217;:
Graphs/gLineChart.h:105: error: &#8216;m_codes&#8217; was not declared in this scope
Graphs/gLineChart.h:105: error: &#8216;m_colors&#8217; was not declared in this scope
Graphs/gLineChart.h:105: error: &#8216;m_enabled&#8217; was not declared in this scope
In file included from daily.h:27,
                 from mainwindow.h:17,
                 from main.cpp:18:
Graphs/gLineChart.h:105: error: &#8216;m_square&#8217; was not declared in this scope
Graphs/gLineChart.h: In member function &#8216;bool gLineChart::plotEnabled(int)&#8217;:
Graphs/gLineChart.h:108: error: &#8216;m_enabled&#8217; was not declared in this scope
Graphs/gLineChart.h: In member function &#8216;void gLineChart::setPlotEnabled(int, bool)&#8217;:
Graphs/gLineChart.h:111: error: &#8216;m_enabled&#8217; was not declared in this scope
In file included from mainwindow.h:17,
                 from main.cpp:18:
daily.h: At global scope:
daily.h:40: error: expected class-name before &#8216;{&#8217; token
daily.h:41: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
daily.h:43: error: expected &#8216;;&#8217; before &#8216;public&#8217;
daily.h:78: error: &#8216;QDate&#8217; has not been declared
daily.h:84: error: &#8216;QDate&#8217; does not name a type
daily.h:96: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
daily.h:98: error: &#8216;QString&#8217; does not name a type
daily.h:104: error: expected &#8216;:&#8217; before &#8216;slots&#8217;
daily.h:111: error: expected primary-expression before &#8216;void&#8217;
daily.h:111: error: ISO C++ forbids declaration of &#8216;slots&#8217; with no type
daily.h:111: error: expected &#8216;;&#8217; before &#8216;void&#8217;
daily.h:152: error: ISO C++ forbids declaration of &#8216;QUrl&#8217; with no type
daily.h:152: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
daily.h:161: error: &#8216;QTreeWidgetItem&#8217; has not been declared
daily.h:183: error: &#8216;QTableWidgetItem&#8217; has not been declared
daily.h:188: error: &#8216;QTableWidgetItem&#8217; has not been declared
daily.h:234: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
daily.h:245: error: &#8216;QDate&#8217; has not been declared
daily.h:250: error: &#8216;QDate&#8217; has not been declared
daily.h:255: error: &#8216;QDate&#8217; has not been declared
daily.h:261: error: &#8216;QTreeWidget&#8217; has not been declared
daily.h:270: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
daily.h:270: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
daily.h:271: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
daily.h:271: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
daily.h:272: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
daily.h:272: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
daily.h:273: error: ISO C++ forbids declaration of &#8216;QHash&#8217; with no type
daily.h:273: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
daily.h:274: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
daily.h:274: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
daily.h:275: error: ISO C++ forbids declaration of &#8216;QGLContext&#8217; with no type
daily.h:275: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
daily.h:277: error: ISO C++ forbids declaration of &#8216;QList&#8217; with no type
daily.h:277: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
daily.h:287: error: &#8216;QDate&#8217; does not name a type
daily.h:288: error: ISO C++ forbids declaration of &#8216;QMenu&#8217; with no type
daily.h:288: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
daily.h:292: error: ISO C++ forbids declaration of &#8216;QHBoxLayout&#8217; with no type
daily.h:292: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
daily.h:293: error: ISO C++ forbids declaration of &#8216;QLabel&#8217; with no type
daily.h:293: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
daily.h:294: error: ISO C++ forbids declaration of &#8216;QIcon&#8217; with no type
daily.h:294: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
daily.h:295: error: ISO C++ forbids declaration of &#8216;QIcon&#8217; with no type
daily.h:295: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
daily.h: In member function &#8216;Layer* Daily::AddCPAP(Layer*)&#8217;:
daily.h:278: error: &#8216;CPAPData&#8217; was not declared in this scope
daily.h: In member function &#8216;Layer* Daily::AddSTAGE(Layer*)&#8217;:
daily.h:279: error: &#8216;STAGEData&#8217; was not declared in this scope
daily.h: In member function &#8216;Layer* Daily::AddOXI(Layer*)&#8217;:
daily.h:280: error: &#8216;OXIData&#8217; was not declared in this scope
In file included from mainwindow.h:18,
                 from main.cpp:18:
overview.h: At global scope:
overview.h:31: error: expected class-name before &#8216;{&#8217; token
overview.h:32: error: ISO C++ forbids declaration of &#8216;Q_OBJECT&#8217; with no type
overview.h:34: error: expected &#8216;;&#8217; before &#8216;public&#8217;
overview.h:54: error: &#8216;QDate&#8217; has not been declared
overview.h:54: error: &#8216;QDate&#8217; has not been declared
overview.h:59: error: expected &#8216;;&#8217; before &#8216;(&#8217; token
In file included from mainwindow.h:18,
                 from main.cpp:18:
overview.h:65: error: ISO C++ forbids declaration of &#8216;QVector&#8217; with no type
overview.h:65: error: expected &#8216;;&#8217; before &#8216;<&#8217; token
overview.h:68: error: &#8216;QString&#8217; has not been declared
overview.h:70: error: expected &#8216;:&#8217; before &#8216;slots&#8217;
overview.h:74: error: expected primary-expression before &#8216;private&#8217;
overview.h:74: error: ISO C++ forbids declaration of &#8216;slots&#8217; with no type
overview.h:74: error: expected &#8216;;&#8217; before &#8216;private&#8217;
overview.h:87: error: ISO C++ forbids declaration of &#8216;QDate&#8217; with no type
overview.h:87: error: expected &#8216;,&#8217; or &#8216;...&#8217; before &#8216;&&#8217; token
overview.h:110: error: ISO C++ forbids declaration of &#8216;QHBoxLayout&#8217; with no type
overview.h:110: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
overview.h:112: error: ISO C++ forbids declaration of &#8216;QIcon&#8217; with no type
overview.h:112: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
overview.h:113: error: ISO C++ forbids declaration of &#8216;QIcon&#8217; with no type
overview.h:113: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
overview.h:116: error: &#8216;QDateEdit&#8217; has not been declared
overview.h:116: error: &#8216;QDate&#8217; has not been declared
In file included from oximetry.h:14,
                 from mainwindow.h:19,
                 from main.cpp:18:
./qextserialport/qextserialport.h:182: error: expected initializer before &#8216;:&#8217; token
make: *** [main.o] Error 1

```Since it worked for you, I'm going to assume my OS is probably missing something that is needed.

EDIT: To help others, I updated the tutorial with your additional information:
[**Tutorial for installing SourceForge SleepyHead CPAP/BiPAP (Sleep Apnea) software **]("http://ubuntuforums.org/showthread.php?p=11755984#post11755984")

---

### Post by rocksockdoc on 2012-03-11
FYI ... a friend of mine who is a lifelong developer was able to compile SleepyHead on Ubuntu Lucid 10.04 (development workstation) using only these three commands:
```
git clone git://sleepyhead.git.sourceforge.net/gitroot/sleepyhead/sleepyhead
qmake
make
./SleepyHead                      
```So I wholly re-edited this tutorial to help others who are also on Lucid 10.04:
[Tutorial for installing SourceForge SleepyHead CPAP/BiPAP (Sleep Apnea) software]("http://ubuntuforums.org/showthread.php?t=1937358")

If you are on Ubuntu Lucid 10.04, it would be nice if you can confirm the steps to obtain, compile, & run are as shown below:
```
$ sudo apt-get install git-core qt4-dev-tools libqt4-opengl-dev libqtwebkit-dev zlib1g-dev 
$ git clone git://sleepyhead.git.sourceforge.net/gitroot/sleepyhead/sleepyhead
$ qmake
$ make
$ ./SleepyHead
```

---

