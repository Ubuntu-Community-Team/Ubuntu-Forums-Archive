---
title: "problem in installing any package"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by ebikh on 2012-07-15
This was started from when I wanted to install google-earth and it did not, I found in some forum that I can do it by installing lsb-core whereas it was mistake.After installing lsb-core,any attempt to install any packages follows by this problem

 dpkg: error: file triggers record mentions illegal package name `libgdk-pixbuf2.0-0' (for interest in file `/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders'): ambiguous package name 'libgdk-pixbuf2.0-0' with more than one installed instance
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: file triggers record mentions illegal package name `libgdk-pixbuf2.0-0' (for interest in file `/usr/lib/gdk-pixbuf-2.0/2.10.0/loaders'): ambiguous package name 'libgdk-pixbuf2.0-0' with more than one installed instance

I am using ubuntu 12.04 anyway

---

### Post by raja.genupula on 2012-07-16
open your synaptic package manager and look for this  pkg  **libgdk-pixbuf2.0-0** install status with combinations if not found directly . Install/reinstall it if you find it anyway .

---

### Post by ebikh on 2012-07-16
Thanks for your help
But I see the error message even when I want to remove or re install libgdk-pixbuf2.0-0 package,I think something must be change in lsb-core package installed on my computer.

---

### Post by raja.genupula on 2012-07-17
you getting the same error ?

---

### Post by ebikh on 2012-07-17
Yes it is the same error

---

### Post by bobsan on 2012-07-17
Maybe this will help?

[http://ubuntuforums.org/showthread.php?t=2006840](http://ubuntuforums.org/showthread.php?t=2006840)

---

### Post by bobsan on 2012-07-17
Maybe this will help? [http://ubuntuforums.org/showthread.php?t=2006840](http://ubuntuforums.org/showthread.php?t=2006840)

---

