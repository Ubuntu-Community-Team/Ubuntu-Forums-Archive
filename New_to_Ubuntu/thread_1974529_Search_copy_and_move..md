---
title: "Search copy and move."
date: 2012-05-06
forum: New to Ubuntu
---

### Post by brawd on 2012-05-06
Hi All,

I wanted to collect all my .mobi files in one place instead of leaving them in their various different folders. It seemed a simple task. First search for .mobi to collect them all together.

That went fine.

When the pane came up showing all the mobi files I selected them all with a notion of copy/paste into another folder but it doesn't work like that.

Anyone got any suggestions on how to do this simple sort and store please?

regards,

---

### Post by llamabr on 2012-05-06
Untested:

```
find / -iname "*.mobi" -type f -exec /bin/mv {} /home/user/books \;
```

---

### Post by brawd on 2012-05-06
Tested.

It works.

Thank you.

---

