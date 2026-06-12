---
title: "Problem with installing true type fonts"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by Master Tonberry on 2013-02-11
I tried to install the microsoft true type font package and at the end of the process a message displayed telling me to press 'ok' to the terms of agreements. I didn't know I had to press TAB in order to select the ok button so I closed the terminal and now have this error: "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' " to correct the problem. 

what do i do?

---

### Post by ibjsb4 on 2013-02-11
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo dpkg --configure -a
```

---

