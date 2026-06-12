---
title: "error on hydra install"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by jba6511 on 2008-08-03
I get the following errors when attempting to compile hydra from source. ./configure and make complete without any problems, but sudo checkinstall and sudo make install fail. Any ideas?


[PHP][blake@deviant:~/hydra-5.4-src$ sudo make install
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
cp: target `/usr/local/bin' is not a directory
make: [install] Error 1 (ignored)
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
cd: 1: can't cd to /usr/local/bin
make: [install] Error 2 (ignored)
[/PHP]


[PHP]Installing with make install...

========================= Installation results ===========================
test -e hydra.exe && touch Makefile || strip hydra pw-inspector
test -e hydra.exe && strip hydra.exe pw-inspector.exe || touch hydra
test -e xhydra && strip xhydra || touch Makefile
test -e hydra.exe && touch Makefile || cp hydra pw-inspector /usr/local/bin && cd /usr/local/bin && chmod 755 hydra pw-inspector
cp: target `/usr/local/bin' is not a directory
make: [install] Error 1 (ignored)
test -e hydra.exe && cp hydra.exe pw-inspector.exe /usr/local/bin && cd /usr/local/bin && chmod 755 hydra.exe pw-inspector.exe || touch Makefile
test -e xhydra && cp xhydra /usr/local/bin && cd /usr/local/bin && chmod 755 xhydra
cd: 1: can't cd to /usr/local/bin
make: [install] Error 2 (ignored)

======================== Installation successful ==========================

Copying documentation directory...
./
./README
./TODO
./INSTALL
./README.arm
./CHANGES
./README.palm
grep: /var/tmp/LaaNaIdqDORHZRHRGdHBI/newfile: No such file or directory

Copying files to the temporary directory...OK

Stripping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package[/PHP]

---

### Post by Diabolis on 2008-08-03
According to this, everything went fine. Can you run hydra?

It only didn't made the .deb, but I don't think that is a problem. Unless what you really what to do is package the application for distribution.

*yes! my cup of coffee is back*

---

### Post by jba6511 on 2008-08-03
thanks. I did not even realize that hydra installed.

---

