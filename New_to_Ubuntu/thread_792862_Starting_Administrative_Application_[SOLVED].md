---
title: "Starting Administrative Application [SOLVED]"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Alex1200GS on 2008-05-13
Hi all,

after upgrading my laptop to Hardy, all applications that required an administrative password failed to start. A button would appear in the panel, reading "Starting Administrative Application", but a few seconds later it would disappear without prompting me for a password.

I discovered that this can be fixed directly in the /etc/hosts file, where there should be two lines reading:

127.0.0.1 localhost
127.0.1.1 vaio

where "vaio" is the name of my computer. That solved the problem for me. Kudos to the forum of the Greek Linux Format magazine.

Alex

---

### Post by johninmihno on 2008-05-16
Hi Alex, my hosts file has the lines you mention but unfortunately I am suffering the same problem. Any ideas? Cheers John

---

### Post by forestpixie on 2008-05-16
this method works

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

---

