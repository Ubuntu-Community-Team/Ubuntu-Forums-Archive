---
title: "Using alien to install rpm package"
date: 2012-11-24
forum: New to Ubuntu
---

### Post by umeshkumar on 2012-11-24
I have a rpm package which consists of script files,properties files and jars.

On ubuntu 12.04 i am using alien to install my rpm package using:

sudo alien -icvk myrpmpackage.rpm

This installs the rpm package with script files and jars, but skips the properties files. I added option -c which includes only scripts.
How do i get properties file be included in installed package ?

---

