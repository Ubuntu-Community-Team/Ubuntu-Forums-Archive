---
title: "bash random string"
date: 2011-06-04
forum: Programming Talk
---

### Post by tapi0n on 2011-06-04
I was wondering if it's possible to create an 8 char random string in bash. Non-capital and capital letters mixed. Found some info but they're all hashes of an existing string. I just want to generate a new string from [A-Za-z].

Cheers

---

### Post by kaibob on 2011-06-04
I came across the following command-line a while back. It produces eight random upper- and lower-case letters. 

```
tr -dc "[:alpha:]" < /dev/urandom | head -c 8
```

---

