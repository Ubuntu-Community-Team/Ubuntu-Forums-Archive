---
title: "Insert line breaks into a very long line"
date: 2008-07-09
forum: Programming Talk
---

### Post by LotsOfPhil on 2008-07-09
Hello,

I have a text file that consists of one very long line (the file is 43 MB). It is a bunch of fixed-length records so I would like to put line breaks in every 494 characters.

I feel like this should be pretty easy to do with awk/sed, but can't figure it out. Can anyone give me some guidance?

Thanks.

---

### Post by Trumpen on 2008-07-09
This should work 

```
sed 's/.\{494\}/&\n/g' yourfile
```

---

### Post by LotsOfPhil on 2008-07-09
Excellent. Thank you.

---

