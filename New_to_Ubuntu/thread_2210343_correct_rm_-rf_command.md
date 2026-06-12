---
title: "correct rm -rf command"
date: 2014-03-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-03-10
in my folder
/home/ray/desktop backgrounds
i have about 100 files that have the prefix .thumb  eg.-.thumb_20712.jpg. what would be the correct command to delete all of them at once. tks

---

### Post by Lars Noodén on 2014-03-10
I would have tried [find](http://manpages.ubuntu.com/manpages/saucy/en/man1/find.1.html)

```

find . -type f -name '.thumb.*' -delete

```

---

### Post by rburkartjo on 2014-03-10
lars tks had to add sudo to the beginning and then delete the last .

sudo find . -type f -name '.thumb*' -delete

that did the trick

---

