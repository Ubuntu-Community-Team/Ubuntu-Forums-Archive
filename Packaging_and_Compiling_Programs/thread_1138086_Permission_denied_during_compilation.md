---
title: "Permission denied during compilation"
date: 2009-04-26
forum: Packaging and Compiling Programs
---

### Post by lovinglinux on 2009-04-26
I'm trying to compile my first package, since the program is not offered for Jaunty and I want it really bad. The application is [Gimmie](http://beatniksoftware.com/gimmie/Main_Page).

Well, I did all necessary steps, but when I do checkinstall I get this error and the package is not created:

```

mkdir -p -- /usr/local/share/icons/hicolor/16x16/apps
mkdir: cannot create directory `/usr/local/share/icons/hicolor/16x16': Permission denied
```

How can I solve this?

---

### Post by andrewsomething on 2009-04-26
sudo checkinstall

---

