---
title: "Anonymous behaviour of cd(if i am right)"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by Sunil Hari on 2012-01-11
Helo guys

Am a new linux user.when i was using ubuntu it showd something wierd to me.when i gave the command cd // it took to // as if there is another directory / inside /.but it has the same contents as that of /.so what is actually this //

---

### Post by CharlesA on 2012-01-11
Looks like it's just referencing the root directory.

Try running this:

```
ls -ld /////
```

---

### Post by bodhi.zazen on 2012-01-11
> Multiple successive slashes are considered to be the same as one slash. 

[http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap03.html#tag_03_266](http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap03.html#tag_03_266)

---

### Post by Sunil Hari on 2012-01-12
:)thank u

---

### Post by CharlesA on 2012-01-12
> **bodhi.zazen said:**
> [http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap03.html#tag_03_266](http://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap03.html#tag_03_266)
Well that explains it.

Thanks!

---

