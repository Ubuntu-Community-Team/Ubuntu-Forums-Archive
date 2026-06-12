---
title: "building across linux distros (wxwidgets)"
date: 2011-03-10
forum: Programming Talk
---

### Post by mikejonesey on 2011-03-10
Think this is a stupid question but maybee someone has done the same thing;

I build a cpp app in wxwidgets on ubuntu, I copy executable to a centos box, I run it I get;

> ./xedit: error while loading shared libraries: libgio-2.0.so.0: cannot open shared object file: No such file or directoryI copy the source and build and it runs;

----------

In reverse I build on the centos and copy to ubuntu I get;

> ./xedit: cannot execute binary file---------

how can I build my projects so they include all dependencies, is this posible?

I also have a solaris box which i really don't want to build source on, so any idea on how I build one app from ubuntu for all...

----------

many thanks

--------------

update:
found this; [http://ldn.linuxfoundation.org/lsb/check-your-app](http://ldn.linuxfoundation.org/lsb/check-your-app)
any extra info welcome...

---

### Post by azzamite on 2011-03-10
This is my experience on that:

Different distros like to build their packages in a different way, sometimes an specific library may be excluded or put in a different package (not installed by default).

Even if you don't use a library within your app the binary can be linked to it... so in other distro it might not been found.

Another issue is the naming, sometimes they name the same thing different, so it's a little hard to accomplish what you want to do using not so popular (base) packages.

Sorry I wasn't of much help.

---

### Post by mikejonesey on 2011-06-14
don't mean to drag up the old but i managed to get the app to work across 34 distros, without needing to be rebuilt...

if helps anyone else i done this using the linux foundations, app checker tool, which can tell you all sorts about nested / required libaries...

(really cool tool)

[http://ldn.linuxfoundation.org/lsb/check-your-app](http://ldn.linuxfoundation.org/lsb/check-your-app)

---

