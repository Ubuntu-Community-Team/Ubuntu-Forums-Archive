---
title: "program parameters"
date: 2008-04-03
forum: Programming Talk
---

### Post by defmomo on 2008-04-03
Why do some programs allow the input of parameters only in the begining, like ls: 
```
ls -l -G -F ./
```
but this isn't allowed:
```
ls -l -G ./ -F
```

It would be very easy to add support for this mini-feature, so why is it absent from so many - very used - programs?

---

### Post by nick_h on 2008-04-03
I don't think the feature would be very useful.  Sometimes you might not want input starting with "-" to be interpreted as an option, although you could use a "--" in those cases.

---

