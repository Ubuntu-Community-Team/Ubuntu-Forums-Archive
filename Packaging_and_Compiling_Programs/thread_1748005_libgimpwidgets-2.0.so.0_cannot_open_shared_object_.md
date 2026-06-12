---
title: "libgimpwidgets-2.0.so.0: cannot open shared object file"
date: 2011-05-03
forum: Packaging and Compiling Programs
---

### Post by adit on 2011-05-03
I downloaded the source code gimp-2.6.11.tar.bz2.
```
./configure
make
sudo make install
```
All of the above commands completed successfully. When I run gimp from command line I get the following error:```

gimp: error while loading shared libraries: libgimpwidgets-2.0.so.0: cannot open shared object file: No such file or directory
```

---

### Post by hakermania on 2011-08-27
same here

---

### Post by MadCow108 on 2011-08-27
installing stuff from source usually lands in /usr/local
you may have to tell dynamic linker to find the libraries placed there.
temporary with LD_LIBRARY_PATH:
```
LD_LIBRARY_PATH=/usr/local/lib  your-application
```
or permanent with ld.so.conf
```
echo "/usr/local/lib" | sudo tee /etc/ld.so.conf.d/usr_local.conf
```

---

### Post by hakermania on 2011-08-29
thanks mad cow, well I solved it, it simply needed:
```

sudo apt-get purge gimp-help-en gimp-help-common gimp-data libgimp2.0
sudo apt-get install gimp-help-en gimp-help-common gimp-data libgimp2.0

```
and all files went were they had to..

Thanks, anyway.

---

