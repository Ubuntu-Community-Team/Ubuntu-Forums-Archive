---
title: "Can we use find -mtime in hourse and minutes"
date: 2012-06-14
forum: Programming Talk
---

### Post by user585858 on 2012-06-14
Hi Guys,

I was reading this article [http://javarevisited.blogspot.sg/2011/03/10-find-command-in-unix-examples-basic.html](http://javarevisited.blogspot.sg/2011/03/10-find-command-in-unix-examples-basic.html)
which says that we can use find -mtime to find out 3 days old file or 2 days old file.

I am just wondering can I do same to find out 3 hours old file or 30 minutes old files? that article doesn't explain much about it. please let me know if it is at all possible ?

---

### Post by MG&amp;TL on 2012-06-14
Use -mmin flag to set number of minutes.

```
find . -mmin 3    #exactly 3 minutes old
find . -mmin +3    #more than 3 minutes old
find . -mmin -3    #less than 3 minutes old.
find . -mmin -360    #less than 6 hours old
```

---

### Post by user585858 on 2012-06-14
Thanks MG&TL, This is was I am exactly looking for. Perfect

---

