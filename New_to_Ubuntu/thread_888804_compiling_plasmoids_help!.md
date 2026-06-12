---
title: "compiling plasmoids help!"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by benji.ijneb on 2008-08-13
whenever i try to compile a plasmoid for KDE 4 following instructions such as these:

> # tar -xvzf plasma-weather-0.2.tar.gz
# cd weather
# mkdir build
# cd build
# cmake -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..
# make
# make install

it all works perfectly until i come to the 'make' command, at which point i get 'no targets specified and no makefile found'. (i have build essential installed).

i'm not sure if this is just a problem with plasmoids, or with any apps - i rarely compile stuff...

all help needed and appreceated! Thanks!

---

### Post by oliviacond on 2008-08-18
make sure u have everything needed to compile.
```

sudo apt-get build-dep extragear-plasma

```

---

