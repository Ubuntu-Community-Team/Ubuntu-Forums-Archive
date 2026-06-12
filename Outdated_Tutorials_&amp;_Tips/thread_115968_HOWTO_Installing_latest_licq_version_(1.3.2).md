---
title: "HOWTO: Installing latest licq version (1.3.2)"
date: 2006-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by ahessling on 2006-01-11
Hi!

For all the users that like [licq's]("http://www.licq.org") features (for example reading away messages especially from Miranda users correctly), I provided some .deb files that I backported from Dapper.
You can download them at [http://www.andrehessling.de/linux/licq-1.3.2/](http://www.andrehessling.de/linux/licq-1.3.2/)

You will at least need licq_1.3.2-5_i386.deb and licq-plugin-qt_1.3.2-5_i386.deb since they depend on each other.

Install licq by issuing the following line as root, but you should as always backup your existing licq directory (~/.licq) and remove an older licq version before (sudo apt-get remove licq):
```
sudo dpkg -i licq_1.3.2-5_i386.deb licq-plugin-qt_1.3.2-5_i386.deb
```

If you want to use the nice kde plugin, you have of course to install it and then activate it in licq's plugin manager. After that restart licq with the line 
```
licq -p kde-gui
```
and you should receive a nicer looking interface.

I hope that helps!

Regards,
Andr&#233;

---

### Post by Pizza the Hutt on 2006-03-03
How do I install the kde-plugin and where do I find the plugin manager?

---

### Post by maulattu on 2006-03-03
it works! nice howto, thansk ;)

---

### Post by ahessling on 2006-03-03
Pizza the Hutt:
You have to download this file:
[http://www.andrehessling.de/linux/licq-1.3.2/licq-plugin-kde_1.3.2-5_i386.deb](http://www.andrehessling.de/linux/licq-1.3.2/licq-plugin-kde_1.3.2-5_i386.deb)

And issue the following command as root:
```
dpkg -i licq-plugin-kde_1.3.2-5_i386.deb
```

Then you can find an entry in licq's main menu where you can enable some plugins. There you have to enable this kde plugin and restart licq on a console  using this line:
```
licq -p kde-gui
```

This will ensure that the kde plugin is loaded before the qt plugin and then you should be able to just start licq without the extra parameter -p kde-gui since licq saves the default frontend.

---

