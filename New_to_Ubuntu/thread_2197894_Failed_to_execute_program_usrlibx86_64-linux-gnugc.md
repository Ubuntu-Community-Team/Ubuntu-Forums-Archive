---
title: "Failed to execute program /usr/lib/x86_64-linux-gnu/gconf/gconfd-2: Success"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by cheeseng2 on 2014-01-05
Hi all, 

I have the following problem after updating the kernel through update manager last week: 

Failed to execute program /usr/lib/x86_64-linux-gnu/gconf/gconfd-2: Success

This happens when I open firefox (though firefox still working after I closed the error dialog), and I am not able to launch my gnome-terminal also, which I guess is due to the same reason.

Is there anything I can do to fix the problem.

Thanks in advanced for any help or pointers.

Thanks!

---

### Post by sandyd on 2014-01-06
**Moved to ABT**

---

### Post by cheeseng2 on 2014-01-07
Problem fixed by copying gconfd-2 executable back into the /usr/lib/x86_64-linux-gnu/gconf/, it went missing somehow&#65279;

---

