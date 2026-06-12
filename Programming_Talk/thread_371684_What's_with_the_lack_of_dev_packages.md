---
title: "What's with the lack of dev packages?"
date: 2007-02-27
forum: Programming Talk
---

### Post by ralphmerridew on 2007-02-27
I keep running into times where a package foo is available under Ubuntu, but the corresponding foo-dev package is not.  (I hit that problem again with SDL just today.)

Why doesn't Ubuntu carry all the dev packages?  (Also, what's the reason for the separate packages for foo and foo-dev?)

---

### Post by runningwithscissors on 2007-02-27
> **ralphmerridew said:**
> (Also, what's the reason for the separate packages for foo and foo-dev?)
Program binaries do not need the headers dumped onto your system.
In source based distributions that is not the case. So any package installation will also install the the headers and other development dependencies, in case the program needs to be updated/recompiled.
Hence, me using a source-based distribution ;)

---

### Post by ralphmerridew on 2007-04-09
Something weird:

$ dpkg -l "*vte*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libvte-common  0.12.2-0ubuntu Terminal emulator widget for GTK+ 2.0 - comm
un  libvte2        <none>         (no description available)
ii  libvte4        0.12.2-0ubuntu Terminal emulator widget for GTK+ 2.0 - runt
ii  python-vte     0.12.2-0ubuntu Python bindings for the VTE widget set

$ sudo apt-get install libvte4-dev
(does so)

$ dpkg -l "*vte*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libvte-common  0.12.2-0ubuntu Terminal emulator widget for GTK+ 2.0 - comm
ii  libvte-dev     0.12.2-0ubuntu Terminal emulator widget for GTK+ 2.0 - deve
un  libvte2        <none>         (no description available)
ii  libvte4        0.12.2-0ubuntu Terminal emulator widget for GTK+ 2.0 - runt
ii  python-vte     0.12.2-0ubuntu Python bindings for the VTE widget set


Why does the libvte-dev package only show up after I install it?

---

### Post by kaamos on 2007-04-10
Because dpkg -l lists installed packages.You can use
```

apt-cache search vte|grep "\-dev"

```
to search the repositories.

---

