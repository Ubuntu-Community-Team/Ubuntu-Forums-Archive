---
title: "[SOLVED] apt-get purge or apt-get remove --purge?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-08-01
Is there any difference?

---

### Post by tommynz1975 on 2008-08-01
To remove just a package
use    apt-get remove NameOfPackage 

To remove a package and its configeration file.
apt-get --purge remove NameOfPackage

remove  is identical to install except that packages are removed
instead of installed. If a plus sign is appended to the  package name (with no intervening space), the identified package will be installed.

---

### Post by Butthead on 2008-08-01
The "man" listing for apt-get just has purge (no leading "--" either) just by itself.

---

### Post by OzzyFrank on 2010-06-04
From what I have seen, **[COLOR="DarkRed"]apt-get purge[/COLOR]** is the newer format, since there is now a ***[COLOR="DarkRed"]purge[/COLOR]*** command for **apt**, whereas **[COLOR="DarkRed"]apt-get remove --purge[/COLOR]** is the old format, which is still fine, and probably always will be for backwards compatibility.

---

