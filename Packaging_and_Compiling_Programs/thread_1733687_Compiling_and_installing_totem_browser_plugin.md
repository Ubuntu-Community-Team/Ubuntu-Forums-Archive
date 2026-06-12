---
title: "Compiling and installing totem browser plugin"
date: 2011-04-19
forum: Packaging and Compiling Programs
---

### Post by marlon_smith on 2011-04-19
Hi everyone,

I'm not sure if this is the best place to ask this, but I am having trouble installing the totem browser plugin from source.  I would like to make some modifications to the plugin.

I downloaded the totem source code, did a ./configure --enable-browser-plugins, and then did a make and a sudo make install.

Totem itself is properly installed, and I can run it, but the browser plugin does not seem to even get compiled.  The configure script does generate a makefile in the ./browser-plugin directory, but I can't see any indication that a .so file is created (and nothing shows up in /usr/lib/mozilla/plugins afterwards).

Does anyone have any knowledge in this area?  If not, is there another forum that I could post in?  I can't seem to find a forum for totem specifically.

Thanks!

Marlon

---

### Post by mc4man on 2011-04-19
I'd probably be inclined to build as a debian package set instead, but anyway - 
the files would by default be installed to /usr/local/*, did you look there?
Also did you run sudo ldconfig after the install?

Did you read through your ./configure results before the make to make sure the mozilla plugin was going to be built

---

