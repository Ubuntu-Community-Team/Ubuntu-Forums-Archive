---
title: "GCC/G++ corrupt :O"
date: 2007-06-09
forum: Programming Talk
---

### Post by Sockerdrickan on 2007-06-09
robin@PC:~/Desktop$ g++ lol.cpp -o lol
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/cstdlib:135: fel: "::system" har inte deklarerats



 // Have not been declared

---

### Post by Sockerdrickan on 2007-06-10
bump

---

### Post by Sockerdrickan on 2007-06-10
WHY do I have to bump this?

---

### Post by christhemonkey on 2007-06-10
Could we have a look at your source file please?
It might help?

---

### Post by Toxe on 2007-06-10
> **Tux0r said:**
> WHY do I have to bump this?
Because we do not know what you want to tell us?

Here's a tip. If you want to ask a question: _ask a question!_. After all you want something from us (i suppose) so show a little effort yourself.

---

### Post by engla on 2007-06-10
I found [this ubuntu bug]("https://bugs.launchpad.net/ubuntu/+source/gcc-4.1/+bug/77559") just by searching. I don't know if it is related, but the error is exactly the same.

---

### Post by Sockerdrickan on 2007-06-11
I can't compile anything lol something is wrong

---

### Post by Sockerdrickan on 2007-06-11
YES it works!!




"After uninstalling libpthread20 and libpthread-dev problem was fixed.
 Matthias Klose said on 2007-05-18: (permalink)"

"closing this report; libpthread-dev is gone long ago, and not in the archives anymore." <-- Does he mean Gutsy?

---

