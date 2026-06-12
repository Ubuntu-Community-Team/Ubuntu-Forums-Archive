---
title: "deb packaging does not finish; permission problem?"
date: 2007-07-09
forum: Programming Talk
---

### Post by tak1150 on 2007-07-09
Hi,

I am trying to make a deb package of "gnome-chemistry-utils" and after I setup the debian files according to [this site]("http://www.debian.org/doc/maint-guide/") and run
```
dpkg-buildpackage -rfakeroot
```

I get this error message. Is this a permission problem? I shouldn't have to run it as root since I am not installing this. Any input would be appreciated.
```

make[4]: Entering directory `/home/tak/gcu_pkg/gnome-chemistry-utils-0.8.1'
/usr/bin/update-mime-database /home/tak/gcu_pkg/share/mime
/usr/bin/update-mime-database: I don't have write permission on /home/tak/gcu_pkg/share/mime.
Try rerunning me as root.

make[4]: *** [install-data-hook] Aborted (core dumped)
make[4]: Leaving directory `/home/tak/gcu_pkg/gnome-chemistry-utils-0.8.1'
make[3]: *** [install-data-am] Error 2
make[3]: Leaving directory `/home/tak/gcu_pkg/gnome-chemistry-utils-0.8.1'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/tak/gcu_pkg/gnome-chemistry-utils-0.8.1'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/tak/gcu_pkg/gnome-chemistry-utils-0.8.1'
make: *** [install] Error 2
tak@tak1150:~/gcu_pkg/gnome-chemistry-utils-0.8.1$ 
```

I have attached the "rules" file

---

