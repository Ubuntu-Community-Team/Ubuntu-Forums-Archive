---
title: "Gambas &quot;alien command has failed&quot; error"
date: 2005-09-16
forum: Programming Talk
---

### Post by mhancoc7 on 2005-09-16
Hi all,

I just found Gambas, and I am really excited to try it out. I have finished a simple "Hello World" app. Now I am trying to "Make an installation package".

I follow the steps in the "Make an installation package" wizard. When I click "Make Package" I get the following error:

Creating package for Debian.
Initializing ~/RPM directory.
Creating source package.
Creating .spec file.
Creating RPM packages.


The package build has failed.

alien command has failed

Can anyone help me get this working. I searched this forum and read a million gambas mailing list archives. I can't find an answer to this one.

I have installed the latest version of Gambas using Synaptic.

Thanks in advance, Jereme

---

### Post by vanwarantion on 2007-03-09
I have the same problem.
actualy it creates a funny named bzip archive in the ~/RPM/SOURCES directory but then gives the error message and kills itself.

i have installed gambas using automatix.

---

### Post by lnostdal on 2007-03-09
well, it does say the `alien' command fails .. is `alien' installed?

```
sudo aptitude install alien
```

edit:
key here is to figure out what "alien command has failed" means or implies .. the software should either log more info somewhere or have an option that displays more verbose information about what's going on

---

