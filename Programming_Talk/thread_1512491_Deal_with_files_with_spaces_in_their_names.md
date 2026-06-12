---
title: "Deal with files with spaces in their names"
date: 2010-06-18
forum: Programming Talk
---

### Post by dragos2 on 2010-06-18
I am using this to avoid problems with files with spaces in their name:
```

find /samba 2>/dev/null -exec ls -l {} \; 

```

But the problem is that its slow, how can I make it work with xargs and still work with files with spaces in their names ?

---

### Post by Compyx on 2010-06-18
You can tell find and xargs to use '\0' to delimit filenames, rather than whitespace. Find needs the option '-print0' and xargs needs the option '--null'.

Example:
```

find /usr/src -name *.c **-print0** | xargs **--null** grep 'printf'

```

---

### Post by dragos2 on 2010-06-18
> **Compyx said:**
> You can tell find and xargs to use '\0' to delimit filenames, rather than whitespace. Find needs the option '-print0' and xargs needs the option '--null'.

Example:
```

find /usr/src -name *.c **-print0** | xargs **--null** grep 'printf'

```

Thank you.

---

