---
title: "HOW TO: Installing mail-notification 5.4"
date: 2010-03-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Francewhoa on 2010-03-14
**Requirements**
* Ubuntu 8.04.x LTS Desktop Edition 32 bits

**Steps**
* Download below attached 'extract-me.zip' file. This file is hard to find on the internet so I attached it below. 

* Extract the 'extract-me.zip' file.

* Open the folder 'The deb package is inside this folder'.

* Right click on 'mail-notification_5.4-0~getdeb1_i386.deb' file.

* Select 'Install with GDebi...'

* Following instructions on screen. Ignore the warning about older version available.

* Navigate to the following menu System -> Preferences -> Mail Notification

* If a popup ask about a keyring thing. Follow instruction at [http://ubuntuforums.org/showthread.php?t=1305302](http://ubuntuforums.org/showthread.php?t=1305302)

* The following is optional. If you want to always display the icon in the toolbar. Type in the following command in TERMINAL
    ```
open gconf-editor
```* Navigate to apps, mail-notification, and check always-display-icon.

---

### Post by blueswerks on 2010-10-06
Thank you! Just what I needed.

---

### Post by tinchs on 2011-01-06
I get this error:

Dependency is not satisfiable: libcamel1.2-11 (>= 2.22.2) 

Could you help me?

---

