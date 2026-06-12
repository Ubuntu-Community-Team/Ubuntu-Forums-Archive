---
title: "libnotify in qt4"
date: 2011-01-30
forum: Programming Talk
---

### Post by Woody1987 on 2011-01-30
I am creating my app in qt-creator. In my mainwindow class I have included libnotifymm.

```

#include <libnotifymm-1.0/libnotifymm.h>

```

But I get an error.
> 
/usr/include/libnotifymm-1.0/libnotifymm.h:33: error: glibmm.h: No such file or directory


I do have libglibmm installed. I tried modifying libnotifymm.h to point to glibmm.h as such:
```

from:
#include <glibmm.h>
to:
#include <glibmm-2.4/glibmm.h>

```

This worked, but I then get another error within glibmm.h
> 
/usr/include/glibmm-2.4/glibmm.h:80: error: glibmmconfig.h: No such file or directory


I cant find this file anywhere. What do I do?

Also are these even the correct libraries to use, in order to use ubuntu notifyosd in gnome within a qt app?

---

### Post by Zugzwang on 2011-01-30
If you have a look at the [file list]("http://packages.ubuntu.com/maverick/amd64/libnotifymm-dev/filelist") of "libnotifymm-dev", the development package of the library you want to use, you will see that there's a "pc" file in the package. These are used by the pkgconfig tool to supply the compiler and linker with paths to the libraries and include directories.

As far as I know, qtcreator supports only one type of make system: qmake. This makes it easy to give you advice. In order to use the library, you will need to tell qmake to call pkgconfig for that library. Support for this task is built in using the PKGCONFIG config variable. Since the name of the library seems to be "libnotifymm-1.0" (this is the name of the .pc file in the package), add the following line to your .pro project file in qtcreator:
```

PKGCONFIG += libnotifymm-1.0

```

You will need to revert your changes to the #include line in your program. I am also not sure whether to drop that "-1.0" from the library name or not, so try it out.

---

### Post by Woody1987 on 2011-01-30
I tried that with and without the "-1.0" and I get the same error.

---

### Post by Woody1987 on 2011-01-30
I found and example here:
[http://wiki.forum.nokia.com/index.php/How_to_show_notification_from_Qt_aplication_in_Maemo_5]("http://wiki.forum.nokia.com/index.php/How_to_show_notification_from_Qt_aplication_in_Maemo_5")

It is for maemo but it uses libnotifymm. It shows a .pro file with
```

CONFIG += link_pkgconfig
PKGCONFIG += libnotifymm-1.0 gtkmm-2.4

```

But this gives me alot of errors.

---

### Post by Woody1987 on 2011-01-30
I have it working by using QProcess and calling notify-send. Its not elegant but it works.

---

### Post by Zugzwang on 2011-01-31
> **Woody1987 said:**
> But this gives me alot of errors.

Perhaps you can copy&paste the errors here?

---

