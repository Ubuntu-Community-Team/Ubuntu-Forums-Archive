---
title: "Compiling XML-LibXML-Common problem..."
date: 2006-07-22
forum: Packaging and Compiling Programs
---

### Post by KooT on 2006-07-22
Im trying to instal perl module XML-LibXML-Common, but this is what i got:

root@marhefka:/home/koot/perl/XML-LibXML-Common-0.13# perl Makefile.PL
enable native perl UTF8
running xml2-config... ok
looking for -lxml2... no
looking for -llibxml2... no
libxml2 not found
Try setting LIBS and INC values on the command line
Or get libxml2 from
  [http://www.libxml.org/](http://www.libxml.org/)
If you install via RPMs, make sure you also install the -devel
RPMs, as this is where the headers (.h files) are.

apt-get says that the newst version of libxml, libxml2, libxml-dev, libxml2-dev are installed...

---

### Post by uzair on 2006-11-24
If you do 'locate libxml2.so' you'll find that the closest you can find is '/usr/lib/libxml2.so.2', which is the right file but isn't being referenced properly.

Just create a symlink with the appropriate name: 'sudo ln -s /usr/lib/libxml2.so.2 /usr/lib/libxml2.so'

Note that if you don't have sudo, you can create the symlink elsewhere and supply a LIB path manually.

---

