---
title: "Quick Alias Question"
date: 2007-02-08
forum: Programming Talk
---

### Post by EADG on 2007-02-08
Hello all.... first post. Lovin' the forum.

I want to have this alias run in the background, but not sure how... I keep getting errors because I can't figure out how\where to put the "&"

alias rmw="wipe -rqsf"

The normal command works fine when used liked this;
wipe -rqsf myfile.doc &

Any suggestions?

---

### Post by engineer on 2007-02-09
did you try?

```

rmw myfile.doc &

```

if you don't want to type the &, you'll need a short shell script.
as far as i know this can't be done with aliases alone

---

### Post by EADG on 2007-02-09
Thanks engineer. It's working now...

---

