---
title: "Whats the most C++'esque way of emptying a file?"
date: 2009-05-31
forum: Programming Talk
---

### Post by Bodsda on 2009-05-31
Hi, I need to either remove all data from a file, or just delete the file. Whats the best way of going about this? 

I'd prefer not to use rm -f via a system call

Regards,

Bodsda

---

### Post by Linteg on 2009-05-31
[http://www.cplusplus.com/reference/clibrary/cstdio/remove/](http://www.cplusplus.com/reference/clibrary/cstdio/remove/)

---

### Post by Bodsda on 2009-05-31
oh, brilliant, just what I needed, thanks dude :)

Thanks,

Bodsda

---

### Post by soltanis on 2009-05-31
Truncating the file to 0 also works if you plan on writing something else to it.

Opening the file in "write" mode automatically does this.

---

