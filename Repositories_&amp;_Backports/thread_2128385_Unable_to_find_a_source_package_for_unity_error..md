---
title: "Unable to find a source package for unity error."
date: 2013-03-23
forum: Repositories &amp; Backports
---

### Post by RefinedCode on 2013-03-23
I am trying to get unity to compile from source, but when i run:
```
$ sudo apt-get build-dep unity
```
I get the following error:

```
E: Unable to find a source package for unity
```

There is virtually nothing on google I can find (one result when i typed the error into google).  Does anyone know how i can fix this?  I dont know which source to add to get unity dependencies.  Any help is greatly appreciated!

---

### Post by steeldriver on 2013-03-23
Do you have the appropriate deb-src lines uncommented in your /etc/apt/sources.list file? have you run 'sudo apt-get update' since adding the deb-src lines?

---

