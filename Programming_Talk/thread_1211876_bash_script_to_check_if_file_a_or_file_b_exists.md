---
title: "bash script to check if file a or file b exists"
date: 2009-07-13
forum: Programming Talk
---

### Post by staticanime on 2009-07-13
Hi all, I want to create a simple script to check if file a OR file b exists.
I know that the following will check for file a, but how would I add file b to the mix?
```

if [ -f filea];then
   [CODE TO RUN]
fi

```
could I do something like:
```

if [ -f filea OR -f fileb];then
   [CODE TO RUN]
fi

```

---

### Post by sisco311 on 2009-07-13
```
if [ -f filea -o -f fileb ]; then 
  ...
fi
```

for more info read the man page:
```
man [
man test
```

---

### Post by staticanime on 2009-07-13
> **sisco311 said:**
> ```
if [ -f filea -o -f fileb ]; then 
  ...
fi
```

for more info read the man page:
```
man [
man test
```

Cool, thanks, just needed -o sweet :D

---

