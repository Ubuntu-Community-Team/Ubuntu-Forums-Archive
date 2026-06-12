---
title: "ubuntu voodoo fate"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by harryliddic on 2012-02-23
I've have climbed the ubuntu ladder over the years, but when I could log out of 11.04 and 11.10 I turned back to the 10.04 paradigm for my linux uses. Now that I am In 10.04 that old voodoo struck again. My top panel strunk to half its size. Sending 'Applications' 'Places' and 'Adminstrative'
into the cybersphere. How do I replace them?
Thanks for your gracious help in advance.

---

### Post by wolfen69 on 2012-02-23
Do Ctrl-Alt-T to open a terminal, and do:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
then log out or reboot.

---

