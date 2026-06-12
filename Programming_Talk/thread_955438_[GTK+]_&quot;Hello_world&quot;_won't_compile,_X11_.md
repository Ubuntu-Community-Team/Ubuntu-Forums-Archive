---
title: "[GTK+] &quot;Hello world&quot; won't compile, X11 error"
date: 2008-10-22
forum: Programming Talk
---

### Post by roccivic on 2008-10-22
Trying to build "Hello world" from the official GTK+ 2.0 tutorial.
Am I missing a library or something?

Thanks for looking.
Rouslan

```
chc@chc-pc:/media/disk/source/current$ make gui
gcc -Wall -g hello.c -o hello-gtk `pkg-config --cflags gtk+-2.0` \ `pkg-config --libs gtk+-2.0`
gcc:  -lgtk-x11-2.0: No such file or directory
make: *** [gui] Error 1


chc@chc-pc:/media/disk/source/current$ su -c "apt-get install libx11-dev libx11-6 gnome-devel libgtk2.0-dev"
Password: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx11-dev is already the newest version.
libx11-6 is already the newest version.
gnome-devel is already the newest version.
libgtk2.0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

```

---

### Post by WW on 2008-10-22
Remove that backslash from the gcc command in your Makefile.  That is, change this:
```

gcc -Wall -g hello.c -o hello-gtk `pkg-config --cflags gtk+-2.0` \ `pkg-config --libs gtk+-2.0`

```
to this
```

gcc -Wall -g hello.c -o hello-gtk `pkg-config --cflags gtk+-2.0` `pkg-config --libs gtk+-2.0`

```
or even this
```

gcc -Wall -g hello.c -o hello-gtk `pkg-config --cflags --libs gtk+-2.0`

```
The backslash is in the tutorial to indicate that the command is really one long line. However, the way you have used it, an extra space is tacked on to the beginning of the argument that is created by the following pkg-config command.  So instead of "-lgtk-x11-2.0", you are giving gcc the argument " -gtk-x11-2.0". Because the first character is not -, gcc treats it as a file name, and reports the error that it can't find it ("No such file or directory.").

---

### Post by roccivic on 2008-10-22
You rock!
Thanks :)

---

