---
title: "dh_make doesn't recognise the .orig.tar.gz file..."
date: 2010-07-06
forum: Packaging and Compiling Programs
---

### Post by J V on 2010-07-06
```
j@jubuntu:~/Projects/apgui/apguideb/apgui-0.3$ ls
apgui-0.3  apgui-0.3.orig.tar.gz
j@jubuntu:~/Projects/apgui/apguideb/apgui-0.3$ dh_make -c gpl3

Type of package: single binary, indep binary, multiple binary, library, kernel module, kernel patch or cdbs?
 [s/i/m/l/k/n/b] s

Maintainer name : Jonathan Vollebregt
Email-Address   : ***
Date            : Tue, 06 Jul 2010 18:54:44 +0200
Package Name    : apgui
Version         : 0.3
License         : gpl3
Using dpatch    : no
Using quilt     : no
Type of Package : Single
Hit <enter> to confirm: 
Could not find apgui-0.3.orig.tar.gz
Either specify an alternate file to use with -f,
or add --createorig to create one.

```It was apgui_0.3.orig.tar.gz before but the error message said I needed a dash, now it's just not seeing it at all...

---

### Post by SevenMachines on 2010-07-06
the tgz should be in the directory above your source directory, ie, if your source directory is apgui-0.3 (inside this is where you run dh_make) then apgui-0.3.orig.tar.gz should be in the ../ directory (apguideb in your case). in addition, if you run
$dh_make -createorig
it will also create this archive for you

---

### Post by J V on 2010-07-06
Oh screw this, call me when someone makes a guide for deb packaging in english...

---

