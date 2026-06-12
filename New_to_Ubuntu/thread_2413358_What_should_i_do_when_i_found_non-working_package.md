---
title: "What should i do when i found non-working package?"
date: 2019-02-24
forum: New to Ubuntu
---

### Post by cm0k on 2019-02-24
I have latest stable version of Ubuntu.
I'm installing some package from the official repo.
I'm starting it and... it can't be started.... some libs are not found... some dependencies are not met... etc.
Works as charm If I download the latest version from the developer's page.

Should I report outdated package somewhere? Should I create new packages and provide it to the community? Should I develop some automation to check if this package is installed correctly and can be run? Where to start?

Last time it was Anki... but often can be found other packages with broken dependencies.

---

### Post by wildmanne39 on 2019-02-24
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by again? on 2019-02-24
First thing to do is find out if others are having similar problems installing or running said package.
eg I had no problems installing/running anki.
I don't know your experience, but most often dependency problems are caused by installing third party ppas.

You should post your terminal output showing dependency problems and others will check
if they have the same problem.

---

### Post by cm0k on 2019-02-25
okay.
I created VirtualBox machine and installed there Ububtu 18.10.
At system i installed Anki and all it's dependencies:
```
sudo apt install anki
```

Then started the anki. I got the message:
> You are using Qt version 5.11.1.  Anki has only been tested upstream with version Qt 5.9.x.  Upstream suggests only using version Qt 5.9.x, and a standalone version containing the required libraries can be downloaded from the Anki website.  Continuing with this Debian version could potentially lead to loss of data (though this is unlikely).  Are you sure you want to continue?
I click "Yes"

I got an error:
```
Error during startup:
 Traceback (most recent call last):
   File "/usr/share/anki/aqt/main.py", line 50, in __init__
     self.setupUI()
   File "/usr/share/anki/aqt/main.py", line 75, in setupUI
     self.setupMainWindow()
   File "/usr/share/anki/aqt/main.py", line 585, in setupMainWindow
     tweb = self.toolbarWeb = aqt.webview.AnkiWebView()
   File "/usr/share/anki/aqt/webview.py", line 114, in __init__
     self.focusProxy().installEventFilter(self)
 AttributeError: 'NoneType' object has no attribute 'installEventFilter'
 
```

I click "Ok".
Errors windows are closed. Application is running. Nothing happens.
In console i can see following:

```
cm0k@cm0k-VirtualBox:~$ anki
Hardware acceleration disabled.
mpv not found, reverting to mplayer
```

I'm pressing Ctrl+C to stop the application. Result:

```
cm0k@cm0k-VirtualBox:~$ anki
Hardware acceleration disabled.
mpv not found, reverting to mplayer



^CException ignored in: <module 'threading' from '/usr/lib/python3.6/threading.py'>
Traceback (most recent call last):
  File "/usr/lib/python3.6/threading.py", line 1294, in _shutdown
    t.join()
  File "/usr/lib/python3.6/threading.py", line 1056, in join
    self._wait_for_tstate_lock()
  File "/usr/lib/python3.6/threading.py", line 1072, in _wait_for_tstate_lock
    elif lock.acquire(block, timeout):
KeyboardInterrupt

```

At my main machine I just downloaded latest code from official webpage and it works perfectly.
Ofcourse I can try to install old QT. But i believe it'll case numerous problems with other applications.
I will be glad to provide any other details.

Packages versions:
 ```
[B]
cm0k@cm0k-VirtualBox:~$ dpkg -l | grep anki[/B]
ii  anki                                       2.1.0+dfsg-1                               all          extensible flashcard learning program
**cm0k@cm0k-VirtualBox:~$ dpkg -l | grep qt**
ii  libqt5core5a:amd64                         5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 core module
ii  libqt5dbus5:amd64                          5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 D-Bus module
ii  libqt5designer5:amd64                      5.11.1-5ubuntu1                            amd64        Qt 5 designer module
ii  libqt5gui5:amd64                           5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 GUI module
ii  libqt5help5:amd64                          5.11.1-5ubuntu1                            amd64        Qt 5 help module
ii  libqt5network5:amd64                       5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 network module
ii  libqt5positioning5:amd64                   5.11.1+dfsg-4                              amd64        Qt Positioning module
ii  libqt5printsupport5:amd64                  5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 print support module
ii  libqt5qml5:amd64                           5.11.1-6build1                             amd64        Qt 5 QML module
ii  libqt5quick5:amd64                         5.11.1-6build1                             amd64        Qt 5 Quick library
ii  libqt5quickwidgets5:amd64                  5.11.1-6build1                             amd64        Qt 5 Quick Widgets library
ii  libqt5sql5:amd64                           5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 SQL module
ii  libqt5sql5-sqlite:amd64                    5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 SQLite 3 database driver
ii  libqt5svg5:amd64                           5.11.1-2                                   amd64        Qt 5 SVG module
ii  libqt5test5:amd64                          5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 test module
ii  libqt5webchannel5:amd64                    5.11.1-3                                   amd64        Web communication library for Qt
ii  libqt5webengine-data                       5.11.1+dfsg-2ubuntu4                       all          Web content engine library for Qt - Data
ii  libqt5webengine5:amd64                     5.11.1+dfsg-2ubuntu4                       amd64        Web content engine library for Qt
ii  libqt5webenginecore5:amd64                 5.11.1+dfsg-2ubuntu4                       amd64        Web content engine library for Qt - Core
ii  libqt5webenginewidgets5:amd64              5.11.1+dfsg-2ubuntu4                       amd64        Web content engine library for Qt - Widget
ii  libqt5widgets5:amd64                       5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 widgets module
ii  libqt5xml5:amd64                           5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 XML module
ii  python3-pyqt5                              5.11.2+dfsg-1ubuntu2                       amd64        Python 3 bindings for Qt5
ii  python3-pyqt5.qtwebchannel                 5.11.2+dfsg-1ubuntu2                       amd64        Python 3 bindings for Qt5's WebChannel module
ii  python3-pyqt5.qtwebengine                  5.11.2+dfsg-1ubuntu2                       amd64        Python 3 bindings for Qt5's WebEngine module
ii  qt5-gtk-platformtheme:amd64                5.11.1+dfsg-7ubuntu2                       amd64        Qt 5 GTK+ 3 platform theme
ii  qttranslations5-l10n                       5.11.1-2                                   all          translations for Qt 5

```

---

### Post by again? on 2019-02-25
Yeah sorry I thought you were using 18.04 and I get your errors on 18.10
This page explains the anki bug with qt versions. [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=855942](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=855942)

Maybe the best you could do would be to give a quick guide to others on 18.10 how to get and install the latest anki.

In reference to "What should i do when i found non-working package?"
Firstly, check the packages bug page. [https://bugs.launchpad.net/ubuntu/+source/anki](https://bugs.launchpad.net/ubuntu/+source/anki)
**_[Reporting Bugs]("https://help.ubuntu.com/community/ReportingBugs")_**

---

### Post by cm0k on 2019-02-26
thank you. i'll check links.

> Maybe the best you could do would be to give a quick guide to others on 18.10 how to get and install the latest anki.
i believe everyone can google, download and unpack =) 
my idea is that if we have package manager - let it do the job properly.

---

### Post by again? on 2019-02-26
True, you can even google "What should i do when i found non-working package?" :p

---

### Post by oldrocker99 on 2019-02-26
You can try downloading the source code here, [https://github.com/dae/anki](https://github.com/dae/anki) and compile it, which **should** give you a working installation.

Here's a tutorial on getting started with compilation. [https://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/](https://www.howtogeek.com/105413/how-to-compile-and-install-from-source-on-ubuntu/).

It really isn't too hard, usually, and the program will be customized for your system.

---

