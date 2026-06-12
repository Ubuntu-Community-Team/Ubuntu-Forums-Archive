---
title: "[SOLVED] how to join the pieces?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by imjscn on 2008-07-12
I used this code to compress and split a folder:
tar cj mybackup/ | split -b 20m -d - mybackup.tar.bz2.

Now I need to join those pieces and extrace it, how can I do it? thanks!

---

### Post by kestrel1 on 2008-07-12
How about the join command?
[http://www.computerhope.com/unix/ujoin.htm](http://www.computerhope.com/unix/ujoin.htm)

---

### Post by sdennie on 2008-07-12
You can just cat them together.  If the files are named x00, x01, x02, etc. you can use:

```

cat x* >> output.tar.bz2

```

Then, extract with:

```

tar xvf output.tar.bz2

```

---

### Post by imjscn on 2008-07-12
Thanks, got it!

---

