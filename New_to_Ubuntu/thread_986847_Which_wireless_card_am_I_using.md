---
title: "Which wireless card am I using?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Skene on 2008-11-19
Well I've switched over to Ubuntu and now I can't seem to remember what I'm using. I used the windows method for so long though don't know the equivalent here.

I've tried "top" but can't seem to get what information I need.

---

### Post by fooman on 2008-11-19
try:

```
lspci
```

or:

```
iwconfig
```

---

### Post by nhasian on 2008-11-19
to see what network adaptors are detected type:

```
lshw -C network
```

---

