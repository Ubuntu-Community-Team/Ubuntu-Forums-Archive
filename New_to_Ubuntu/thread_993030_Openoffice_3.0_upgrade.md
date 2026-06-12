---
title: "Openoffice 3.0 upgrade"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by Ant-eater on 2008-11-25
Total ubuntu beginner posting here,

Just installed Intrepid and I got the majority of my system running nicely, but I'm having a problem with OpenOffice. First v2.4.1 was already installed and I upgraded it to 3.0 using a repository(?). Later on I installed Japanese writing support. But it deleted some of my Openoffice files in the progress. Then i tried to reinstall 2.4.1 from the add/remove section under applications. Which didn't work. I proceeded by removing all Openoffice packages. After that 2.4.1 installed just fine, but i can't get it to upgrade to 3.0 anymore.:confused:

Help would be greatly appreciated :)

---

### Post by fooman on 2008-11-25
do you still have the openoffice3 repository enabled?

check this guide:

[http://ubuntuforums.org/showthread.php?t=987181](http://ubuntuforums.org/showthread.php?t=987181)

---

### Post by HellNoire on 2008-11-25
Add the OpenOffice.org 3 repositories
Go to System -> Administration -> Software Sources
Go to the second tab, "Third-Party Software," click on the "Add" button, and paste the line below...

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

Close, reload sources when asked. Then open update manager and update!

Walkthough (c) Softpedia

---

### Post by Ant-eater on 2008-11-25
Already tried that, it didn't work, when i click reload it doesn't give me any updates

---

### Post by Soriano on 2008-11-25
Hmmmmm.  Try removing the Repository and then reloading it.  If that doesn't work I'd say go and download the .deb file from OO website:

[http://download.openoffice.org/other.html#en-US](http://download.openoffice.org/other.html#en-US)

Then add the repo again to be sure you get updates.

---

