---
title: "GTK+ Problems"
date: 2007-02-24
forum: Programming Talk
---

### Post by Skyler on 2007-02-24
Hi,
I'm trying to install GTK+ on my Edgy system. I've gotten as far as trying to compile cairo. It says it can't find freetype and fontconfig, despite the fact that apt-get tells me that they are already installed. Can anyone tell me what's going on?

---

### Post by po0f on 2007-02-24
Skyler,

GTK+ 2.0 is already installed on your system, you just need the header files:

```
[font="Courier New"]$ sudo apt-get **install** libgtk2.0-dev[/font]
```

[EDIT]

Forgot "install" in the above command.

---

### Post by lnostdal on 2007-02-24
[http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) contains some writings showing you how to get started with GTK+/Glade (ubuntu-programming3.pdf) and general Ubuntu development

---

### Post by Skyler on 2007-02-24
The program I'm trying to compile says this when I run ./configure:

```

checking for GTK+ - version >= 2.2.1... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
checking for gtk-config... no
checking for gtk12-config... no
checking for gtk13-config... no
checking for GTK - version >= 1.2.5... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.

```

---

### Post by lnostdal on 2007-02-24
uhm, what are you compiling?

---

### Post by Skyler on 2007-02-24
It's a turn based strategy game called FreeCiv.

---

### Post by yabbadabbadont on 2007-02-24
FreeCiv is in the repositories.  (at least it is in dapper)  If you are trying to build a newer version than that available in the repos, you can probably get most, if not all, of the build dependencies by running, "sudo apt-get build-dep freeciv".

---

### Post by lnostdal on 2007-02-24
why do you want to compile that? it's already available in the repos for you to install automatically

use synaptic or aptitude to install software under Ubuntu .. here's how to do it with aptitude from the terminal:

```
sudo aptitude install freeciv
```

(see [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/add-applications.html) and [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto) )

---

### Post by Skyler on 2007-02-25
Oh... okay... thank you.

---

