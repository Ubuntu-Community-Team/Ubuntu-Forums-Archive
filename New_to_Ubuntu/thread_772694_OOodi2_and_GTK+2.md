---
title: "OOodi2 and GTK+2"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Captaingracekidd on 2008-04-28
Im trying to install OOodi for Openoffice so i can get spellcheck in swedish, it is dependent on GTK2 i assumed this came included in gutsy but maybee i was wrong. This is what happens when i ./configure

```
~/Desktop/OOodi2-0.68$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for strerror in -lcposix... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for         glib-2.0                   gthread-2.0                    gtk+-2.0
        libglade-2.0... Package glib-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `glib-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'glib-2.0' found Package gthread-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gthread-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gthread-2.0' found Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found Package libglade-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `libglade-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'libglade-2.0' found
configure: error: Library requirements (        glib-2.0                       gthread-2.0              gtk+-2.0
        libglade-2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```

I tried apt-get install the packages but i cant find them in the repositories, Can anyone help me on how to fix this? Do I need to install GTK2 from scratch, and if so how do i do this?

Thanks

---

### Post by quirks on 2008-04-28
```
apt-get install libglib2.0-dev
```
This should fix your problem.

If it tells you something like it can't find the package, open System -> Administration -> Synaptic Package Manager. Go to Settings -> Repositories and check all listed software sources.

---

