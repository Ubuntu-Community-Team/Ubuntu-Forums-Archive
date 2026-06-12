---
title: "problem with configure"
date: 2012-05-03
forum: Packaging and Compiling Programs
---

### Post by forsubhi on 2012-05-03
I tried to install gedit using source code , but I face the following error during ./configure 


```
configure: error: Package requirements (
        libxml-2.0 >= 2.5.0
        glib-2.0 >= 2.28.0
        gthread-2.0 >= 2.13.0
        gio-2.0 >= 2.26.0
        gtk+-3.0 >= 3.1.6
        gtksourceview-3.0 >= 3.0.0
        libpeas-1.0 >= 0.7.3
        libpeas-gtk-1.0 >= 1.1.0
        gsettings-desktop-schemas
) were not met:

No package 'libxml-2.0' found
No package 'gtk+-3.0' found
No package 'gtksourceview-3.0' found
No package 'libpeas-1.0' found
No package 'libpeas-gtk-1.0' found
No package 'gsettings-desktop-schemas' found
```

How can I update these package , I tried sudo apt-get install , but it doesn't work ?

---

### Post by oldos2er on 2012-05-03
Moved to Packaging and Compiling Programs.

You're missing some needed dependencies. Try running ```
sudo apt-get build-dep gedit
``` then try ./configure again.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

