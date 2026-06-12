---
title: "[SOLVED] Error Msg with Synaptic Package Manager"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by eluis.c on 2008-07-24
When i try to open the SPM it says: "An error ocurred"
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And cant install another programs because says: "Only one software management tool is allowed to run at the same time."

Any help?!

---

### Post by BDNiner on 2008-07-24
did you run
```

sudo dpkg -configure -a

```

from a terminal?

---

### Post by Elfy on 2008-07-24
First you can only have synaptic, add/remove or be doing an apt-get or aptitude in the terminal one at a time if you get the "Only one software management tool..." error you either have more than one open or a previous one has not closed properly.

```
sudo dpkg --configure -a
``` for the first error you have

---

### Post by eluis.c on 2008-07-24
Yes and already typed dpkg -help but dont know what to do next

---

### Post by Elfy on 2008-07-24
Run the command in a terminal.

---

### Post by eluis.c on 2008-07-24
Done... just had a broken filter (sun-java-...) and the problem is fixed.
Thanks for the help forrest

---

### Post by Elfy on 2008-07-24
Welcome - cna you mark thread solved

---

