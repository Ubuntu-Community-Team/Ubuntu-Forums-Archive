---
title: "c/c++ programming with eclipse"
date: 2007-05-02
forum: Programming Talk
---

### Post by jmwalloh on 2007-05-02
kudos to the development team for the new feisty fawn 7.04.there's this eclipse stuff that i heard about and wanted to try it on ubuntu but don't how to go about it .can someone direct in the right direction

---

### Post by jespdj on 2007-05-02
The normal way to install software on Ubuntu Linux is to use a package manager tool to look up if there is a Ubuntu package for the software you want to use. Choose the menu System / Administration / Synaptic Package Manager and search for Eclipse packages.

For the C/C++ development tools, you'll need the package named **eclipse-cdt**.

---

### Post by bluedalmatian on 2007-05-06
On a related note, anyone know why Eclipse is failing to link against the Mysql client libraries.

In project properties theres a C++ linker section which allows you to specify libs (-l option on gcc) or specify library search paths (-L option on gcc).

It seems to completely ignore anything in the first box (-l)

I'vr got libmysqlclient.a in /usr/lib which I want to link with.

If I add /usr/lib to the -L option I can see it in the console output at build time being added to the g++ command but it dosnt link with mysqlclieny

If I add /usr/lib/libraryname  to the top box (-l)  no -l options are ever added to the g++ command when in scrolls past in the console.

Thanks

AW

---

