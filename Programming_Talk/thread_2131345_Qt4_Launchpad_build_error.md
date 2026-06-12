---
title: "Qt4 Launchpad build error"
date: 2013-04-01
forum: Programming Talk
---

### Post by alenn on 2013-04-01
Hello
I made debian package using debuild and pbuilder on my computer and everything is ok, but I try to build mine application on Launchpad I get error about missing qmake. Here is complete build log: [http://pastebin.com/3ini4chU](http://pastebin.com/3ini4chU)
Can anyone help me.

---

### Post by schragge on 2013-04-02
[size=-1]*Double-post deleted*[/size]

---

### Post by schragge on 2013-04-02
Try to explicitly specify buildsystem in debian/rules:
```

%:
       dh $@ [COLOR=red]--buildsystem=qmake_qt4[/COLOR]

```
or, just for the dh_auto_configure step
```

override_dh_auto_configure:
       dh_auto_configure [COLOR=red]-Sqmake_qt4[/COLOR]

```
Alternatively, you may try to put this at the start of your debian/rules
```
export PATH := /usr/share/qt4/bin:$(PATH)
```

---

### Post by alenn on 2013-04-02
Thank you a lot, I used your first solution and it worked.

---

