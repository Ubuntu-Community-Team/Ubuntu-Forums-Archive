---
title: "Can't compile scmbug"
date: 2006-02-02
forum: Packaging and Compiling Programs
---

### Post by shaji on 2006-02-02
Hi,

I wanted to try scmbug on Ubuntu 5.10. Since an Ubuntu package doesn't seem to exist, I downloaded SCMBUG_RELEASE_0-8-17.tar.gz from [http://freshmeat.net/projects/scmbug/](http://freshmeat.net/projects/scmbug/) and tried to build it, but the configuration script listed some dependencies for most of which I could not find Ubuntu packages. The output of ./configure is given below - has anyone tried it and made it work ?

root@ubuntu:/for_installation/scmbug/SCMBUG_RELEASE_0-8-17# ./configure
Before processing arguments....
prefix... NONE
exec_prefix... NONE
bindir... ${exec_prefix}/bin
sbindir... ${exec_prefix}/sbin
mandir... ${prefix}/man

datadir... ${prefix}/share
localstatedir... ${prefix}/var
sysconfdir... ${prefix}/etc
After processing arguments....
prefix... /usr
exec_prefix... /usr
bindir... /usr/bin
sbindir... /usr/sbin
mandir... /usr/man
datadir... /usr/share
localstatedir... /var
sysconfdir... /etc
checking for gawk... no
checking for mawk... mawk
checking whether ln -s works... yes
checking for perl... yes
checking for sed... yes
checking for awk... yes
checking for xargs... yes
checking for grep... yes
checking for cvs2cl... no
checking for convert... no
 *** This tool is provided by ImageMagick
checking for fig2dev... no
 *** This tool is provided by transfig
checking for latex2html... no
checking for docbook2dvi... no
 *** This tool is provided by docbook-utils
checking for docbook2pdf... no
 *** This tool is provided by docbook-utils
checking for docbook2html... no
 *** This tool is provided by docbook-utils
checking for docbook2man... no
 *** This tool is provided by docbook-utils
checking for linkchecker... no
The following programs are necessary for building this project but are missing: cvs2cl convert fig2dev latex2html docbook2dvi docbook2pdf docbook2html docbook2man linkchecker
Scmbug cannot be build.

Regards
Shaji

---

