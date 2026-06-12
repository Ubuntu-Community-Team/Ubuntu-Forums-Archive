---
title: "[SOLVED] mv /a/b/* /a/"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by bhe1123 on 2008-10-25
How do I move all of the contents of /a/b/ to /a/ ? Caveat: all of the contents in /a/b/ are folders with things in them.

edit: command I'm trying is "mv /a/b/* /a/" and getting back "mv: cannot move `/a/b/X' to `/a/X': Directory not empty

---

### Post by The Tronyx on 2008-10-25
I've been drinking so I am not sure if I am reading this right but....

mv /a/b/* ../  Does that work?

---

### Post by bhe1123 on 2008-10-25
Negative. I get the same "mv: cannot move ... to ...: Directory not empty"

To clarify: /a/b/ is a folder full of other folders with things in them. I want to move all of the folders from /a/b/ to /a/.

---

### Post by Elfy on 2008-10-25
Can I suggest that you use cp - if it goes wrong you'll still have the originals and can remove them once you know all is well

```
sudo cp -r /path/original /path/new
```

Once your sure that all is well remove the original

```
sudo rm -r /path/original
```

Edit - it needs to be recursive (-r)

---

### Post by bhe1123 on 2008-10-25
> **forestpixie said:**
> Can I suggest that you use cp - if it goes wrong you'll still have the originals and can remove them once you know all is well

```
sudo cp -r /path/original /path/new
```

Once your sure that all is well remove the original

```
sudo rm -r /path/original
```

Edit - it needs to be recursive (-r)

This worked. Thanks!

---

### Post by etitor on 2008-10-25
Enlightening question and answer, but there are simpler ways.

```
sudo apt-get install mc
```

---

