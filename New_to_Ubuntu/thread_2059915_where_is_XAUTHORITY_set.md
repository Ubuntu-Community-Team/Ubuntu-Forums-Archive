---
title: "where is XAUTHORITY set?"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by Script Wrecked on 2012-09-19
Where is (the value for) (environment variable) XAUTHORITY set?

I sudo from the userid "foo" to "bar" (via "sudo -u bar -i"; foo has administrator access; bar has normal access) and find XAUTHORITY set to foo's ".Xauthority" file, to which bar does not have access.

This causes the application I'm trying to run (nwn) to segmentation fault.

Regards,

Script Wrecked.

---

### Post by Script Wrecked on 2012-09-29
XAUTHORITY is set in /usr/bin/startx, but startx isn't normally used to start X-windows. Digging...

---

### Post by Bashing-om on 2012-09-29
see if this points you in any pertinent direction:
[http://www.ibm.com/developerworks/linux/library/l-basics/section6.html](http://www.ibm.com/developerworks/linux/library/l-basics/section6.html)

[INDENT]hth <==BDQ

[/INDENT]

---

### Post by Script Wrecked on 2012-09-30
Thanks for the link. Digging...

---

