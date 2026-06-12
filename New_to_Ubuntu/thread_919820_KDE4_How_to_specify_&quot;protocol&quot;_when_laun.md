---
title: "KDE4 How to specify &quot;protocol&quot; when launching kate editor?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by gregphil on 2008-09-14
When in a terminal as the root user I can't seem to launch most programs, instead I get errors something like:

/home/greg # /usr/lib/kde4/bin/kate
No protocol specified
kate: cannot connect to X server :0.0

Why?  
***********************************************************************
Can I do something to fix this?, I can launch kate from a terminal as a normal user, but then I don't have the privledge needed to edit configuration files.  If I use the kdesu command to invoke the kate editor, the terminal fills up will messages (which looks stupid and, since back scrolling is broken in the KDE4 konsole right now, is a real pain):
                                                                               
/home/greg $ kdesu /usr/lib/kde4/bin/kate
passprompt                               


kate(6891): createDoc

kate(6891) KateSessionManager::KateSessionManager: LOCAL SESSION DIR:  "/root/.kde4/share/apps/kate/sessions"                                                           

kate(6891) KateApp::initKate: Setting KATE_PID: ' 6891 '

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: false

kate(6891) KateMainWindow::KateMainWindow: **************************************************************************** 0x81ba1c0                                       

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: false

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: false

kate(6891) KateApp::startupKate: KateApplication::init finished successful

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: true

kate(6891) KMimeTypeFactory::parseMagic: Now parsing  "/usr/share/mime/magic"

kate(6891) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "Untitled"

kate(6891) KateDocManager::slotDocumentNameChanged: docname changed:  "Untitled" -----> "smb.conf"

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: false

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: true

kate(6891) KateDocManager::slotDocumentNameChanged: docname changed:  "smb.conf" -----> "Untitled"

kate(6891): deleting document with name: "Untitled"

kate(6891): QVariant(QString, "Untitled") REMOVING

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: false

kate(6891) KateViewDocumentProxyModel::slotRowsAboutToBeRemoved: **************

kate(6891): createDoc

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: false

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: false

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: false

kate(6891) KateViewDocumentProxyModel::updateBackgrounds: true

QFSFileEngine::open: No file name specified

QThreadStorage: Thread 0x804b3c8 exited after QThreadStorage 2147483641 destroyed

QThreadStorage: Thread 0x804b3c8 exited after QThreadStorage 2147483643 destroyed


***************************
Isn't there some simple way to invoke the kate editor with root privledges?

Thank You.

---

### Post by linuxford on 2009-01-07
I'm not sure, I use Gnome, but maybe try

```
System~>Admin~>UserAndGroups
```

then unlock, and then change so that one of your normal users has adminstrative privileges?

---

### Post by mgranet on 2009-01-07
kdesu is a graphical frontend to su. When in the konsole, you should just run ```
sudo *command*
```

EDIT: @linuxford: Dang, talk about digging up the old posts....

---

### Post by sayakb on 2009-01-07
use **kdesudo** or simply **sudo** as user:
```
$ kdesudo kate
```

---

