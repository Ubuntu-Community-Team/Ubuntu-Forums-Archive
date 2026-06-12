---
title: "After installation error"
date: 2015-06-22
forum: New to Ubuntu
---

### Post by vinay9 on 2015-06-22
I installed Ubuntu 13.10 on thinkpad, prior to which 8.1 windows was installed I used bootable USB to install the new oS but now after installation error message came up error code 0x000000f and after which I get dual boot option, unable to login in any of them, while selecting Ubuntu error code is 0x0000001 path, \ubuntu\winboot\wubildr\.mbr.
Tried using bootable USB for repairing it says oS missing

---

### Post by Bashing-om on 2015-06-22
vinay9; Hello;

Wubi is no longer supported, and will not work in UEFI systems @ default.
Un-install the Wubi from within Windows and do a proper dual boot install of a current release of 'buntu.
Ubuntu 13.10 (Saucy Salamander) was the 19th release of Ubuntu. Support ended on July 17th, 2014. See:  [http://ubottu.com/y/saucy](http://ubottu.com/y/saucy)

Let us know how we can help further.

[INDENT][INDENT]good things can happen
[/INDENT][/INDENT]

---

### Post by mansonfan78 on 2015-06-23
Make sure you disable Windows fast boot before installing Ubuntu.  This may have something to do with your current problem, but even if it isn't the cause now it will cause problems later.

---

