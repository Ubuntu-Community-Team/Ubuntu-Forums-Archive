---
title: "Help with packaging the app"
date: 2012-09-24
forum: Programming Talk
---

### Post by bird1500 on 2012-09-24
Hi,
Can anyone please try to package (create a deb) this app?

To compile the app one needs: libgtkmm-3.0-dev, libgstreamermm-0.10-dev, libappindicator3-dev
To compile go to $source/bin do "cmake ..", then "make" and the binary "uap" will appear in this dir. Double click it and an audio player launches.

However, I can't [package]("http://developer.ubuntu.com/packaging/html/packaging-new-software.html") it.
bzr builddep yields a broken .deb which doesn't contain neither the source files nor the compiled binary file.

---

### Post by conradin on 2012-10-15
This page:
[http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/#AEN42](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/#AEN42)

is really helpful.
the program lintain can help you figure out where a deb package you may have previously built fails.

---

