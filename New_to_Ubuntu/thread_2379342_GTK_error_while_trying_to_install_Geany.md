---
title: "GTK error while trying to install Geany"
date: 2017-12-04
forum: New to Ubuntu
---

### Post by bmanche on 2017-12-04
Hey all.

Very new to linux/Ubuntu and have a question regarding a failure on the ./configure command when trying to install the Geany editor.  I was able to eventually get it installed using apt-get, however I'd like to understand why it failed trying to install it per the Geany documentation.  The docs say "You will need the GTK (>= 2.24) libraries and their dependencies."  After downloading, extracting and changing to the correct directory, I tried ./configure and got 

configure: error: Package requirements (gtk+-2.0 >= 2.24 glib-2.0 >= 2.32 gio-2.0 >= 2.32 gmodule-no-export-2.0) were not met:
No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'gio-2.0' found
No package 'gmodule-no-export-2.0' found

I just downloaded and installed Ubuntu today from the Ubuntu site.  I typed dpkg -l | grep libgtk and the output looks like 2.24.31 and 3.22.11 are present so I don't understand why they weren't found/used.

Any assistance is appreciated.

---

### Post by deadflowr on 2017-12-04
To install and compile from source you need the -dev packages.
-dev packages contain the header files you needed.
Specifically in this case you needed libgtk2.0-dev
It's installable through Ubuntu's archives.

For naught though if you were able to install from the Ubuntu archives.
(Unless you really need the latest from geany.

---

### Post by bmanche on 2017-12-04
Thanks.  I don't need the latest.  I just wanted to understand why the process failed and you provided that info.  I thought it might come up in attempts to install other programs as well.

Much appreciated.

---

### Post by Lewis Balentine on 2018-08-02
Actually that does NOT resolve the issue.
Even with [COLOR=#000000] libgtk2.0-dev one still gets the same error as of geany version 1.33
Sadly, something is still missing ....

[/COLOR]configure: error: Package requirements (gtk+-2.0 >= 2.24 glib-2.0 >= 2.32 gio-2.0 >= 2.32 gmodule-no-export-2.0) were not met:


No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'gio-2.0' found
No package 'gmodule-no-export-2.0' found

---

