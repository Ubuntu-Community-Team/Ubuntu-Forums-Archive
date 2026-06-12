---
title: "update manager problem"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by HunkieChan on 2008-09-14
bogofilter-bdb

this app is sitting in my update manager that i can't update. its been there for last several months. i cant check it to update. what is this app and how can i remove it or update it ? 

thank you

---

### Post by prshah on 2008-09-14
> **HunkieChan said:**
> bogofilter-bdb

this app is sitting in my update manager that i can't update.

You may have added a custom repository to your software sources, in which the above software was available; that repository may be offline now. Here's what you can do to check:

Open a terminal (Applications-Accessories-Terminal), and give the command ```
sudo apt-get update
``` You will get lots of output, check it for errors manually.

If you find a certain repository is giving errors, note it's name and then comment it out from the "/etc/apt/sources.list" file. You can edit the file with the command ```
gksudo gedit /etc/apt/sources.list
``` which can be given either in the terminal or the Alt+F2 ("run") box.

---

### Post by HunkieChan on 2008-09-14
i dont get any error. all of them were hit or ign ,any suggestion ?

---

