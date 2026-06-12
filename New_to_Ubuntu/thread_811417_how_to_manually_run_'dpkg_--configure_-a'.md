---
title: "how to manually run 'dpkg --configure -a'"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by milan_cortana on 2008-05-29
hi.
j was updating my ubuntu when j accidentally turn off pc.
now when j try to continue installing updates j get this error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

please help me.
j dont know how to do this.

thanks

---

### Post by kaboodle_fish on 2008-05-29
You just need to copy and paste the command into a terminal

---

### Post by forestpixie on 2008-05-29
Open aterminal - it's in accessories and then paste this in to the terminal and enter

```
sudo dpkg --configure -a
```

It will ask for your password - enter it, but you will not see it appear - it is ther though and then enter again

---

### Post by iaculallad on 2008-05-29
Open up your terminal: Applications->Accessories->Terminal and issue the command:

Code:
```

sudo dpkg --configure -a
```

---

