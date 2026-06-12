---
title: "Get time from Bash"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by DBrocks on 2008-07-30
Hey guys. How can i get the system time in BASH, then send that time into a text file?

---

### Post by pauper on 2008-07-30
```
date
date >> $HOME/Desktop/new_file
```

---

### Post by DBrocks on 2008-07-30
Thanks. Figured it would be an easy fix. :lolflag::lolflag:

---

### Post by tamoneya on 2008-07-30
> **DBrocks said:**
> Hey guys. How can i get the system time in BASH, then send that time into a text file?

```
date +%H:%M:%S > myfile.txt

```

EDIT: late again

---

